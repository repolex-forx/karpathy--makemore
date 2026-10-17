# Repolex Knowledge Graph of karpathy/makemore

RDF knowledge graph data for [karpathy/makemore](https://github.com/karpathy/makemore), parsed by [repolex](https://repolex.ai).

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
rlex download karpathy/makemore
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 988aa59e4d8fefa526d06f3b453ad116258398d4
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 988aa59e4d8fefa526d06f3b453ad116258398d4
│           └── chunk-001.nq.gz
├── blob
│   ├── 329db5e33310fd5d98343e2bca690bfb07317526.nq.gz
│   ├── 603b94140e5e11a60e6962992da00e31a742b241.nq.gz
│   ├── 736d88e18b70b292750a30e5cca6a92b0b333bd2.nq.gz
│   └── db0fe4c1e071b05573f9bd73040e9a29410cb3db.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 988aa59e4d8fefa526d06f3b453ad116258398d4.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 12 files
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

[karpathy/makemore](https://github.com/karpathy/makemore)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
