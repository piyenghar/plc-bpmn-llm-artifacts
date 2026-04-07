# Process-Aware OT Security Requirements: Data Artifacts

This repository provides the **data artifacts** used in our study on LLM-based generation and evaluation of IEC 62443-aligned PLC security requirements with BPMN-derived process context.

## Scope of this release

This is a **data-only release**.  
It includes scenario definitions, baseline concept sets, model outputs, and aggregated evaluation results.

Code is intentionally omitted from this release.

---

## Included files

### 1) `data/scenarios.json`
Defines the scenario and prompt-context design used for generation.

Each scenario object contains:

- `scenario_id`
- `system_context`
- `task_name`
- `previous_task`
- `next_task`
- `expected_artifact`
- `iec62443_principles` (list)

This file represents the BPMN-derived context abstraction used in prompts.

---

### 2) `data/keyword_baselines.json`
Defines keyword/concept baselines per engineering task used for concept-coverage evaluation.

For each task, baseline items describe the expected IEC 62443-aligned concepts.

---

### 3) `outputs/results.json`
Raw generation outputs for all runs.

Each record includes:

- `timestamp_utc`
- `scenario_id`
- `task_name`
- `expected_artifact`
- `prompt_mode`
- `model`
- `prompt`
- `response` (model-generated requirements)

---

### 4) `outputs/annotated_results.json`
Run-level outputs enriched with evaluation annotations.

Includes matching and scoring details such as:

- baseline items
- per-item match details
- `matched_count`
- `pass` / `fail` status (threshold-based)
- additional diagnostic fields used in analysis

---

### 5) `outputs/evaluation_summary.json`
Aggregated evaluation statistics for quick verification and reuse.

Contains summary blocks such as:

- `overall`
- `by_model`
- `by_prompt_mode`
- `by_task_name`
- `baseline_item_hits`

---

## Experimental framing (as reflected by artifacts)

- Prompt modes:
  - `task_only`
  - `bpmn_only`
  - `standards_only`
  - `bpmn_plus_standards`
- Evaluated models: as listed in `results.json`
- Pass rule (see summary file):  
  `pass if matched_count >= 3 of 5 baseline items`

---

## Notes for users

- `results.json` contains full prompt and generated text outputs.
- `annotated_results.json` and `evaluation_summary.json` are sufficient for most secondary analyses.
- Field names should be treated as the source of truth for parsing.

---

## Reproducibility statement

This artifact release is intended to support **result inspection, validation, and reuse of data outputs**.  
A full code release is not included in this repository version.

---

## Citation

If you use these artifacts, please cite the corresponding paper:

> Padma Iyenghar and Elke Pulvermüller. “Process-Aware Generation of Operational Technology (OT) Security Requirements Using BPMN Context and Large Language Models.” In Proceedings of the 21st International Conference on Evaluation of Novel Approaches to Software Engineering (ENASE 2026). SciTePress, 2026.

(Replace with final venue citation when available.)
