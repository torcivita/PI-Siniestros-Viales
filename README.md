# <div align="center"><u>**PROYECTO INDIVIDUAL N° 2:**</u> </div>
# <div align="center"><u>**Data Analytics** </u> </div>

<p align=center><img src='Imágenes\Captura de pantalla 2024-01-17 062012.png'><p>

## **Descripción**
Este proyecto es una simulación de trabajo real de un Data Analyst del El Observatorio de Movilidad y Seguridad Vial (OMSV), centro de estudios que se encuentra bajo la órbita de la Secretaría de Transporte del Gobierno de la Ciudad Autónoma de Buenos Aires. 

En este contexto, se nos solicita elaborar un proyecto de anális de datos, con el fin de generar información que le permita a las autoridades locales tomar medidas para disminuir la cantidad de víctimas fatales de los siniestros viales. Para esto, contamos con un dataset sobre homicidios en siniestros viales acaecidos en la Ciudad de Buenos Aires durante el periodo 2016-2021. Este dataset se encuentra, junto con otros datasets sobre lesiones en siniestros viales y datos de población de la ciudad, en la carpeta [Datasets](Datasets). Estos archivos fueron extraidos de la página del Gobierno de la Ciudad de Buenos Aires.

El archivo Poblacion por comuna (tambien disponible en la carpeta [Datasets](Datasets)) corresponde a proyecciones de poblacion realizadas con el censo de 2010 por la Dirección General de Estadística y Censos (Ministerio de Hacienda GCBA).

## **Proceso**
### ETL y EDA
El proceso de Extracción, Transformación y Carga de los datos se realizó en simultaneo con el Análisis Exploratorio de los mismos en el archivo 'ETL+EDA.ipynb'.

Extrajimos los datos de la [página oficial de datos de la Ciudad de Buenos Aires](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales). Los mismos no necesitaron mucha transformación pero de todas maneras realizamos normalizaciones entre mayúsculas y minúsculas, nombres de variables y valores equivalentes con distinto nomenclatura. A la vez, exploramos los valores que podian asumir las variables, eliminamos datos innecesarios, valores nulos y outliers (como por ejemplo los accidentes con coordenadas fuera de los límites de la Ciudad de Buenso Aires). Una vez hechas todas estas transformaciones, mergeamos los dataframes correspondientes a hechos y victimas, creando así dos dataframes: uno con todos los datos de homicidios, y otro con todos los datos de lesiones. También creamos un tercer dataframe con el total de datos de siniestros.

Posteriormente, realizamos análisis gráficos con visualizaciones sobre algunos aspectos importantes en los datos procesados, llegando así a algunas conclusiones interesantes, las cuales se encuentran detalladas en el mismo archivo.

Por último, exportamos los dataframes como archivos de excel para realizar el Dashboard y posterior análsis. Dichos archivos se encuentran disponibles en la carpeta de 'Datos de Trabajo'.

El archivo de poblaciones tenía datos simples en tres cuadros separados. Como eran pocos datos y la distribución era simple, la transformación se realizó directamente en ese archivo de excel. Consistió en una transposición de las columnas correspondientes a los distintos años a filas y la fusion de los tres cuadros. También se omitieron columnas correspondientes a años fuera del análisis de siniestros (previo a 2016 y posterior a 2021).

### KPIs

En el archivo [KPI.ipynb](KPI.ipynb) se encuentra el paso a paso de la creación de DataFrames donde se calculan, con los datos de siniestros proporcionados y procesados, ciertos Indicadores Clave de Desempeño.
A saber, dichos indicadores son:

- `KPI 1: Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior.`
Definimos a la tasa de homicidios en siniestros viales como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico. Su fórmula es: (Número de homicidios en siniestros viales / Población total) * 100,000.

- `KPI 2: Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior.` Definimos a la cantidad de accidentes mortales de motociclistas en siniestros viales como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales con víctimas en moto es: (Número de accidentes mortales con víctimas en moto en el año actual - Número de accidentes mortales con víctimas en moto en el año anterior) / (Número de accidentes mortales con víctimas en moto en el año anterior).

- `KPI 3: Reducir en un 5% la cantidad de siniestros fatales ocacionados en avenidas en el último año, en CABA, respecto del año anterior.`
Definimos a la cantidad de accidentes mortales de siniestros viales en avenidas como el número absoluto de accidentes fatales que ocurrieron en una avenida en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales en avenidas es: (Número de accidentes mortales en avenidas en el año actual - Número de accidentes mortales en avenidas en el año anterior) / (Número de accidentes mortales en avenidas en el año anterior).

- `KPI 4: Reducir en un 5% la cantidad de siniestros fatales ocacionados en calles en el último año, en CABA, respecto del año anterior.`
Definimos a la cantidad de accidentes mortales de siniestros viales en calles como el número absoluto de accidentes fatales que ocurrieron en una calle en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales en calles es: (Número de accidentes mortales en calles en el año actual - Número de accidentes mortales en calles en el año anterior) / (Número de accidentes mortales en calles en el año anterior).

Cada uno de esos dataframes, fue exportado en formato *.xlsx* para su utilización en el tablero. Los mismos se encuentran en la carpeta de 'Datos de trabajo'.

### Herramientas y Librerías

Para el proceso de ETL, EDA y el armado de archivos para el cálculo de KPIs, se utilizaron Notebooks de Jupyter, ya que permiten ir documentando el paso a paso del proceso. En cuanto a las librerías utilizadas, las mismas se detallan en el archivo [requirements.txt](requirements.txt).

Para el armado del Dashboard se utilizó PowerBI, ya que permite unir diferentes fuentes de datos, analizarlos y presentar un análisis de estos a través de informes y paneles.

### Dashboard

El mismo consiste de una portada y seis páginas:

- En la primera página se da contexto sobre datos poblacionales de la Ciudad Autónoma de Buenos Aires.

- En las tres páginas siguientes se detallan varios aspectos importantes sobre los siniestros viales, como ser la distribución de lugares, horas y días de ocurrencia. Además, se plantean dos KPIs sobre reducción de cantidad de víctimas fatales en tipos de calle.

- En las últimas dos páginas se detallan datos importantes sobre las víctimas, como ser edad, género y vehículos que utilizan. Además se plantean otros dos KPIs sobre reducción de cantidad total de víctimas fatales y reducción de cantidad de víctimas fatales por un tipo de vehículo en específico.

## Conclusiones

Los siniestros viales son un tema muy importante ya que son la principal causa de muertes violentas en Argentina. La única forma de evitarlos, es tomando medidas de precaución y concientización. 
Los accidentes pasan, pero hay que intentar minimizar las probabilidades de que ocurran. Para eso es muy importante contar con una buena infraestructura que brinde seguridad y, además, contar con instituciones que se encarguen de recopilar, procesar y difundir de la información sobre cómo evitar los siniestros.

