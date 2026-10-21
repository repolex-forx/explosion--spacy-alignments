# Repolex Knowledge Graph of explosion/spacy-alignments

RDF knowledge graph data for [explosion/spacy-alignments](https://github.com/explosion/spacy-alignments), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download explosion/spacy-alignments
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 67a902acfed49eb806e6003783b793c70326778f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 67a902acfed49eb806e6003783b793c70326778f
│           └── chunk-001.nq.gz
├── blob
│   ├── 1a78f89d0ead191717fcbc7e9d0ca7057e509e6c.nq.gz
│   ├── 1b0ab6570b942007ab1359daa08c0b5bcf660753.nq.gz
│   ├── 20746d55599c478f97292a80990f0749f88a3d00.nq.gz
│   ├── 2ad1e1e3295c57ed3487f1079a0061d7bf78a654.nq.gz
│   ├── 43eb14a7ec07435b41d75d250454f4f70e1a1700.nq.gz
│   ├── 6b88e45aa58446635fa8dc62355c90a424072024.nq.gz
│   ├── 6b93003c833cfe0aa94b82abfe13da56409e8abb.nq.gz
│   ├── 743f666cd5e2e7d916be5ae09d1d8efdc0c6b392.nq.gz
│   ├── 9df06d15b14c83806e7f7bdb52b928eefce4c315.nq.gz
│   ├── ad217041acd81f24de1ec0a0d5b3dc573b9398ba.nq.gz
│   ├── b82c591c674e8428b9331067b2681df5995d2cab.nq.gz
│   ├── bb5dcb807bb2a2c34f4e36dcb16a24a93c2b64c1.nq.gz
│   ├── bfcf496c8d0ef1a7c916abc0ea8332779d4ddfb3.nq.gz
│   ├── cdb580aeb1ac8d96e7afa442ee60a2b137dc3cfa.nq.gz
│   ├── d8763bb247ed317c20cfeec682b50fc300188938.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e6d4e4c226e8e383a2183337a9fa93687a605988.nq.gz
│   ├── efc92074220fa58be312f2049411741e887c3c48.nq.gz
│   └── fe67d39149e0c1ef1c2dc96366c078d6f279ceda.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 67a902acfed49eb806e6003783b793c70326778f.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 26 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[explosion/spacy-alignments](https://github.com/explosion/spacy-alignments)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
