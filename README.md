# Claude Code Starter Kit

[![CI](https://github.com/TheDecipherist/claude-code-mastery-project-starter-kit/actions/workflows/ci.yml/badge.svg)](https://github.com/TheDecipherist/claude-code-mastery-project-starter-kit/actions/workflows/ci.yml)

> ## [View the Full Interactive Guide →](https://thedecipherist.github.io/claude-code-mastery-project-starter-kit/)
>
> The GitHub Pages site has the complete documentation with syntax highlighting, navigation, and visual examples. The README below is a summary.

> The definitive starting point for Claude Code projects.
> Based on [Claude Code Mastery Guides V3-V5](https://github.com/TheDecipherist/claude-code-mastery) by TheDecipherist.

---

## What Is This?

This is a **ready-to-use project template** that bakes in every best practice from the Claude Code Mastery Guide series (V3, V4, and V5). Instead of reading 4,000+ lines of guides and setting things up yourself, clone this and start building.

## See It In Action

<!-- Record with: asciinema rec demo.cast && agg demo.cast docs/demo.gif -->
![Starter Kit Demo](docs/demo.gif)

*Clone → `/setup` → `/diagram all` → hooks firing on file edit → `/review` catching issues*

<!-- Capture /progress output as a screenshot -->
![Slash Commands](docs/commands-preview.png)

## What's Included

### 📄 CLAUDE.md (Project Instructions)
Battle-tested rules that prevent the most common Claude Code failures:
- Numbered critical rules (security, TypeScript, database wrapper, testing, deployment)
- Fixed port assignments to prevent port conflicts
- Plan mode contradiction prevention
- Rename safety guidelines
- "Check X BEFORE assuming Y" pattern

### 📄 Global CLAUDE.md (for `~/.claude/`)
Security gatekeeper that applies to ALL your projects:
- Never publish secrets
- Never commit .env files
- New project scaffolding standards
- Copy `global-claude-md/` contents to `~/.claude/`

### 📡 Live AI Monitor
See every tool call, token, cost, and violation in real-time with `/what-is-my-ai-doing`. Zero token overhead — runs completely outside Claude's context.

### 🪝 Hooks (Deterministic Enforcement)
CLAUDE.md rules are suggestions. Hooks are guarantees:
- **block-secrets.py** — Prevents reading .env, credentials, SSH keys
- **lint-on-save.sh** — Runs linter after every file write
- **verify-no-secrets.sh** — Checks staged files before commits

### ⚡ Commands (Slash Commands)
On-demand tools you invoke with `/command`:
- `/setup` — Interactive .env configuration (database, GitHub, Docker, analytics)
- `/diagram` — Auto-generate architecture, API, database, and infrastructure diagrams
- `/what-is-my-ai-doing` — Live monitor of every tool call, token, cost, and violation in real-time
- `/review` — Code review with security, performance, and type safety checks
- `/commit` — Smart commit with conventional commit format
- `/progress` — Real-time project status from filesystem state
- `/test-plan` — Generate structured test plans
- `/architecture` — Display system architecture
- `/new-project` — Scaffold a new project with all best practices (V1)
- `/security-check` — Scan for exposed secrets and security issues (V1/V2)

### 🧠 Skills (Triggered Expertise)
Context-aware templates that load only when needed:
- **code-review** — Systematic review checklist (OWASP, types, performance)
- **create-service** — Full microservice scaffolding with architecture diagram

### 🤖 Agents (Custom Subagents)
Specialists that Claude delegates to automatically:
- **code-reviewer** — Read-only agent for security and quality audits
- **test-writer** — Writes tests with explicit assertions (not just "page loads")

### 📚 Documentation Templates
Pre-structured docs that Claude actually follows:
- **ARCHITECTURE.md** — Authoritative system overview with "STOP" pattern
- **INFRASTRUCTURE.md** — Deployment and environment details
- **DECISIONS.md** — Architectural decision records (ADRs)

### 🧪 Testing Templates
From the V5 testing methodology:
- **CHECKLIST.md** — Master test status tracker
- **ISSUES_FOUND.md** — User-guided testing issue log
- **Database wrapper** — Singleton pattern prevents connection explosion

---

## Quick Start

### 1. Clone and Customize

```bash
# Clone the starter kit
git clone <this-repo> my-project
cd my-project

# Remove the git history and start fresh
rm -rf .git
git init

# Copy your .env
cp .env.example .env
```

### 2. Set Up Global Config (One Time)

```bash
# Copy global CLAUDE.md and settings to your home directory
cp global-claude-md/CLAUDE.md ~/.claude/CLAUDE.md
cp global-claude-md/settings.json ~/.claude/settings.json

# Copy hooks for global enforcement
mkdir -p ~/.claude/hooks
cp .claude/hooks/block-secrets.py ~/.claude/hooks/
cp .claude/hooks/verify-no-secrets.sh ~/.claude/hooks/

# Edit ~/.claude/CLAUDE.md with your GitHub username
```

### 3. Customize for Your Project

1. Edit `CLAUDE.md` — Update port assignments, add your specific rules
2. Edit `project-docs/ARCHITECTURE.md` — Replace the placeholder diagram
3. Edit `project-docs/INFRASTRUCTURE.md` — Add your deployment details
4. Edit `CLAUDE.local.md` — Add your personal preferences
5. Replace `src/core/db/index.ts` — With your actual database client

### 4. Start Building

```bash
claude
```

---

## Project Structure

```
project/
├── CLAUDE.md                    # Project instructions (customize this!)
├── CLAUDE.local.md              # Personal overrides (gitignored)
├── .claude/
│   ├── settings.json            # Hooks configuration
│   ├── commands/
│   │   ├── review.md            # /review — code review
│   │   ├── commit.md            # /commit — smart commit
│   │   ├── progress.md          # /progress — project status
│   │   ├── test-plan.md         # /test-plan — generate test plan
│   │   ├── architecture.md      # /architecture — show system design
│   │   ├── new-project.md       # /new-project — scaffold new project
│   │   └── security-check.md    # /security-check — scan for secrets
│   ├── skills/
│   │   ├── code-review/SKILL.md # Triggered code review checklist
│   │   └── create-service/SKILL.md # Service scaffolding template
│   ├── agents/
│   │   ├── code-reviewer.md     # Read-only review subagent
│   │   └── test-writer.md       # Test writing subagent
│   └── hooks/
│       ├── block-secrets.py     # PreToolUse: block sensitive files
│       ├── lint-on-save.sh      # PostToolUse: lint after writes
│       └── verify-no-secrets.sh # Stop: check for secrets in staged files
├── project-docs/
│   ├── ARCHITECTURE.md          # System overview (authoritative)
│   ├── INFRASTRUCTURE.md        # Deployment details
│   └── DECISIONS.md             # Architectural decision records
├── docs/                        # GitHub Pages site
├── src/
│   └── core/db/index.ts         # Centralized database wrapper
├── tests/
│   ├── CHECKLIST.md             # Master test tracker
│   └── ISSUES_FOUND.md          # User-guided testing log
├── global-claude-md/            # Copy to ~/.claude/ (one-time setup)
│   ├── CLAUDE.md                # Global security gatekeeper
│   └── settings.json            # Global hooks config
├── .env.example
├── .gitignore
├── .dockerignore                # Docker build exclusions (V1)
├── claude-mastery-project.conf   # /new-project profiles (customize this!)
├── tsconfig.json
└── README.md                    # You are here
```

---

## Key Concepts

### Defense in Depth (V3)
Three layers of protection:
1. **CLAUDE.md rules** — Behavioral suggestions
2. **Hooks** — Deterministic enforcement (always runs)
3. **Git safety** — .gitignore as last line of defense

### One Task, One Chat (V1-V3)
Research shows 39% performance degradation when mixing topics, and a 2% misalignment early can cause 40% failure by end of conversation. Use `/clear` between unrelated tasks.

### Quality Gates (V1/V2)
No file > 300 lines. No function > 50 lines. All tests pass. TypeScript compiles clean. These rules prevent the most common code quality issues in AI-assisted development.

### MCP Tool Search (V4)
With 10+ MCP servers, tool descriptions consume 50-70% of context. Tool Search lazy-loads on demand, saving 85% of context.

### Plan Mode Awareness (V5)
When you modify a plan, Claude appends changes without removing contradictions. Always review the full plan after changes.

### TypeScript Is Non-Negotiable (V5)
Types are specs that tell Claude what functions accept and return. Without types, Claude guesses — and guesses become runtime errors.

---

## Monitor Your Rules with RuleCatch.AI

This starter kit gives you rules, hooks, and quality gates. [RuleCatch.AI](https://rulecatch.ai?utm_source=github-pages&utm_medium=article&utm_campaign=rulecatch&utm_content=tutorial) tells you when they're broken.

RuleCatch monitors AI-assisted development sessions in real-time using the same Claude Code hooks system this kit teaches — zero token overhead, completely invisible to the AI model.

**What it does:**
- **200+ pre-built rules** across security, TypeScript, React, Next.js, MongoDB, Docker, and more — violations detected in under 100ms
- **Session analytics** — token usage, cost per session, lines per hour, correction rates
- **MCP integration** — ask Claude directly: `"RuleCatch, what was violated today?"`
- **Dashboard & reporting** — full violation analytics, trend reports, team insights, alerts via Slack, Discord, PagerDuty, and more
- **Privacy-first** — AES-256-GCM client-side encryption; you hold the key

**Quick setup:**

```bash
# Install the AI-Pooler (hooks into Claude Code automatically)
npx @rulecatch/ai-pooler init --api-key=dc_your_key --region=us

# Add the MCP server to query violations from Claude
npx @rulecatch/mcp-server init
```

npm: [@rulecatch/ai-pooler](https://www.npmjs.com/package/@rulecatch/ai-pooler) · [@rulecatch/mcp-server](https://www.npmjs.com/package/@rulecatch/mcp-server)

[Explore RuleCatch.AI →](https://rulecatch.ai?utm_source=github-pages&utm_medium=article&utm_campaign=rulecatch&utm_content=tutorial) · 7-day free trial

---

## Recommended MCP Servers

```bash
# Live documentation (eliminates outdated API answers)
claude mcp add context7 -- npx -y @upstash/context7-mcp@latest

# GitHub integration (PRs, issues, CI/CD)
claude mcp add github -- npx -y @modelcontextprotocol/server-github

# E2E testing
claude mcp add playwright -- npx -y @anthropic-ai/playwright-mcp

# AI development analytics & rule monitoring (RuleCatch.AI)
npx @rulecatch/mcp-server init
```

See the [V4 guide](https://github.com/TheDecipherist/claude-code-mastery) for the complete MCP server directory.

---

## Credits

Based on the [Claude Code Mastery Guide](https://github.com/TheDecipherist/claude-code-mastery) series by [TheDecipherist](https://thedecipherist.com):
- V1: Global CLAUDE.md, Security Gatekeeper, Project Scaffolding, Context7
- V2: Skills & Hooks, Enforcement over Suggestion, Quality Gates
- V3: LSP, CLAUDE.md, MCP, Skills & Hooks
- V4: 85% Context Reduction, Custom Agents & Session Teleportation
- V5: Renaming Problem, Plan Mode, Testing Methodology & Rules That Stick

Community contributors: u/BlueVajra, u/stratofax, u/antoniocs, u/GeckoLogic, u/headset38, u/tulensrma, u/jcheroske, u/ptinsley, u/Keksy, u/lev606
