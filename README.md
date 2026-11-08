# Repolex Knowledge Graph of bentoml/OpenLLM

RDF knowledge graph data for [bentoml/OpenLLM](https://github.com/bentoml/OpenLLM), parsed by [repolex](https://repolex.ai).

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
rlex download bentoml/OpenLLM
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 200b37fbf6f75b174e0737b937b886af460495e9
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 200b37fbf6f75b174e0737b937b886af460495e9
│           └── chunk-001.nq.gz
├── blob
│   ├── 194f0de50131241c25c51fd00dabe31d1709497a.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2b0a0a8a71844a6e3402b05d743db6218cccea5a.nq.gz
│   ├── 2c0733315e415bfb5e5b353f9996ecd964d395b2.nq.gz
│   ├── 2cf4e60a66014bc819f0db566ca954439c113323.nq.gz
│   ├── 3c804aa18c0443131346c145a9c3f6028ee34540.nq.gz
│   ├── 4c92bd39b67aaa69af6f3f31a5a83a1188c47f14.nq.gz
│   ├── 4e24e9176b9e15a598267c2c6de4c21ba04f5722.nq.gz
│   ├── 4f9521ed04938a812a7d015ec4babc964f0ccd0b.nq.gz
│   ├── 50db426818743e28361668385a6b35c08149361e.nq.gz
│   ├── 6510b78a27453f16ad73202691cbc00354b7ae8f.nq.gz
│   ├── 6725a59fc54a7f85310981d663876b68e0d684d2.nq.gz
│   ├── 781f2ddd3c751136f5f0ffb5c2d1cece08585048.nq.gz
│   ├── 7c7cfda3221e3b666d420ee93c2e4d671cd3c93f.nq.gz
│   ├── 7f08b8ef05c978566583ae4d10918b59a106efb7.nq.gz
│   ├── 83d331b72d46682122c35f8dd9980ffdee9e3b71.nq.gz
│   ├── 877a9ed9688311ae74a626261f6f128bc30daf16.nq.gz
│   ├── 8f7a85ed87a47ec9fb69048fa7c6af45ef1ffa07.nq.gz
│   ├── 8fb235d7045be0330d94bcb3abd2ac43badaa197.nq.gz
│   ├── 92f52bb125c3f63aa2302e2610cc20d7e560c183.nq.gz
│   ├── 93ebf319c1560595bafe1fd546f7ce7f3dbf27a3.nq.gz
│   ├── 9c63418b8dc31a423581eeba12fa12af8cb4fb5c.nq.gz
│   ├── 9d99305c24c8ee76a5b63ebb112b26981c8899e7.nq.gz
│   ├── a0baf626b31da704e18fd9b25b686e61bd09b864.nq.gz
│   ├── b00331cdbffdb6ad2b72f71f0b8e33394a19393a.nq.gz
│   ├── b4eb18b5c47e66a143125978a3d0a1e59b08ac4f.nq.gz
│   ├── b6d4302840b71f8332421a7dab67fcdb89151579.nq.gz
│   ├── c3646ba69151094c8e18ff60b32216ccff2dab6d.nq.gz
│   ├── c5ef99867c0a4eef1f947b6c933a4c698ff64171.nq.gz
│   ├── caf11c871c2a52f3d3b709a09a539759a769dce8.nq.gz
│   ├── d94d33bea6184a89a9de87dde72c900a72c85593.nq.gz
│   ├── d9ea71920b482c8403fa78860b8bfd896ed025ed.nq.gz
│   ├── e02d7b5530593b3ec31ef5a13a199ba324859805.nq.gz
│   ├── e0455979e4709cfa635337e7fc42561e4e56907a.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f3d1112746006cba4a06a5b128415156124f23b4.nq.gz
│   ├── f8ebc6941f18433fcee8f32982b8eaf8ea2cbb01.nq.gz
│   ├── f9a997c9ff9a8461cced5514c2fb10e9af3c9275.nq.gz
│   └── fb3f72752ec149c3b9d99ce6bc0275abc405e62b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 200b37fbf6f75b174e0737b937b886af460495e9.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 47 files
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

[bentoml/OpenLLM](https://github.com/bentoml/OpenLLM)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
