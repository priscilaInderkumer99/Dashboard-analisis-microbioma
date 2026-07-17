# 🦠 Dashboard de Análisis de Microbiomas

Dashboard interactivo para análisis de comunidades microbianas de sedimento y plancton usando datos de metabarcoding 16S (procariotas) y 18S (eucariotas).

Desarrollado como herramienta de análisis para tesis de grado — UNER, 2026.

---

## Requisitos

- Python 3.8 o superior
- pip

---

## 🚀 Instalación

1. Clonar el repositorio.

```bash
git clone https://github.com/priscilaInderkumer99/Dashboard-analisis-microbioma.git
```

2. Ingresar al directorio del proyecto.

```bash
cd Dashboard-analisis-microbioma
```

3. Crear un entorno virtual.

```bash
python3 -m venv venv
```

4. Activar el entorno virtual.

```bash
source venv/bin/activate
```

5. Instalar las dependencias.

```bash
pip install -r requirements.txt
```

6. Ejecutar la aplicación.

```bash
streamlit run app.py
```

Una vez ejecutado el último comando, Streamlit iniciará la aplicación y mostrará en la terminal una dirección similar a:

```text
Local URL: http://localhost:8501
```

La aplicación se abrirá automáticamente en el navegador. Si esto no sucede, copiá y pegá en el navegador la dirección que aparece en la terminal (por ejemplo, `http://localhost:8501`).
---

## Estructura del proyecto

```
dashboard-microbiomas/
├── app.py                  # Entrada principal
├── requirements.txt        # Dependencias
├── MANUAL_USUARIO.md       # Guía de uso para usuarios
├── utils/
│   ├── data_loader.py      # Carga y procesamiento de archivos
│   └── diversity.py        # Cálculo de métricas de diversidad
└── tabs/
    ├── tab1_composicion.py
    ├── tab2_dominancia.py
    ├── tab3_comparativos.py
    ├── tab4_espacial.py
    ├── tab5_multivariados.py
    ├── tab6_rareza.py
    ├── tab7_ratios.py
    ├── tab8_comparacion.py
    └── tab9_glmm.py
```

---

## Formato de archivos de entrada

### Feature table (.tsv)
```
#OTU ID    1SED    1PLA    2SED    2PLA    ...
abc123     100     0       250     80      ...
def456     0       320     10      410     ...
```
- Primera columna: ID de OTU/feature
- Resto de columnas: muestras con conteos de lecturas
- Muestras 16S: sin prefijo (ej: `1SED`, `1PLA`)
- Muestras 18S: con prefijo `E_` (ej: `E_1SED`, `E_1PLA`)

### Taxonomy (.tsv)
```
#OTUID    taxonomy                                        Confidence
abc123    d__Bacteria; p__Proteobacteria; c__...          0.99
def456    d__Eukaryota; p__Chlorophyta; c__...            0.98
```
- Taxonomía en formato QIIME2 con separador `; ` y prefijos `d__`, `p__`, `g__`, etc.

### Metadata (.tsv)
```
SampleID    Site    Class     pH     Temp_C    ...
1SED        1       Sediment  8,18   20,8      ...
1PLA        1       Plankton  8,18   20,8      ...
```
- Columna de ID de muestra: `SampleID` para 16S, `sample-id` para 18S
- Coordenadas en formato grados/minutos/segundos: `34°45'05.2"S`
- Valores numéricos con coma decimal (`,`) son aceptados automáticamente

---

## Funcionalidades

| Tab | Descripción |
|-----|-------------|
| 📊 Composición | Barras apiladas, heatmap y tabla de abundancias relativas por phylum |
| 👑 Dominancia | Índices de Simpson, Pielou, curvas rango-abundancia, core vs raros |
| ⚖️ Comparativos | Diversidad alfa SED vs PLA con tests Mann-Whitney U |
| 🗺️ Espacial | Gradientes longitudinales, composición por sitio y mapa interactivo |
| 🔢 Multivariados | PCA, NMDS (Bray-Curtis) y clustering jerárquico |
| 💎 Rareza | Taxa únicos por ambiente y proporción de phylums raros |
| 📐 Ratios | Cocientes entre phylums y correlaciones de Spearman |
| 🔬 16S vs 18S | Comparación entre diversidad procariota y eucariota |
| 📈 GLMM | Modelos lineales mixtos con predictores ambientales |

---

## Dependencias principales

```
streamlit==1.31.0
pandas==2.1.4
numpy==1.26.3
plotly==5.18.0
scipy==1.11.4
scikit-learn==1.4.0
statsmodels==0.14.1
matplotlib==3.8.2
seaborn==0.13.1
```

---

## Autora

**Priscila Inderkumer**
2026
