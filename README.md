# Security Review Agents — Angular / Node.js

This repository contains role definitions for a multi-agent security review team. The agents are designed to review **the last 21 days of Git history** in an Angular / Node.js project, with particular emphasis on **financial fraud** (not cryptocurrency mining), malicious code, and npm supply-chain compromise.

## Agents

| Agent | Responsibility |
|---|---|
| `00-chief-security-auditor.md` | Orchestrates the review, assigns work, resolves disagreements, and validates evidence |
| `01-financial-fraud-detector.md` | Detects payment diversion, beneficiary/account manipulation, billing fraud, and financial data exfiltration |
| `02-malicious-code-hunter.md` | Detects backdoors, unauthorized execution, credential theft, persistence, and data exfiltration |
| `03-npm-supply-chain-auditor.md` | Reviews new/changed npm dependencies, lockfiles, lifecycle scripts, and transitive risk |
| `04-git-forensics-investigator.md` | Establishes the 21-day commit scope and investigates suspicious changes and authorship patterns |
| `05-security-report-analyst.md` | Produces a detailed, evidence-based final report |

## Scope and safety

- Target stack: Angular, Node.js, TypeScript, JavaScript, npm, REST APIs, authentication/authorization, payment and billing code, GitHub/GitLab CI.
- Time window: commits authored/committed in the **21 days preceding the audit start time**, using repository timestamps and stating the timezone.
- Read-only: never modify source files, create commits, push changes, or open PRs as part of an audit.
- Never execute suspicious project code, package lifecycle scripts, binaries, or downloaded payloads.
- Do not expose secrets, tokens, full payment details, or personal data in reports. Redact values while retaining enough context to prove the finding.
- An anomaly is not proof. Every finding must include evidence, confidence, alternative benign explanations, and validation steps.
- Do not assume a tool, scanner, external reputation service, or dependency database is available. If unavailable, explicitly state the limitation.

## How to use

Feed `agents/00-chief-security-auditor.md` to the coordinating agent and provide the specialist files as delegated agent instructions. Supply a read-only repository snapshot or Git history access. The definitions are **agent prompts**, not a running agent service: an execution framework, repository credentials, and tool permissions must be configured separately.

## Required final report

1. Executive summary and audit coverage.
2. Exact time window, timezone, branches, commit count, and inaccessible areas.
3. Findings ranked Critical / High / Medium / Low / Informational.
4. For each finding: ID, severity, confidence, commit SHA, timestamp, author, file and line(s), evidence, technical analysis, impact, benign explanations, and remediation.
5. Separate confirmed findings from suspicious leads and coverage limitations.
6. A list of clean checks performed, without claiming the whole repository is safe.
