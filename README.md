# Email Threat Detection Pipeline (Simulation)

A browser-based simulation of a five-stage email threat-triage flow: header authentication check, confidence threshold, and escalation. It runs on scripted test scenarios to show how the stages fit together.

Built by **Ramon Cortez**

**Status:** Prototype. This is a simulation, not a working detector. Real DKIM and SPF verification and an intent classifier are planned but not yet implemented.

---

## Pipeline Stages (as simulated)

1. **Header check:** Shows DKIM and SPF results for each scripted scenario. The results are fixed values in the demo, not verified from raw headers.
2. **Confidence threshold:** Shows a confidence score per scenario and compares it to a 90% threshold. The scores are hardcoded, not produced by a model.
3. **Routing:** Shows which path a scenario would take (archive, escalate, or manual review).
4. **Escalation:** Displays the escalation step. No real review queue is connected.

## Planned Work

- Replace scripted header checks with real DKIM and SPF verification on raw email headers.
- Build and test an intent classifier, with documented test cases and a confidence threshold.
- Connect escalation to a real review queue and document the audit log format.

## Design Principles

- **Deterministic checks first:** Authentication checks should run before any probabilistic model.
- **Inspectable:** Every stage and threshold is visible in the code.
- **Complements existing tools:** Mature filters such as SpamAssassin and Rspamd already do DKIM/SPF checks and spam scoring. This project is a reference design for the triage flow, not a replacement for them.

## License

MIT

---

[Live Demo](https://ramon-email-threat.netlify.app)
