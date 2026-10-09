# Análisis de nodos del Sistema Eléctrico Nacional (México)

Notebook de Python que explora el catálogo de nodos del Sistema Eléctrico Nacional (SEN): distribución de nodos por entidad federativa y por nivel de tensión, y su cruce.

## Datos

Los datos **no se incluyen en este repositorio**. Deben descargarse de la fuente original y colocarse en la carpeta `data/`.

- **Fuente:** [CENACE, Nodos P](https://www.cenace.gob.mx/Paginas/SIM/NodosP.aspx)
- **Nombre original:** *Catálogo NodosP Sistema Eléctrico Nacional (v2026-09-23)*
- **Versión utilizada:** v2026-09-23
- **Tamaño:** 2,610 registros y 19 columnas.
- **Ruta esperada por el notebook:** `data/catalogo_nodosp_sen_v2026-09-23.xlsx`

Para usar el notebook, descarga el archivo y renómbralo exactamente como `catalogo_nodosp_sen_v2026-09-23.xlsx` (sin acentos, espacios ni paréntesis, y con una sola extensión `.xlsx`), para evitar problemas de compatibilidad entre sistemas operativos. Su contenido no debe modificarse.

Notas sobre los datos:

- No hay valores nulos (`NaN`), pero 9 nodos tienen el valor `No Aplica` en `ENTIDAD FEDERATIVA (INEGI)`. Por sus nombres, corresponden a puntos de interconexión con redes de países vecinos, y se tratan como una categoría independiente.
- `CLAVE DE MUNICIPIO (INEGI)` se repite entre entidades. La clave única de municipio es la combinación de la clave de entidad y la de municipio.

## Contenido del notebook

`nodos_cfe.ipynb` se organiza en estas secciones:

1. Carga de datos e inspección general (`info`, valores nulos, columnas).
2. Nodos por entidad federativa (tabla y gráfica de barras).
3. Nodos de interconexión clasificados como `No Aplica`.
4. Nodos por nivel de tensión (tabla y gráfica de barras).
5. Tabla cruzada entidad federativa × nivel de tensión, con total por entidad.

Las salidas están guardadas en el notebook, por lo que GitHub muestra tablas y gráficas sin ejecutarlo ni descargar los datos.

## Estructura del repositorio

```
.
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
├── data/
│   └── .gitkeep          # el archivo .xlsx debe colocarse aquí (no se versiona)
└── nodos_cfe.ipynb
```

## Requisitos

- **Python 3.11 o superior** (desarrollado con Python 3.14).
- **[Visual Studio Code](https://code.visualstudio.com/)** con estas extensiones:
  - [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
  - [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
- **Dependencias** de `requirements.txt`: `pandas`, `matplotlib`, `openpyxl` e `ipykernel` (kernel que usa VS Code para ejecutar el notebook).

## Ejecución en VS Code

1. Clona el repositorio:

```bash
   git clone https://github.com/samuel-c124/analisis_nodosp_sen_mx.git
   cd analisis_nodosp_sen_mx
```

2. Descarga el catálogo desde la [fuente](https://www.cenace.gob.mx/Paginas/SIM/NodosP.aspx) y guárdalo en `data/` como `catalogo_nodosp_sen_v2026-09-23.xlsx` (ver sección **Datos**).
3. Abre la carpeta clonada **desde su raíz**: *File → Open Folder*. Esto es necesario para que la ruta relativa `data/...` funcione.
4. Abre una terminal en VS Code (*Terminal → New Terminal*), crea el entorno virtual e instala las dependencias:

```bash
   python -m venv .venv
   # Windows:
   .venv\Scripts\activate
   # Linux / macOS:
   source .venv/bin/activate

   pip install -r requirements.txt
```

5. Abre `nodos_cfe.ipynb`.
6. Selecciona el kernel: botón **Select Kernel** (arriba a la derecha) → *Python Environments* → `.venv`.
7. Ejecuta todas las celdas con **Run All**.

Si VS Code no lista `.venv`, ejecuta *Python: Select Interpreter* desde la paleta de comandos (`Ctrl+Shift+P`) o reinicia VS Code.

El notebook carga los datos con una ruta relativa (`data/...`), por lo que debe ejecutarse con la raíz del repositorio como directorio de trabajo.

## Autor

Samuel Canul, Ingeniería en Energías Renovables, Universidad Autónoma de Yucatán (UADY).

## Licencia

- **Código:** [MIT](LICENSE)
- **Datos:** no se redistribuyen en este repositorio. Pertenecen al CENACE y están sujetos a los términos de la fuente original.