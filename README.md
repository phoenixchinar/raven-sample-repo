# RAVEN Credit Card Risk Assessment Sample

This repository is a YAML-native RAVEN authoring sample for assessing credit card transaction risk.

It models a transaction workflow that:

- accepts a credit card transaction record
- reads cardholder profile and velocity context from a risk history database
- applies a credit card risk ruleset
- produces a risk score, decision, reason code, and manual review flag

The repository is intended for VS Code Web authoring with the RAVEN extension. Raw YAML files under `raven/` are the source of truth.

## Layout

- `raven.config` declares the YAML-native project contract
- `.raven/` contains local authoring controls and agent guardrails
- `raven/records/` contains record and variable resources
- `raven/modules/` contains module interfaces, dependencies, tests, and database bindings
- `raven/rulesets/` contains the risk policy ruleset
- `raven/transactions/` contains the transaction graph

## IntelliSense Exercise Points

- Variable files under `raven/records/**/variables/*.yaml` use `type:` so the RAVEN extension can infer the variable resource from the path and offer valid type values.
- Module files use `module_type:` to exercise module enum completions.
- `rule_high_risk_tier_simulation.yaml` sets `simulation: true`, so rule condition logging can be tested without applying variable updates.
- Rule documents use the generic `WHEN ... THEN SET ...` business logic format.

## Authoring Rules

- Use immutable IDs for relationships.
- Do not add JSON authored resources.
- Do not use `raven.yaml` or `.raven/config.json`.
- Do not inline variable logic inside variable resources.
- Keep generated and local-only files under `.raven/local/`.
