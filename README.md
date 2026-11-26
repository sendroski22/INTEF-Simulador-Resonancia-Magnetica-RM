# Simulador de Resonancia Magnética (RM) – versión recuperada para navegadores actuales

[![Licencia: CC BY-NC-SA](https://img.shields.io/badge/Licencia-CC%20BY--NC--SA%20Espa%C3%B1a-lightgrey.svg)](#autoría-y-licencia)

Simulador de un servicio de resonancia magnética creado en Flash dentro del programa **Internet en el Aula** (Red.es, Ministerio de Industria, Turismo y Comercio y Ministerio de Educación a través del ITE, hoy INTEF). Esta versión recupera el original para que funcione en cualquier navegador actual sin instalar Flash.

**CFGS Imagen para el Diagnóstico y Medicina Nuclear** · Módulo 1352 - Técnicas de imagen por resonancia magnética

🔗 **Acceso al simulador:** https://sendroski22.github.io/INTEF-Simulador-Resonancia-Magnetica-RM/

📘 **Manual de ayuda al profesor (PDF):** [docs/manual-ayuda-profesor-RM.pdf](docs/manual-ayuda-profesor-RM.pdf)

## ¿Para qué sirve?

El alumnado trabaja como técnico o técnica en su primer día en un servicio de RM. Tiene que organizar su jornada como en un servicio real: elegir un volante médico, preparar la sala y el equipo, tratar con el paciente y con el resto del equipo y realizar la prueba siguiendo el protocolo. El simulador puntúa por separado el **trabajo** y las **relaciones**, de modo que también cuentan la actitud profesional y el trato con el paciente.

## Relación curricular

| | |
|---|---|
| **Ciclo** | CFGS Imagen para el Diagnóstico y Medicina Nuclear (Real Decreto 770/2014) |
| **Módulo** | 1352 - Técnicas de imagen por resonancia magnética |
| **Resultados de aprendizaje** | RA1. Prepara la exploración, aplicando los procedimientos de control establecidos.<br>RA2. Aplica técnicas de administración de los medios de contraste, según protocolo específico de la unidad, identificando los tipos y sus indicaciones de uso.<br>RA3. Realiza la prueba de resonancia magnética, interpretando los protocolos de exploración establecidos. |

## Contenido

1. **Portada**: ver una demo, cargar una sesión guardada, elegir personaje (técnica o técnico) y entrar en el simulador.
2. **Escenarios en 3D** que se recorren girando la vista: sala de descanso, sala de RM y cabina de control.
3. **Casos clínicos**: cada volante indica el protocolo, la prioridad, la región, si lleva contraste y los datos del paciente. Se puede elegir al azar, para practicar o libremente.
4. **Personajes** (enfermería, celador, jefe de técnicos y pacientes) con los que se dialoga y se toman decisiones.
5. **Minijuegos**: revisar el volante, el material, las bombas de contraste y la máquina de RM, y colocar al paciente.
6. **Material de apoyo**: teoría guiada, glosario, mapa conceptual, tutorial, ayuda y área docente con informes.
7. **Puntuación** de trabajo y de relaciones, y cronómetro.

## Qué se ha cambiado respecto al original

El contenido, los textos, los casos y la lógica del simulador son los originales. Solo se han hecho los cambios técnicos necesarios para que funcione hoy:

- **Emulador de Flash**: la página `sim.html` carga el simulador con [Ruffle](https://ruffle.rs/), un emulador libre de Flash escrito en WebAssembly. Ya no hace falta tener Flash instalado.
- **Pantalla completa**: botón en la esquina inferior derecha. El simulador se amplía sin deformarse.
- **Texturas verdes**: los objetos con los que se puede interactuar llevaban encima un rectángulo verde que Flash ocultaba y el emulador no. Se han hecho transparentes y siguen funcionando igual.
- **Bata**: en el original la bata del perchero no respondía. Estaba enlazada a un elemento vacío en lugar de a su programación, que sí venía incluida. Se ha conectado y se ha corregido el orden de las capas para que el emulador detecte el clic. Ahora se puede coger y desaparece del perchero.
- **`index.html`**: redirige a `sim.html` para que el enlace de GitHub Pages abra directamente el simulador.

## Material para el profesorado

El [**Manual de ayuda al profesor**](docs/manual-ayuda-profesor-RM.pdf) (117 páginas, PDF) forma parte del material original. Explica paso a paso, con capturas, cómo resolver la revisión de los equipos y cada uno de los casos clínicos del simulador: datos del volante, colocación del paciente, introducción de datos del protocolo y control de calidad de las imágenes.

Contiene las soluciones de los casos, así que está pensado para el docente.

## Uso

- **En línea:** abre el enlace de acceso. Funciona en Chrome, Edge, Firefox y Safari actuales.
- **En Moodle:** sube el paquete `.zip` completo como actividad **SCORM**. El seguimiento SCORM 2004 del original se conserva.
- **En tu ordenador:** el simulador **no funciona con doble clic** sobre `index.html`, porque el navegador bloquea el emulador al abrir archivos locales. Hay que servir la carpeta con un pequeño servidor, por ejemplo con Python: abre una terminal en la carpeta, escribe `python -m http.server` y entra en `http://localhost:8000`.

### Publicar en GitHub Pages

1. Sube **todo el contenido de la carpeta** a la raíz del repositorio, no solo `index.html`. El simulador necesita los archivos `.swf`, las carpetas `assets`, `xml`, `ruffle`, etc.
2. Ve a **Settings → Pages**.
3. En *Source*, elige **Deploy from a branch**, rama `main` y carpeta `/ (root)`.
4. En unos minutos estará en `https://<usuario>.github.io/<repositorio>/`.

El archivo `.nojekyll` debe estar en la raíz: evita que GitHub Pages procese y oculte archivos.

## Estructura del repositorio

```
├── index.html          → entrada; redirige a sim.html
├── sim.html            → página que carga el simulador con Ruffle (pantalla completa, SCORM)
├── Simulador.swf       → simulador original (Flash)
├── *.swf               → módulos: portada, minijuegos, teoría, glosario, ayuda…
├── assets/             → escenarios, animaciones, imágenes y vídeos
├── xml/                → textos, casos clínicos y configuración
├── docs/               → manual de ayuda al profesor (PDF)
├── ruffle/             → emulador Ruffle y sus licencias (LICENSE_MIT, LICENSE_APACHE)
├── imsmanifest.xml     → manifiesto SCORM 2004 para Moodle
├── .nojekyll           → indica a GitHub Pages que publique los archivos tal cual
├── README.md           → este archivo
└── LICENSE             → licencia y créditos
```

No necesita instalación ni dependencias. Solo hay que servirlo desde un servidor web: GitHub Pages, Moodle o un servidor local.

## Limitaciones

- El simulador funciona dentro de un emulador. Puede haber diferencias menores respecto a Flash. Por ejemplo, no aparece el brillo que rodeaba a los objetos al pasar el ratón, pero el cursor y los textos de ayuda funcionan.
- Está pensado para ordenador, con ratón. En móviles y tabletas puede ir lento o resultar difícil de manejar.
- Los contenidos clínicos son los del original y reflejan los protocolos de cuando se creó.

## Agradecimientos

A la web [Recursos Imagen para el Diagnóstico y Medicina Nuclear](https://www.rxcuenca.com/recursos.htm), que sigue manteniendo disponibles estos simuladores y sus manuales, y de donde se han descargado los originales para esta recuperación.

## Autoría y licencia

**Obra original:**

> El presente material educativo digital es propiedad de la entidad pública empresarial Red.es y ha sido realizado en el marco del programa Internet en el Aula. Este programa ha sido desarrollado y ejecutado por el Ministerio de Industria, Turismo y Comercio, la entidad pública empresarial Red.es, el Ministerio de Educación -a través del Instituto de Tecnologías Educativas (ITE)- junto a las Consejerías de Educación de las distintas Comunidades Autónomas de España.

La obra original está licenciada como **Creative Commons Reconocimiento-No Comercial-Compartir bajo la misma licencia España**, tal y como indican sus créditos. Este reconocimiento no implica el apoyo por parte de Red.es a esta adaptación.

**Adaptación técnica:** "Simulador de Resonancia Magnética – versión recuperada para navegadores actuales" por **Pablo A. Sendra Lleó** (2026). Se distribuye bajo **la misma licencia que la obra original**, como exige su condición de compartir igual. Puedes compartirla y adaptarla siempre que reconozcas los créditos de Red.es y de esta adaptación, no la uses con fines comerciales y distribuyas las obras derivadas con la misma licencia. Más información en el archivo [`LICENSE`](LICENSE).

**Ruffle:** © Ruffle LLC y colaboradores, con licencia doble [MIT](ruffle/LICENSE_MIT) o [Apache 2.0](ruffle/LICENSE_APACHE), compatible con este uso.

Esta adaptación se desarrolló con la asistencia del modelo de inteligencia artificial [Claude (Anthropic)](https://claude.ai/).
