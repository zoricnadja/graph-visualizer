# Graph Visualizer

A Django-based platform for interactive graph visualization, supporting multiple graph sources and visualization plugins. Designed to showcase the benefits of modular, object-oriented architecture with easy plugin integration.

## Team Members

| Name              | Plugin             | GitHub                                           |
|-------------------|--------------------|--------------------------------------------------|
| Milica Radić      | Block Visualizer   | [milicaradicc](https://github.com/milicaradicc)  |
| Nadja Zorić       | Simple Visualizer  | [zoricnadja](https://github.com/zoricnadja)      |
| Mijat Krivokapić  | RDF Datasource     | [mijatkrivokapic](https://github.com/mijatkrivokapic) |
| Andjela Ristić    | JSON Datasource    | [RisticAndjela](https://github.com/RisticAndjela)|
| Damjan Vincić     | PyPI Datasource    | [DamjanVincic](https://github.com/DamjanVincic)  |

## Development Setup

### 1. Local (without Docker)

**Create a virtual environment:**
```sh
python3 -m venv .venv
source .venv/bin/activate    # Linux
# or
source .venv\Scripts\activate # Windows
```

**Install dependencies:**
```sh
pip install -r requirements.txt
```

**Run migrations and start the development server:**
```sh
cd graph_visualizer
python manage.py migrate
python manage.py runserver
```

### 2. Docker

**Build and launch the application:**
```sh
docker-compose up -d
```

**Stop the running containers:**
```sh
docker-compose down
```

The app will be available at [http://localhost:8000](http://localhost:8000).

**Tips:**
- Code changes in `graph_visualizer`, `core`, and `api` are instantly reflected (with Docker volume mapping).
- If you encounter permission issues with `entrypoint.sh`, run:
  ```sh
  chmod +x entrypoint.sh
  ```

## Project Structure

```
graph-visualizer/
│
├── api/                # API library: models, interfaces for data and plugins
├── core/               # Platform/business logic
├── datasource_rdf/     # RDF graph source plugin
├── datasource_json/    # JSON graph source plugin
├── datasource_pypi/    # PyPI graph source plugin
├── simple_visualizer/  # Simple visualizer plugin
├── block_visualizer/   # Block visualizer plugin
├── graph_visualizer/   # Django app (entry point/UI)
├── requirements.txt
├── graph_visualizer/requirements.txt
├── Dockerfile
├── docker-compose.yml
├── entrypoint.sh
└── README.md
```

## Key Features

- **Flexible graph models:** Supports directed, undirected, cyclic, and acyclic graphs with strongly typed node/edge properties.
- **Plugin-based architecture:** Easily add new data sources and visualizations.
- **Three graph views:** Main view (pan/zoom/DD), Tree View (YAML/explorer/tree), and Bird View (overview with viewport).
- **Graph search/filter:** Backend subgraph extraction (not just coloring!) via text or filter queries.
- **CLI terminal:** Command line interface for graphs (create/edit/delete nodes/edges, search, filter, etc.).

## Git & Collaboration Conventions

- Development uses the [GitFlow workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
- One feature branch per issue (`feature-<name>`/`bugfix-<name>` naming).
- Commits reference the relevant issue via `#issue-identificator` in the commit message.
- Periodic merges from feature branches to `develop`.
- Milestones reflect checkpoints of project progress.
- Only team members should appear in the commit history.

## Troubleshooting & FAQs

- If migrations or code changes are not reflected, ensure all local plugins are reinstalled and the container/virtualenv is clean.
- Do not add `venv` or large libraries to git; track Python packages via `requirements.txt`.
- For questions on running and setting up the environment, follow terminal instructions as outlined above.

## Further Specification & Details

Full project and technical specification can be found in [`project-specification.md`](project-specification.md).
