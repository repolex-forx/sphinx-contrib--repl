# Repolex Knowledge Graph of sphinx-contrib/repl

RDF knowledge graph data for [sphinx-contrib/repl](https://github.com/sphinx-contrib/repl), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/repl
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6a07f80dc53584a6400989f165f3ba767dcd1bf2
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6a07f80dc53584a6400989f165f3ba767dcd1bf2
│           └── chunk-001.nq.gz
├── blob
│   ├── 1a8be837a5e05daa26d532261199c23a1bf65939.nq.gz
│   ├── 299a390ca5bd13c2dbd9e12ae3559e74fc67c786.nq.gz
│   ├── 3b69ee425a95d802e64390552636954279ab5d9b.nq.gz
│   ├── 4351754c0c2c870b6b66ea6abfa7489b5057aba8.nq.gz
│   ├── 463b20c4ab26a3eef5e2559fc3c6f7a07c9a5fe8.nq.gz
│   ├── 48e04da3790885dc73f54444ab24a0287faacd0c.nq.gz
│   ├── 4ac964f06ebb46602130fb5d3e090f219bc688c3.nq.gz
│   ├── 7829312639e01a4d18682d231fd1f3e028cd5bbb.nq.gz
│   ├── 801c222e108b7be1389f284293bcd2e816069cd9.nq.gz
│   ├── 8b783e87f9e6ad53429649ef81e519f5d4648b56.nq.gz
│   ├── 948fc29dd54c0e71616e2251e97582e1bd58bd3c.nq.gz
│   ├── 9e0dfe865c538f154ec4a17b5f601eafff71fea7.nq.gz
│   ├── a0b46e782753aa407841f4428f226220ca5ecdf7.nq.gz
│   ├── b6de5f8b35d39bea2a6840c8abf681e9608b8085.nq.gz
│   ├── c44287c16f3abe638c7c6b17ab2aef47fc5d8f2d.nq.gz
│   ├── d159169d1050894d3ea3b98e1c965c4058208fe1.nq.gz
│   ├── d926c36c2425eea3693266a888b81ba2389aa715.nq.gz
│   ├── ea7c313ff7156d38c20a31158abc5486e5c86251.nq.gz
│   └── fa72415c1dfc5a0680c4562bd7cd491ea8d07ec9.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6a07f80dc53584a6400989f165f3ba767dcd1bf2.nq.gz
├── issue
│   └── issue.nq.gz
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

[sphinx-contrib/repl](https://github.com/sphinx-contrib/repl)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
