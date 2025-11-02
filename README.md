# 🧬 GPT Prompt — Extractor de Biomarcadores Whoop + Advanced Labs (España / LATAM / UE)

## 🇪🇸 Descripción general
Este repositorio comparte un **prompt de ChatGPT** para crear un **GPT personalizado** que:
- 🧪 **Extrae automáticamente biomarcadores** desde informes/analíticas (PDF, imagen OCR o texto).
- 🌍 **Muestra resultados en español e inglés** (nombre + valor + unidad).
- 🔁 **Convierte unidades** a los formatos que reconoce Whoop / Advanced Labs.
- 📊 **Entrega JSON estructurado + cuadros visuales** listos para registrar.
- 🧩 **Indica faltantes** (qué marcadores no aparecen en el informe).

Pensado para la comunidad de **Whoop** en **España, LATAM y UE** que no tiene acceso directo a **Advanced Labs**.

---

## 🚀 Cómo usarlo (GPT personalizado en ChatGPT)
1. Abre el creador de GPTs: https://chat.openai.com/create  
2. En la sección **Conocimiento**, sube el archivo:
   - `Prompt_Extractor_Biomarcadores_CONOCIMIENTO_BILINGUE_VALORES.txt`
3. En **Instrucciones del sistema**, pega este texto:
   > Usa el documento “Prompt_Extractor_Biomarcadores_CONOCIMIENTO_BILINGUE_VALORES.txt” como guía completa para procesar informes de analíticas de sangre y mostrar biomarcadores en cuadros bilingües (español e inglés), con detección de faltantes, valores y conversiones automáticas de unidades.
4. Guarda.  
5. Prueba subiendo un informe/analítica: el GPT devolverá **JSON + cuadros ES/EN** y, si falta algo, un bloque `[no_disponibles / not available]`.

> **Tip:** Si quieres ver solo los cuadros, escribe `/cards_only`.

---

## 🧾 Biomarcadores principales (ES / EN)
Incluye, entre otros:
- Cortisol / Cortisol  
- Testosterona / Testosterone  
- TSH / Thyroid-Stimulating Hormone  
- Vitamina D / Vitamin D  
- **Creatinina / Creatinine**  
- Glucosa / Glucose  
- HbA1c / Hemoglobin A1c  
- ApoB / Apolipoprotein B  
- Ferritina / Ferritin  
- Magnesio / Magnesium  
- Leptina / Leptin  
- AST / Aspartate Aminotransferase

> El GPT **convierte unidades** habituales: p. ej., Creatinine **µmol/L → mg/dL (÷88.4)**, Glucose **mmol/L → mg/dL (×18.02)**, etc.

---

## 🔄 ¿Por qué es útil si no tengo Advanced Labs?
- Convierte resultados de **laboratorios locales** (ES/UE/LATAM) a los formatos requeridos por Whoop.
- Estandariza nombres y unidades **ES/EN** para evitar errores al transcribir.
- **Lista faltantes** para que sepas qué pedir la próxima vez.

---

## 📈 Mejora continua (aprendizaje progresivo)
A medida que **introduces nuevos análisis**, el GPT:
- Aprende patrones de **tus laboratorios locales** (formatos, abreviaturas).
- Mejora la **detección y normalización** de unidades.
- Mantiene la coherencia con los valores requeridos por Whoop/Advanced Labs.

> Si el informe contiene **datos y marcadores correctos**, el GPT devolverá los **valores correctos en las unidades que la app de Whoop necesita**.

---

## 🖼️ Ejemplo de salida
**Cuadros bilingües:**
```
[metabólica / metabolic]
**Creatinina / Creatinine**: `1.20 mg/dL`
**Glucosa / Glucose**: `86 mg/dL`
**HbA1c / Hemoglobin A1c**: `5.0 %`

[no_disponibles / not available]
hormonas / hormones → DHEA-S / DHEA Sulfate, Cortisol / Cortisol
```

**JSON (fragmento):**
```json
{
  "panels": {
    "metabolica": [
      {
        "label_es": "Creatinina",
        "label_en": "Creatinine",
        "value_std": 1.20,
        "unit_std": "mg/dL",
        "notes": "converted from µmol/L"
      }
    ]
  }
}
```

---

## 📂 Estructura del repo (sugerida)
```
.
├─ README.md
├─ prompts/
│  └─ Prompt_Extractor_Biomarcadores_CONOCIMIENTO_BILINGUE_VALORES.txt
└─ examples/
   ├─ ejemplo_salida_json.md
   └─ ejemplo_cuadros.md
```

---

## 🤝 Contribuir
¡Contribuciones bienvenidas!
- Envía **PRs** para añadir nuevos biomarcadores, sinónimos y conversiones.
- Aporta ejemplos de **laboratorios locales** para mejorar la extracción.
- Abre issues con capturas o textos de analíticas (sin datos personales).
