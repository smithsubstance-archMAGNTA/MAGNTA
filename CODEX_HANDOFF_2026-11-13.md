# MAGNTA — Codex handoff
**Cutoff:** 2026-11-13  
**Branch:** `codex/handoff-2026-11-13`  
**Status:** handoff specification only; no Codex execution, tests, deployment, or merge has occurred.

## Purpose
Provide bounded, evidence-first work packages for Codex. Notion remains the institutional source of truth; Jira tracks execution; GitHub stores versioned implementation; Codex implements and tests. Epistemological decisions and acceptance of MRO/EOO definitions remain subject to human review.

## Repositories identified
- `smithsubstance-archMAGNTA/MAGNTA`: Site Central repository. README describes the institutional document structure and index. `Archivo MAGNTA.docx` was located in the root (28,135 bytes) but its binary contents were not read by the GitHub connector.
- `smithsubstance-archMAGNTA/magnta-arquitectura`: Python/FastAPI project with EOO/MRO modules, Docker files, PostgreSQL configuration and two basic unit tests. Presence in GitHub is not proof of deployment.

## Initial static observations
- API routes visible in `app/api/routers.py`: `/health`, `/metrics`, `/ingest-signal`, `/diagnostic`, WebSocket `/ws`.
- EOO indicators in `app/capa_eoo/indicadores.py`: variability, mean deviation, saturation, apparent latency and anomaly rate.
- `motor_diagnostico.py` aggregates normalized values and classifies an entropy score.
- `Kalman1D` exists in `app/nucleo_mro/filtro_kalman.py`; static inspection did not establish that the API ingestion path uses it.
- The ingestion route imports a Bayesian failure-probability estimator.
- `app/db.py` defines a simple signals table. Durable persistence has not been integration-tested.
- Docker Compose declares web, PostgreSQL and simulator services. The inspected configuration contains example credentials; do not reuse them in real environments.
- Existing tests: `tests/test_indicadores.py`, `tests/test_kalman.py`. They have not been run in this audit.
- Pipeline Pulse Reconstruction v1 remains classified as draft/not applied. DigitalTwinFruto implementation was not verified in the inspected files.

## Work packages

### CP-01 — Repository and architecture audit
Inspect complete trees, branches, commit history, dependencies, workflows, configuration and docs. Deliver a component inventory and evidence map. Cite file paths and commit refs. Classify each item as source, draft, mockup, prototype, simulator or deployed only when evidence supports it.

### CP-02 — EOO/MRO technical audit
Review input validation, units, null/non-numeric handling, indicator calculations, normalization, diagnostic thresholds, Bayesian estimation, temporal filtering, persistence and WebSocket behavior. Add regression tests. Do not alter epistemological formulas or thresholds without an approved specification.

### CP-03 — Pipeline Pulse Reconstruction v1
Treat as draft/not applied unless contrary evidence is found. Propose data contracts, signal states and metrics for observation, friction, EOO and continuity. Clearly label synthetic data; do not connect to physical equipment or claim real measurements.

### CP-04 — Digital Twin / DigitalTwinFruto
Search all authorized repositories. If no implementation is found, provide an architecture proposal labeled design-only. Distinguish physical system, simulation, digital model and data-connected digital twin.

### CP-05 — 2025–2026 document recovery
Inventory files without moving, renaming or overwriting originals. Record source, path, hash, date, version and maturity where available. The DOCX identified above requires a separate authorized binary download/read workflow.

### CP-06 — Financial, fiscal and contractual evidence
Prepare a checklist and evidence matrix only. Do not infer revenue, cash, burn, runway, obligations, contracts, legal status or tax compliance. Keep personal and MAGNTA records separate. Do not commit sensitive documents or personal data to Git.

## Execution protocol
1. Work on a dedicated branch; never push directly to `main`.
2. Before edits, report plan, target files and risks.
3. Inspect scripts and side effects before running them.
4. No deployments, destructive migrations, infrastructure changes, external communications or connections to real equipment.
5. Do not add secrets, credentials or personal/operational sensitive data.
6. Keep changes small; include tests, docs and rollback notes.
7. Report exact commands, outputs, changed paths, commit/PR and unresolved issues.
8. Do not mark complete until acceptance criteria are met.

## Required acceptance report
For every package: status; evidence reviewed; files changed; tests executed and results; risks; limitations; PR/commit link; items requiring human decision. A static review is not an executed test, and a proposed architecture is not an implementation.
