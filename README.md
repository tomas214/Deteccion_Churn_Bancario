# 🏦 Predicción de Churn Bancario - Optimización de Ganancia

Este proyecto implementa un modelo de **Machine Learning (LightGBM)** para predecir la fuga de clientes (**BAJA+2**) en una entidad bancaria, maximizando la ganancia económica mediante el envío estratégico de estímulos.

## 📈 Lógica de Negocio
Se busca optimizar la rentabilidad de las campañas de retención basada en una matriz de costos:
* **Acierto (BAJA+2 identificado):** Ganancia de **$273,000**.
* **Error (Falso Positivo):** Costo de **$7,000**.
* **Estrategia:** Solo se envía el estímulo a los clientes cuya probabilidad de fuga justifique el riesgo económico según el modelo.

## 📂 Datos
* **Datos Crudos:** `competencia_03_crudo.csv` (Dataset histórico).
* **Dataset Procesado:** `DatosComp3.csv` (Generado tras limpieza y etiquetado).

## ⚙️ Orden de Ejecución (Pipeline)

Seguí este orden para reproducir el experimento:

1. **`clase_ternaria.R`**: 
   - Lee el archivo crudo y crea la variable objetivo `clase_ternaria` (BAJA+1, BAJA+2, CONTINUA).
   - Realiza limpieza de columnas con exceso de ceros.
   - Exporta `DatosComp3.csv`.

2. **`optimizacion_optuna.py`**:
   - Realiza la ingeniería de variables: **Lags, dLags y Percentiles**.
   - Ejecuta la búsqueda bayesiana de hiperparámetros con **Optuna**.
   - Guarda los mejores parámetros y el estado en `entorno_completo.pkl`.

3. **`entrenamiento_prediccion.py`**:
   - Carga el entorno y los mejores parámetros.
   - Entrena el modelo final con **LightGBM** sobre el histórico completo.
   - Genera predicciones para septiembre 2021.
   - Exporta los archivos de sumisión (`predicciones_kaggle_Xk.csv`).

## 🛠️ Requisitos
Instalá las dependencias con:

pip install -r requirements.txt
