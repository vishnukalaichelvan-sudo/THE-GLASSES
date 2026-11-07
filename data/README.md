---
tags:
- curatorkit
configs:
- config_name: ppo
  default: true
  description: curatorkit ppo export, sha256 0842873909bfeececbc767be4d570ed9fd102108f3208718bc75be1d9cedd071
  data_files:
  - split: train
    path: ppo.jsonl
---

# Dataset Card: curatorkit_run

## Summary

- **Run timestamp**: 2026-11-07T07:53:02.719890Z
- **Wall clock time**: 0.4s
- **Pipeline config hash**: `5a7994542805b7a0`

## Source Documents

  - Unknown

## Pipeline Stages

| Step | Input | Passed | Recovered | Rejected | Forward |
|------|-------|--------|-----------|----------|---------|
| JSONLReader | 150 | 150 | — | 0 | 150 |
| SchemaGate | 150 | 150 | 0 | 0 | 150 |
| ExactDeduplicator | 150 | 150 | — | — | 150 |
| MinHashDeduplicator | 150 | 150 | — | — | 150 |
| TextCleaner | 150 | 150 | — | — | 150 |
| PPOExporter | — | 150 | — | — | 150 |

## Gate Pass Rates and Rejection Breakdown

- **JSONLReader**: 150/0 passed (N/A), 0 rejected
- **SchemaGate**: 150/150 passed (100.0%), 0 rejected


**Rejection reasons:**
  - None

## Deduplication

  - near_duplicates_removed: 0
  - surviving_count: 150

## Known Limitations

- MinHash threshold used: **0.85** — this is a starting point, not a universal answer. Adjust per domain (legal, medical, and other domain-specific corpora may need a lower threshold to avoid losing structurally similar but semantically valid examples).
- Table extraction requires `extract_tables: true` on the PDF reader and MinerU with GPU support. Disabled by default.
- Token counting uses a whitespace tokenizer by default. For exact LLM context window
  enforcement, enable `use_tiktoken: true` in the SchemaGate config.
- Both within-run (MinHash/Diversity) and cross-run (EmbeddingDeduplicator) deduplication
  are available. Cross-run dedup persists an embedding index across runs; use
  `embedding_reset_index: true` to start fresh.

## Reproduction

```bash
pip install curatorkit
curatorkit run pipeline.yaml --output-dir ./out/
```

## Tool Versions

- **curatorkit**: 0.1.23
- **python**: 3.12.10

## Configs

Load one with `datasets.load_dataset("<this folder or Hub repo>", "<config>")`.

| Config | Splits (rows) | Columns |
|--------|---------------|---------|
| `ppo` | train (150) | `prompt`: string |
