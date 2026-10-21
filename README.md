# Repolex Knowledge Graph of pydata/pyrallel

RDF knowledge graph data for [pydata/pyrallel](https://github.com/pydata/pyrallel), parsed by [repolex](https://repolex.ai).

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
rlex download pydata/pyrallel
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 761cbf7783dd8ada377ff164f78b254689067088
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 761cbf7783dd8ada377ff164f78b254689067088
│           └── chunk-001.nq.gz
├── blob
│   ├── 0992003b9236f9c9679080db1adad26b63ed8011.nq.gz
│   ├── 0cb15d89cc0f1e5e8c6533977297bfee7307d629.nq.gz
│   ├── 241ce817bd0f16ee5c72b4e9d43f80f3d627d1db.nq.gz
│   ├── 3b6270cac70cf4e5322f4830ffe9c899cd7bea78.nq.gz
│   ├── 58d7db3e1dfbdac10394b19899048238069b5b8d.nq.gz
│   ├── 5cc3e09459193f11952f2738f9c0564b0674960a.nq.gz
│   ├── 8d838d92becdb6ef01a7a3d4e6814eaa450e2c64.nq.gz
│   ├── 9f2151c2e57c8b41948bb0ab0a2b3ede85c7f6ae.nq.gz
│   ├── a25cc4e75d375270ede8668078218ab52c2ccaf0.nq.gz
│   ├── af4897f42a8a81a6c031d5721aeefffde4759c79.nq.gz
│   ├── c1b68e4bcf68a4a93be0aa8fde468faea61d7b77.nq.gz
│   ├── e8a57cab44cf3f6d5078e1ebb1028c700311bd53.nq.gz
│   └── e98c96ebf1ee1c766171b0c09d870a5c5e03b3f9.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 761cbf7783dd8ada377ff164f78b254689067088.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 21 files
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

[pydata/pyrallel](https://github.com/pydata/pyrallel)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
