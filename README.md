# Estructura del Pipeline

## Carga del Dataset
* **Carga de opiniones:** Importación desde un archivo local de Excel (`Actividad 5 .xlsx`).
* **Mecanismo de respaldo:** Activación automática con datos sintéticos balanceados en caso de ausencia del archivo físico.

## Limpieza de Datos
* **Depuración:** Eliminación de valores nulos y registros duplicados.
* **Normalización:** Conversión del texto a minúsculas y remoción de espacios innecesarios.

## Preparación de Datos
* **Codificación de etiquetas:** Transformación de texto mediante `LabelEncoder` (\(\text{POS} \rightarrow 1\), \(\text{NEG} \rightarrow 0\)).
* **Vectorización:** Uso de la representación matemática TF-IDF (`TfidfVectorizer`) sobre los textos limpios.
* **División del dataset:** Separación estratificada en conjuntos de entrenamiento (**80%**) y prueba (**20%**).

## Entrenamiento y Optimización de Modelos
* **Clasificadores base:** Configuración y entrenamiento de Regresión Logística y Random Forest.
* **Ajuste de hiperparámetros:** Optimización fina mediante validación cruzada con `GridSearchCV` buscando maximizar la métrica *F1-macro*.

## Evaluación y Visualización
* **Reporte final:** Generación de métricas de clasificación en el conjunto de test independiente.
* **Gráfico comparativo:** Diagrama de barras con las métricas clave de desempeño (Exactitud, Precisión, Sensibilidad y F1-Score).

## Versionamiento con MLflow
* **Almacenamiento:** Configuración y registro de ejecuciones utilizando una base de datos local SQLite.
* **Registro automático:** Guardado de hiperparámetros óptimos y métricas finales del conjunto de prueba.
* **Serialización:** Persistencia segura de modelos silenciando advertencias innecesarias del sistema.

## Monitoreo y Auditoría
* **Consulta programática:** Uso de `MlflowClient` para listar experimentos activos y verificar el estado de los runs (`FINISHED`/`FAILED`), parámetros y métricas registradas.
