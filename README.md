# Proyecto de Análisis Exploratorio de Datos (EDA) 

# Conjunto de datos bank-additional

## 🧠 Objetivo

Este proyecto tiene como propósito aplicar técnicas de análisis exploratorio de datos (EDA) en un conjunto de datos reales provenientes de campañas de marketing telefónico de una institución bancaria. El objetivo final es obtener insights que puedan ayudar a entender qué factores influyen en que un cliente contrate un depósito a plazo (`y = yes`).

---

## 🛠️ Herramientas utilizadas

- Python
- Pandas
- Matplotlib
- Seaborn
- Visual Studio Code

---

## 📦 Descripción de los datos

El dataset principal contiene información sobre clientes bancarios, sus características demográficas, historial de contacto y resultados anteriores de campañas.

Se trabajó con el archivo: `bank-additional.csv`  
Variables clave incluyen:

- `age`, `job`, `marital`, `education`
- `housing`, `loan`, `contact`, `duration`, `campaign`, `pdays`
- `emp.var.rate`, `euribor3m`, `cons.price.idx`, `nr.employed`
- `y`: variable objetivo (¿contrató el producto?)

---

## 🧹 Transformación y limpieza

- Conversión de columnas numéricas con coma decimal a formato `float`.
- Imputación de valores faltantes:
  - Numéricos: media o mediana.
  - Categóricos: moda o "unknown".
- Eliminación de columnas irrelevantes (`id_`, `date`).
- Verificación de tipos de datos y outliers.

---

## 📊 Análisis Exploratorio

### Análisis univariado
- Se analizaron las distribuciones de variables categóricas y numéricas.
- La mayoría de los clientes no contrataron el producto (`y = no`).

### Análisis bivariado
- La profesión (`job`) y duración de llamada (`duration`) muestran relación fuerte con `y`.
- La edad también influye: clientes de edad media a avanzada presentan mayor tasa de conversión.
- Las tasas económicas (`euribor3m`, `emp.var.rate`) también están relacionadas con el resultado.

### Outliers y correlaciones
- Variables como `duration`, `campaign` y `pdays` contienen valores atípicos importantes.
- `duration` tiene alta correlación con `y`, aunque influida por sesgo de llamada.

---


## 🧩 Conclusiones

- La duración de la llamada es un predictor clave, pero puede estar sesgada.
- Variables demográficas como edad y profesión ayudan a segmentar clientes.
- Variables económicas reflejan el contexto macro, útil para ajustar estrategias.

---

## 📌 Recomendaciones

- En campañas futuras, priorizar perfiles que históricamente muestran mayor tasa de conversión.
- Evitar contactos excesivos en una misma campaña (`campaign > 3` tiende a no funcionar).





# Conjunto de datos customer-details

## 🧠 Objetivo

Este análisis exploratorio se centra en los datos demográficos y de comportamiento de los clientes del banco. El objetivo es identificar patrones relacionados con el ingreso anual, la estructura del hogar (niños y adolescentes) y la actividad en el sitio web del banco, especialmente en función del tiempo que llevan como clientes.

---

## 🛠️ Herramientas utilizadas

- Python 
- Pandas
- Matplotlib
- Seaborn
- Visual Studio Code

---

## 📦 Descripción del dataset

Archivo utilizado: `customer-details.xlsx`  
Estructura: 3 hojas, una por año de registro de clientes, combinadas en un solo DataFrame.

### Columnas clave:
- `Income`: ingreso anual del cliente
- `Kidhome`: número de niños en el hogar
- `Teenhome`: número de adolescentes
- `Dt_Customer`: fecha de alta como cliente
- `NumWebVisitsMonth`: visitas mensuales al sitio web
- `ID`: identificador único del cliente

---

## 🧹 Limpieza de datos

- Eliminación de columnas irrelevantes (`Unnamed: 0`).
- Conversión de `Dt_Customer` a formato `datetime`.
- Creación de columnas derivadas: `Customer_Year`, `Customer_Month`.
- Verificación de valores nulos: **0 valores nulos** detectados.

---

## 📊 Análisis univariado

- **Income**: distribución sesgada a la derecha con outliers altos.
- **Kidhome / Teenhome**: la mayoría de los hogares tienen 0 o 1 niño/adolescente.
- **NumWebVisitsMonth**: la mayoría de clientes visita entre 0 y 10 veces al mes.
- **Customer_Year**: registros concentrados en pocos años, con picos en altas.

---

## 🔗 Análisis bivariado

- **Income vs visitas web**: no se ha detectado una relación significativa.
- **Hijos vs visitas web**: tener hijos no parece influir en el uso del sitio web.
- **Año de alta vs visitas web**: clientes más antiguos tienden a visitar más la web → posible efecto de fidelización.

---

## 📉 Outliers y correlación

- Outliers detectados en `Income` y `NumWebVisitsMonth`, pero controlables.
- Correlaciones entre variables numéricas son muy bajas (< 0.1), sin relaciones lineales destacadas.

---

## 🧩 Conclusiones

- No hay una variable numérica que prediga fuertemente la actividad web.
- El año de alta puede ser un buen punto de segmentación.
- El comportamiento online no está determinado por ingresos ni estructura familiar.

---

## 📌 Recomendaciones

- Analizar variables adicionales (productos contratados, historial) en futuros estudios.
- Combinar este dataset con el de campañas (`bank-additional.csv`) para insights más profundos.
- Considerar segmentaciones por antigüedad para marketing personalizado.
