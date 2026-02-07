# 🛡️ OpenClaw Fortress: The "Just Use a VPS" Playbook

[![OpenClaw Hardware Hardening](https://img.shields.io/badge/Security-Rent--Free-red)](https://github.com/your-username/openclaw-fortress)
[![Ansible](https://img.shields.io/badge/Ansible-2.15+-black)](https://www.ansible.com/)
[![Tailscale](https://img.shields.io/badge/Mesh-Tailscale-blue)](https://tailscale.com/)

"I was just going to buy a Mac Mini—" **NO.** You need a fresh Linux VPS. It’s what everyone does. This repository contains the definitive Ansible playbook to turn a $5-a-month VPS into an impenetrable fortress for your OpenClaw AI assistant.

## 📺 The Inspiration
This configuration follows the "sane" security architecture outlined in the **"Interview with ‘Just use a VPS’ bro"**:

[![Interview with ‘Just use a VPS’ bro](https://img.youtube.com/vi/40SnEd1RWUU/0.jpg)](https://www.youtube.com/watch?v=40SnEd1RWUU&t=39s)

> *"You don't do security. Security needs to live rent-free in your mind at all times."*

---

## 🏗️ Architecture: The "Elimination Diet"
This playbook doesn't just install software; it creates a ghost in the machine:
* **Zero Public Ports:** SSH on Port 22 is dead. Port 2222 is blocked from the public web.
* **The Wormhole:** Access is only possible via a **Tailscale** private mesh.
* **User Isolation:** OpenClaw runs as a restricted `openclaw` user, installed via `curl` into `~/.openclaw`.
* **Self-Updating:** Because it's a user-scoped install, the bot can update its own binaries without `sudo`.
* **Persistence:** systemd user service with lingering — OpenClaw survives reboots without root.
* **OS-Level Isolation for AI Agents:** Landlock sandbox with **nono** — kernel‑enforced playpen: read home, exec trusted bins, write only data dirs, block non‑Tailscale egress. Think “agent in a playpen.” (new untested feature)

---

## 🚀 Deployment

### 1. Prerequisites
* A fresh **Ubuntu 24.04 LTS** VPS.
* A **Tailscale Auth Key** (from your Admin Console).
* Your API keys (Anthropic, OpenAI, or OpenRouter).

### 2. Setup Variables
Adapt the `group_vars/all.yml` file (keep this safe or use `ansible-vault`):

```yaml
tailscale_auth_key: "tskey-auth-yourkey"
llm_provider: "anthropic" # or "openai", "openrouter"
llm_api_key: "sk-ant-xxx"
messaging_provider: "telegram"
messaging_token: "123456:ABC-DEF"
```

## 🚀 Infrastructure

To run the OpenClaw Fortress with the necessary performance for agentic workflows (especially when compiling skill dependencies), we recommend a DigitalOcean Droplet with at least **2 vCPUs** and **4GB RAM**.

[![DigitalOcean Referral Badge](https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%201.svg)](https://www.digitalocean.com/?refcode=140cab9a88c2&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)

> **Bearded Pro-tip:** Using the link above helps support the ongoing development of this "Fortress" architecture.

## 🤝 Connect with the Visionary
If this playbook saved you from buying a Mac Mini, go thank the creator of the original lore:
* **X (Twitter):** [@kailentit](https://x.com/kailentit)
* **YouTube:** [Kai Lentit](https://www.youtube.com/@programmersarealsohuman5909)


