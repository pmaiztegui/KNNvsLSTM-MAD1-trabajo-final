# Trabajo Final de Métodos para el Análisis de Datos I: KNN vs LSTM para detectar intrusiones en red. #
# _Descripción_ : #

El objetivo del trabajo es comparar un modelo clásico de aprendizaje como lo es K-Nearest Neighbors con uno de aprendizaje profundo, como Long Short Term Memory.

Trabajaremos sobre el dataset provisto por el Canadian Institute of Cybersecurity, CICIDS-2017, que contiene información de tráfico en red normal y distintos tipos de ataques. 

# _Motivación_: #
En un mundo donde cada vez dependemos más de la tecnología, la seguridad en red es fundamental. Es por esto, que nos resulta necesario desarrollar sistemas que sean capaces de detectar amenazas de manera precisa y eficiente. En este contexto, comparar distintos modelos de aprendizaje permite analizar cuál se adecúa mejor para detectar estas intrusiones. 

# _Datos_: #
Como mencionamos, utilizaremos el dataset CICIDS-2017 que contiene tráfico en red, generado en 5 días y contiene tráfico normal y distintos tipos de ciberataques.

Originalmente, éste contenía 2.830.743 de registros de flujos de red. Cada registro se describe mediante 78 características numéricas y una clasificación (Label) que detecta al tráfico como benigno o indica qué ataque es. 

Algunas de las variables numéricas que podemos observar son: Flow Duration, Flow Bytes/s, Flow Packets/s, Destination Port, Flow IAT.

Además, con el fin de simplificar la clasificación, elegimos agrupar la variable Label en siete clases: BENIGN, DoS, DDoS, PortScan, Other, Web Attack y Bot.

# _Metodología:_ #

  1. Eliminación de filas duplicadas: Hallamos 308.381 filas duplicadas en el dataset y las eliminamos.
  2. Eliminación de filas con datos infinitos: Encontramos que la variable Flow Bytes/s tenía 1211 valores infinitos y la variable Flow Packets/s, 1564. Ubicamos esas filas y las eliminamos.
  3. Tratamiento de datos faltantes: Localizamos 353 datos faltantes, todos en la variable Flow Bytes/s. Calculamos la media de tal variable y la usamos para reemplazar los datos faltantes. Esta técnica es simple y efectiva para datos numéricos, minimizando el impacto en la distribución.
  4. Agrupamos la etiquetas como indicamos anteriormente.
  5. Separamos la muestra en una muestra de entrenamiento y otra de testeo.
  6. Estandarizamos las variables numéricas.
  7. SMOTE: Las clases se veían altamente desbalanceadas, por lo que aplicamos el método de SMOTE. Esta técnica produce datos sintéticos que balancean las clases.
  8. Entrenamos y comparamos dos modelos:

     - KNN: Utilizamos una muestra de 100.000 registros balanceada y estratificada para entrenar el modelo. Elegimos el mejor k mediante validación cruzada.
     - LSTM: Entrenamos una red neuronal recurrente con la misma muestra.
9. Comparamos métricas de los modelos mediante: Accuracy, Precisón, Recall, F1 macro y ponderado.


# _Principales Resultados:_ #
Comparamos los resultados obtenidos por los que se reportan en _Deep Learning vs. Machine Learning for Intrusion Detection in Computer Networks: A Comparative Study_ (Ali et al., 2025).

Observamos diferencias, que se pueden deber a las decisiones que fuimos tomando a lo largo del trabajo. 

# _Cómo ejecutar:_ #
El repositorio se encuentra organizado de la siguiente forma:

KNNvsLSTM-MAD1-trabajo-final/

├── data/

│   └── README.md

├── notebooks/

│   └── KNNvsLSTM.ipynb

├── Reports/

│   ├── KNN_vs_LSTM_beamer.pdf

│   └── KNN_vs_LSTM_beamer.txt

└──  README.md
