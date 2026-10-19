# Edge RAG video

[Watch or download the walkthrough](./Edge-RAG-Partner-Enablement.mp4) |
[English captions](./Edge-RAG-Partner-Enablement.en.srt)

**5:29 | 1080p | female English narration**

The walkthrough covers machine readiness, Azure portal setup, container downloads
and startup, document indexing, and two recorded Streamlit queries.

## Container setup chapters

| Time | Step | What to do |
|---|---|---|
| 2:20 | 7 | Download the container images with Compose |
| 2:42 | 8 | Start the containers and run inference checks |
| 3:01 | 9 | Show all eight running containers in Docker Desktop |
| 3:18 | 10 | Index once and launch Streamlit |

From the application repository root, after preparing the private `.env`:

```powershell
docker compose -f .\compose.local-ai.yaml pull
docker compose -f .\compose.local-ai.yaml config --quiet
docker compose -f .\compose.local-ai.yaml up -d
docker compose -f .\compose.local-ai.yaml ps

.\venv\Scripts\python.exe .\tests\verify_local_services.py
```

`pull` downloads the images defined in
[compose.local-ai.yaml](https://github.com/odulkuyulu/Edge-RAG/blob/5ed938c/compose.local-ai.yaml):
Document Intelligence, its Layout dependency, four Language feature containers,
Qdrant, and Ollama. `up -d` creates and starts the services with the configured
billing values, ports, dependencies, and persistent storage.

In Docker Desktop, select **Containers**, expand **edge-rag-local-ai**, and check
that `language`, `ner`, `keyphrase`, `sentiment`, `document`, `layout`, `qdrant`,
and `ollama` all have running indicators. Confirm actual inference with the
verifier, not status alone.

Use Compose rather than the image's standalone **Run** button for this lab:
Compose supplies `Eula=accept`, `Billing`, `ApiKey`, and the required dependencies.
Do not publish keys or print expanded container environments.

Azure setup and commands are illustrated; the Docker Desktop pictures are
presenter-supplied reference captures. The query clips are actual recordings.
Inference runs locally, with Azure billing connectivity still required.

Full instructions:
[Partner enablement guide](https://github.com/odulkuyulu/Edge-RAG/blob/5ed938c/PARTNER_ENABLEMENT_GUIDE.md).
