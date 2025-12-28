Textify is a lightweight Python tool for Autodesk Maya that generates 3D text procedurally using a single Texture Atlas (Material).

Textify operates in two distinct phases to optimize performance:

1.  Harvest Phase (Development): The developer manually prepares source geometry (cutting out characters from a font sheet). The harvest_font_data.py script scans this geometry and "harvests" the UV coordinates and vertex offsets into a lightweight JSON file.

2. Runtime Phase (Production): The artist uses the main wordify package. It reads the JSON definitions to procedurally generate text meshes instantly, with correct UVs mapping back to the original atlas.

Project Structure:

wordify_project/
├── tools/
│   └── harvest_font_data.py    # Dev utility: Scans source geometry and writes JSON
│
├── src/
│   └── wordify/                # Main Package
│       ├── components.py       # Core Logic: LetterFactory, TextBlock classes
│       ├── ui.py               # Interface: PySide/Maya CMDs window
│       └── data/               # Database: Font definitions (e.g., font_arial.json)
│
└── install.mel                 # Drag-and-drop installer