# Portfolio Web Personal - Pablo Ezequiel Schlotthauer

Este repositorio contiene el código fuente y el proceso de diseño del Portfolio Web Personal desarrollado para la asignatura **Diseño UX/UI (2026)** de la **Licenciatura en Sistemas de Información (UADER FCyT - Sede Concepción del Uruguay)**.

---

## 🚀 Enlaces del Proyecto

- **Sitio Web Publicado (Deploy):** https://github.com/pablosch91/portfolio-pablo
- **Prototipo Navegable en Figma:** https://www.figma.com/design/ffhtcmwGazt923TqcMoedd/Portfolio-Web---Pablo-Schlotthauer?node-id=0-1&t=n5LzUaSVRUFk4fbt-1

---

## 🛠️ Stack Tecnológico

- **Maquetación:** HTML5 Semántico (`<header>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- **Estilos:** Tailwind CSS (vía CDN para entorno de desarrollo)
- **Tipografías e Íconos:** FontAwesome 6
- **Control de Versiones:** Git & GitHub (CI/CD con despliegue automático)

---

## 🎨 Proceso UX / UI & Benchmark

- **Usuario Objetivo (Proto-persona):** Reclutadores IT, coordinadores académicos y clientes interesados en desarrollo frontend claro y accesible.
- **Concepto Visual (3 Palabras Clave):** *Estructura*, *Accesibilidad*, *Claridad*.
- **Paleta de Colores:** Fondo Oscuro (`#161513`), Acentuación Púrpura/Azul (`#635BFF`), Texto Neutro Blanco/Gris.

### 🧪 Test de Usabilidad & Validación (3 Usuarios)
Se realizó una prueba con 3 usuarios sobre la versión prototipada y la maquetación final:
1. **Usuario 1:** Indicó que la jerarquía de proyectos y la sección de experiencia técnica es muy clara y fácil de leer.
2. **Usuario 2:** Sugirió resaltar los accesos rápidos de contacto y verificar el contraste de los textos pequeños en móviles.
3. **Usuario 3:** Confirmó que el desplazamiento suave por anclas navega correctamente en dispositivos celulares.

---

## 📊 Métricas Lighthouse (Mobile)

- **Performance:** ≥ 70
- **Accesibilidad:** ≥ 90
- **Buenas Prácticas:** ≥ 90
- **SEO:** ≥ 90

## Optimización de rendimiento

Con Lighthouse, la performance pasó de **35 a 75-80** (Accesibilidad: 95, Buenas prácticas: 100, SEO: 100).

### Qué se hizo

1. **Tailwind compilado en vez de CDN.** Se reemplazó el script `cdn.tailwindcss.com` (unos 300 KB de JavaScript que bloqueaba el render) por un `styles.css` generado con la CLI de Tailwind, que incluye solo las clases usadas (14 KB minificado).
2. **Imágenes en WebP y a tamaño real.** Las capturas de proyectos, el logo de UADER y la foto de perfil se convirtieron de PNG/JFIF a WebP y se redimensionaron al tamaño en que se muestran, pasando de varios MB a unos 100 KB en total.
3. **Atributos de imagen.** Se agregaron `width`, `height` y `decoding="async"`, `loading="lazy"` en las imágenes de debajo del primer pantallazo, y `fetchpriority="high"` en la foto de perfil, para evitar saltos de layout y priorizar la carga.
4. **Íconos SVG inline en vez de Font Awesome.** Se eliminó la descarga de la librería completa (CSS + fuentes) y se reemplazó por los mismos íconos como SVG dentro del HTML.
5. **Foto de perfil sin doble anillo.** La imagen ya traía su borde violeta, por lo que se eliminó el contenedor con borde del CSS.
6. **Logo de UADER unificado.** Los dos logos de la sección Experiencia usan ahora el mismo contenedor circular de 32 px.
7. **Menú hamburguesa en mobile.** La navegación estaba oculta en pantallas chicas; se agregó un menú desplegable que se cierra al tocar un link.
8. **Limpieza de HTML.** Se eliminó un `</main>` duplicado y los `preconnect` repetidos.

### Cómo regenerar el CSS

Si se agregan clases nuevas de Tailwind al HTML, hay que volver a compilar:

```bash
npm install -D tailwindcss@3
npx tailwindcss -i ./input.css -o ./styles.css --minify

*(Ver capturas adjuntas en docs/capturas).*