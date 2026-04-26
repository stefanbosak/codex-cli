<div align="center">

# 🤖 OpenAI codex CLI

**Containerized OpenAI codex CLI (Hardened)**

[![build_status_badge](../../actions/workflows/docker-image-native-multiplatform-pipeline.yml/badge.svg?branch=main)](.github/workflows/docker-image-native-multiplatform-pipeline.yml)
[![codex](https://img.shields.io/badge/GitHub-Repository-blue?logo=github)](https://github.com/openai/codex)
[![Documentation](https://img.shields.io/badge/Docs-GitHub-green?logo=github)](https://developers.openai.com/codex)
[![MCP](https://img.shields.io/badge/MCP-Servers-orange)](https://mcpservers.org/)

</div>

---

## 📦 Latest Build

<!-- VERSION_INFO_START -->
| Component | Version |
|-----------|---------|
| **OpenAI codex CLI** | [`0.126.0-alpha.3`](https://github.com/openai/codex/releases/tag/rust-v0.126.0-alpha.3) |

> 🔄 Last updated: 2026-04-26T07:37:20Z · [Build #46](https://github.com/stefanbosak/codex-cli/actions/runs/24951265592)
<!-- VERSION_INFO_END -->

---

## 📋 Overview

This repository provides a fully automated preparation of  <span style="color: #0969da;">**containerized**</span> [OpenAI codex CLI](https://github.com/OpenAI/codex) environment with integrated <span style="color: #8250df;">**MCP server**</span> support using <span style="color: #1a7f37;">**Docker-in-Docker**</span> architecture.

### About solution
- Sandboxing environment for AI scope (reduced possible negative impact via isolation)
- Automated packaging of current tool versions (optimized maintenance effort via automation)
- Strong focus on security (mitigated security issues and vulnerabilities through hardening)
- Simplification of the initial run-up (see: [Container runner script](./codex.sh), [OpenAI codex setup](./.codex/settings.json), [Environment configuration](./.codex/.env))

- **Container image is:**
  - keyless-signed via cosign using GitHub OIDC certificate issuer (trusted verifiable source)
  - automatically built when a new pre-release of OpenAI codex CLI is detected (scheduled monitoring - every hour)

### 📚 Resources

- 📖 [Official Documentation](https://docs.OpenAI.com/cli/overview)
- 📖 [AI models database](https://models.dev)
- 🤖 **Supported AI Models**: GPT 5.4
  - **Recommended models**:
    - <span style="color: #a371f7;">**OpenAI GPT 5.4**</span> - [Documentation](https://openai.com/index/introducing-gpt-5-4/): Low, Medium, High, Extra High
  - **Effective Prompting**:
    - Save output to prevent data loss (reduce costs)
    - Iteratively processing excessively long messages (drop error rate ~<10%)
    - XML tags ensure structural clarity (compliance increase to ~>98 %)
    - Validate continuously (maintain ~>95% accuracy)
    - Instruct what to avoid, not what to do (significantly reduce hallucination by ~>60 %)
    - Contextualize personas (~<15 % improvement using personas)

### OpenAI IP prefixes, subdomains for whitelisting, status

- curl -s https://openai.com/chatgpt-connectors.json
- curl -s https://status.openai.com/api/v2/summary.json | jq '.status'

### ⚠️ Important Notices

> [!NOTE]
> All files in this repository are well-commented with relevant implementation details.

> [!IMPORTANT]
> Always review and understand the code before executing any commands.

> [!CAUTION]
> Users are solely responsible for any modifications or execution of code from this repository.

## 🛠 Utilities
- [uv](https://github.com/astral-sh/uv) - An extremely fast Python package installer and resolver
- [bun](https://github.com/oven-sh/bun) - All-in-one JavaScript runtime and toolkit for faster development
- [mdflow](https://github.com/johnlindquist/mdflow) - Markdown-based workflow automation tool for streamlined task execution

## 🔌 MCP Servers

### <span style="color: #8250df;">🧠 Reasoning & Documentation</span>

#### **sequentialthinking** - <span style="color: #8250df;">Step-by-Step Reasoning</span>
- **Benefits:** <span style="color: #1a7f37;">Reduces token consumption by 5-55%</span>
- **Documentation:** [Sequential Thinking MCP Server](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking)

#### **ref** - <span style="color: #8250df;">Documentation Search</span>
- **Type:** <span style="color: #0969da;">HTTP</span>
- **URL:** `https://api.ref.tools/mcp`
- **Authentication:** <span style="color: #d73a49;">Requires `REF_API_KEY`</span>
- **Benefits:** <span style="color: #1a7f37;">Essential for efficient context retrieval</span>
- **Documentation:** [Ref.tools](https://ref.tools/)

---

### <span style="color: #1a7f37;">🌐 Utilities</span>

#### **fetch** - <span style="color: #1a7f37;">Web Fetching</span>
- **Documentation:** [Fetch MCP Server](https://github.com/modelcontextprotocol/servers/tree/main/src/fetch)

#### **time** - <span style="color: #1a7f37;">Time & Timezone</span>
- **Documentation:** [Time MCP Server](https://github.com/modelcontextprotocol/servers/tree/main/src/time)

---

### <span style="color: #0969da;">🗄️ Database & Storage</span>

#### **postgres** - <span style="color: #0969da;">PostgreSQL Integration</span>
- **Documentation:** [MCP Toolbox for Databases](https://github.com/googleapis/genai-toolbox)
- ⚠️ **Note:** <span style="color: #d73a49;">Linux ARM64 architecture not currently supported ([issue](https://github.com/googleapis/genai-toolbox/issues/2754))</span>

---

### <span style="color: #d73a49;">📊 Monitoring & Logging</span>

#### **grafana** - <span style="color: #d73a49;">Grafana</span>
| test | production |
| -----|------------|
| [agent](.codex/agents/grafana-tst.agent.md) | [agent](.codex/agents/grafana-prd.agent.md) |
| [skill](.codex/skills/grafana-tst/SKILL.md) | [skill](.codex/skills/grafana-prd/SKILL.md) |
- **Documentation:** [Grafana MCP Server](https://github.com/grafana/mcp-grafana)

#### **graylog** - <span style="color: #d73a49;">Graylog</span>
| test | production |
| -----|------------|
| [agent](.codex/agents/graylog-tst.agent.md) | [agent](.codex/agents/graylog-prd.agent.md) |
| [skill](.codex/skills/graylog-tst/SKILL.md) | [skill](.codex/skills/graylog-prd/SKILL.md) |
- **Authentication:** <span style="color: #d73a49;">Authorization header required</span>
- **Documentation:** [Graylog MCP Documentation](https://go2docs.graylog.org/current/setting_up_graylog/model_context_protocol__mcp__tools.htm)


## 📁 Repository Structure

### <span style="color: #8250df;">Configuration Files</span>
| File | Description | Note |
|------|-------------|------|
| [`settings.json`](./.codex/settings.json) | <span style="color: #0969da;">codex CLI configuration</span> | |
| [`.env`](./.codex/.env) | <span style="color: #1a7f37;">Environment variables</span> | |
| [`commands`](./.codex/commands) | <span style="color: #1a7f37;">Commands</span> | [docs](https://docs.OpenAI.com/cli/custom-commands) |
| [`rules`](./.codex/rules) | <span style="color: #1a7f37;">Rules</span> | [docs](https://docs.OpenAI.com/cli/rules) |

### <span style="color: #0969da;">Docker & Build</span>
| File | Description |
|------|-------------|
| [`Dockerfile`](./Dockerfile) | <span style="color: #0969da;">Container image configuration</span> |
| [`codex-build.sh`](./codex-build.sh) | <span style="color: #1a7f37;">Build automation script</span> |
| [`codex.sh`](./codex.sh) | <span style="color: #1a7f37;">Execution wrapper script</span> |
| [`act.sh`](./act.sh) | <span style="color: #1a7f37;">Act tool script</span> |

## Other resources


## 🐳 Container Images

### <span style="color: #0969da;">Available Registries</span>

| Registry | Network Support | Pull Command |
|----------|----------------|--------------|
| [**GitHub CR**](https://github.com/stefanbosak/codex-cli/pkgs/container/codex-cli) | <span style="color: #8250df;">IPv4 only</span> | `docker pull ghcr.io/stefanbosak/codex-cli:initial` |
| [**Docker Hub**](https://hub.docker.com/r/developmententity/codex-cli) | <span style="color: #1a7f37;">IPv4 & IPv6</span> | `docker pull developmententity/codex-cli:initial` |

---

<div align="center">

<span style="color: #8250df;">**Made with ❤ for ⚡ efficiency and 🔒 security**</span>

</div>
