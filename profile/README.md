<div align="center">

<img src="https://qubepods.com/img/qubepods.jpeg" alt="qubepods" width="100%" />

<br />
<br />

`Q U B E P O D S`

# Capability-bounded code, mid-conversation.

**A hosted runner for [`q64`](https://q64.dev) qubes.**
Agents author tools as WebAssembly; the host grants only the
capabilities the manifest declares.

<br />

[![Site](https://img.shields.io/badge/qubepods.com-5fd4ff?style=for-the-badge&labelColor=07090d)](https://qubepods.com)
&nbsp;
[![Docs](https://img.shields.io/badge/docs.q64.dev-07090d?style=for-the-badge&labelColor=07090d)](https://docs.q64.dev)
&nbsp;
[![API](https://img.shields.io/badge/api.qubepods.com-07090d?style=for-the-badge&labelColor=07090d)](https://api.qubepods.com)

</div>

<br />

## What is qubepods?

qubepods is a hosting platform for [q64](https://q64.dev) WebAssembly qubes.
Write a **Qube**, deploy it, and it is served at `<hostname>.qubepod.app` — a
capability-bounded HTTPS endpoint with per-call micro-billing. No servers to
provision, no containers to babysit: the manifest declares what the code may
touch, and the host grants nothing more.

```
qube pod new my-app      # scaffold a qubepod.jsonc manifest
qube publish             # push to the Continuum registry
# → served at https://<hostname>.qubepod.app
```

## How it works

| | |
|---|---|
| **Author** | A deployable Qube ships a `qubepod.jsonc` manifest (kind `QubePod`, `apiVersion qubepods.dev/v0.1`). It compiles to wasm32 — the [WebAssembly Component Model](https://q64.dev) is the substrate. |
| **Bound** | The manifest declares capabilities. The host hands the qube *only* those faces — network, storage, time — and nothing it didn't ask for. |
| **Deploy** | Drive the **MCP control plane** at `mcp.qubepods.com/mcp` with a `qube_…` project token, or `POST` a bundle to `api.qubepods.com`. |
| **Serve** | Each app is reachable at a subdomain of `*.qubepod.app` (or `*.etiamo.app`), TLS terminated at the edge. |

## The ecosystem

| Project | What it is | |
|---|---|---|
| **q64** | The language. Typed, effectful, compiles to wasm components. | [q64.dev](https://q64.dev) |
| **Continuum** | The public package registry for qubes. | [continuum.q64.dev](https://continuum.q64.dev) |
| **cmotion** | A typed DSL for motion graphics & animation. | [cmotion.org](https://cmotion.org) |
| **plinken** | Creative DAW for film & music production. | [plinken.com](https://plinken.com) |

## For agents

qubepods is built to be driven by AI agents. The machine-readable entry points:

- **`/llms.txt`** — [qubepods.com/llms.txt](https://qubepods.com/llms.txt) — the human-and-agent guide
- **`/.well-known/qubepods.json`** — the machine manifest (services, auth, schema)
- **MCP** — `https://mcp.qubepods.com/mcp` (JSON-RPC 2.0; bearer `qube_…` project token)

<div align="center">
<br />

`mid-conversation` · [info@qubepods.com](mailto:info@qubepods.com) · © 2026 qubepods

</div>
