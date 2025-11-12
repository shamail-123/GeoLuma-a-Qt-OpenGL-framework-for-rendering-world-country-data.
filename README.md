# GeoLuma-a-Qt-OpenGL-framework-for-rendering-world-country-data.
A Qt C++ desktop application that loads world-country vector data (GeoJSON or Shapefiles) from a folder, parses it, triangulates polygons, and renders the countries using OpenGL inside a QOpenGLWidget. Architecture: N-tier — separate UI, data parsing, and rendering layers.
## 🚀 Features

- 🗂️ Load folder of world-country datasets (GeoJSON / Shapefile)
- 🧭 Parse and project geographic coordinates (EPSG:4326 → Web Mercator)
- 🎨 Render polygons with OpenGL (triangulated meshes)
- 🧩 View and inspect country metadata in table view
- 🖱️ Select and highlight countries (color picking)
- 🧵 Multithreaded parsing (QtConcurrent)
- ⚙️ N-tier architecture (UI, Controller, Renderer, Data)

---

## 🏗️ Architecture Overview

```text
+-----------------------+
|        UI Layer       |
|-----------------------|
|  MainWindow (Qt UI)   |
|  GLWidget (OpenGL)    |
+-----------+-----------+
            |
            v
+-----------------------+
|   Controller Layer    |
|-----------------------|
| RendererController    |
| Handles app logic,    |
| manages threads        |
+-----------+-----------+
            |
            v
+-----------------------+
|      Data Layer       |
|-----------------------|
| GeoJSONLoader         |
| CountryMesh (buffers) |
| ProjectionUtils       |
+-----------------------+
            |
            v
+-----------------------+
|   Rendering Layer     |
|-----------------------|
| QOpenGLWidget + Shaders |
+-----------------------+
