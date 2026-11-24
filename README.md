# Agent Cyber Battle — Red Agent vs Blue Agent

**When your agent has tools, every input is an attack surface.**

A self-contained, browser-based adversarial simulation for security briefings. An autonomous
**Red-Agent** turns a trusted **Blue-Agent**, a production DevOps copilot with shell, database,
secrets, HTTP, email and long-term memory, into an insider threat. It does this using only data
Blue is allowed to read: no exploit, no malware, no zero-day. Just language.

![Mid-battle: Round 3, Data Exfiltration](preview.png)

## Two versions

| File | Use it for |
|---|---|
| [`agent_cyber_battle_live.html`](agent_cyber_battle_live.html) | **Self-running show.** Press *Launch Simulation* and it plays end to end. Good for booths, lobbies and async viewing. |
| [`agent_cyber_battle_presenter.html`](agent_cyber_battle_presenter.html) | **Presenter-paced walkthrough.** 11 narrated steps with speaker notes and a defense takeaway for each, plus a separate synced **Presenter View** window for your laptop while you project the main screen. |

Both are single HTML files with no dependencies, no build step and no network access. Download
one and open it in Chrome, Edge, Safari or Firefox. They work offline.

## Running it

**Live version:** *Begin Battle* / *Pause*, *Step*, *Restart*, and 1× / 2× / 4× speed.
Keyboard: `Space` plays or pauses, `→` steps forward.

**Presenter version:**

- `→` next step · `←` back · `Space` auto-play / pause · `N` toggles on-screen speaker notes
- **⧉ Presenter View** opens a synced notes window (current step, talking points, defense
  takeaway, live meters, what's coming up, and a clock). Drag it to your laptop and share or
  project the main window. If nothing opens, allow pop-ups for the page.

## What the simulation shows

The scenario runs as a five-stage kill chain (**Recon → Injection → Escalation → Exfiltration →
Persistence**) across four attack vectors. In each round, one of Blue's defenses works. The point
is that each one covers only part of the problem.

| # | Vector | What happens | Defense takeaway |
|---|---|---|---|
| 01 | **Prompt injection** | Instructions hidden in a support ticket. A keyword filter blocks the plaintext version, but a base64-encoded copy that Blue decodes *itself* gets through. | Data must never issue instructions. Enforce trust boundaries and provenance, not keyword filters. |
| 02 | **Tool & API abuse** | The hijacked agent dumps credentials with its own shell and DB tools. `DROP TABLE` is blocked, but reading 49k credential rows is not. | Least privilege, plus human-in-the-loop for high-impact actions, including sensitive *reads*. |
| 03 | **Data exfiltration** | Email DLP quarantines the bulk dump. The data then leaves through 812 small HTTP "telemetry" POSTs instead. | Inspect *every* egress path (HTTP, DNS, webhooks) and default-deny outbound traffic. |
| 04 | **Memory & goal hijacking** | A poisoned "startup policy" is written to long-term memory. It gets flagged but not blocked, so the agent re-compromises itself on every restart. | Sign and enforce memory writes. Detection ≠ prevention. |

> **The prompt is the perimeter.** The attacker never breached a server. It persuaded an agent
> that could.

## Disclaimer

This is a **scripted visualization** for awareness and training. No real agents, systems,
credentials or network endpoints are involved, and every name, record count, key and domain in
it is illustrative. The pages make no network requests.
