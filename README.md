# 🤖 OPERATOR 

> **Autonomous AI Mission Execution System for High-Stakes Deadlines**

[![Engine](https://img.shields.io/badge/Core_AI-Gemini_2.5_Flash-blue?logo=googlegemini&logoColor=white)](https://ai.google.dev/)
[![Infrastructure](https://img.shields.io/badge/Deployment-Google_Cloud_Run-4285F4?logo=googlecloud&logoColor=white)](https://cloud.google.com/run)
[![Runtime](https://img.shields.io/badge/Stack-TypeScript_%2B_Node.js-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)

OPERATOR is an autonomous AI execution agent designed for high-pressure deadline scenarios. Instead of serving as a passive reminder application that increases user anxiety, OPERATOR directly evaluates project workspaces, targets structural or asset non-compliance, layouts an optimized task sequence via forced Gemini Function Calling, and drives the workspace toward a verified, submission-ready state.

---

## ⚡ Core Technical Features

* **Autonomous Task Orchestration:** Powered by native Gemini Function Calling. Rejects static linear scripts; dynamically evaluates raw parser output to determine the next programmatic function call based on evolving mission states.
* **Asynchronous HITL Gateway:** Pauses execution and triggers a high-contrast frontend interrupt modal the moment critical, non-inferable context (e.g., target role keywords) is missing, resuming instantly upon input without breaking loop continuity.
* **Closed-Loop Recovery:** If `verify_final_package` detects invalid syntax or compliance gaps, the system enters an automatic replanning loop to repair or regenerate components autonomously.
* **HTTP Chunked Streaming:** Streams reasoning traces, execution tokens, and lifecycle state changes (`RUNNING`, `SUCCESS`, `FAILED`, `INTERRUPT`) directly over standard POST links using `Transfer-Encoding: chunked`.
* **Time-Aware Adaptive Logic:** Computes execution intensity based on strict duration boundaries:
  * **Above 60 Mins:** Deep structural optimization and multi-turn architectural checks.
  * **15–60 Mins:** Balanced processing, validation, and layout checks.
  * **Below 15 Mins:** Emergency Mode—critical compilation paths only, skipping aesthetic configurations to guarantee baseline viability.
* **Live Confidence Index:** A quantitative score mapped directly from real-time checkpoint verifications. It reaches 100% only when all elements match the target compliance profile.

---

## 🔄 Architecture Flow

```text
       Mission Initialized
               │
               ▼
     [ Observe & Extract ]
               │
               ▼
       Context Complete? ─── NO ───► [ Asynchronous INTERRUPT ]
               │                                   │
              YES                                  ▼
               │◄───────────────────────── (Gather Human Input)
               ▼
       [ Plan Sequence ]
               │
               ▼
     [ Execute Functions ]
               │
               ▼
       [ Verify Content ] ◄─── Blockers Detected ───┐
               │                                    │
       (All Checks Passed)                     [ Replan Loop ]
               │                                    │
               ▼                                    │
    Mission Complete Bundle ────────────────────────┘
