
# Red Team OP Plan: CI/CD Pipeline Attack

### Objective
Compromise the CI/CD pipeline to introduce unauthorized code or configurations into production environments, leading to potential access and data exfiltration, downtime, or system manipulation.

### Overview
This operation simulates an adversary exploiting weaknesses within the CI/CD infrastructure, focusing on stages where code and configurations traverse through build, testing, and deployment stages. Attack techniques will be aligned with MITRE ATT&CK tactics for a structured, threat-informed approach.

---

### Operation Phases

#### 1. Reconnaissance

- **Objective**: Gather intelligence on the CI/CD environment, roles, tools, and configurations.
- **TTPs**:
  - **Techniques**:
    - **T1590** - Gather Victim Network Information (identify CI/CD systems, servers, and relevant network paths).
    - **T1592** - Gather Victim Identity Information (roles and permissions, especially those with deployment privileges).
  - **Procedures**: Scrape internal documentation, analyze developer profiles, identify common tech stacks (e.g., Jenkins, GitLab CI/CD), and target SCM (Source Code Management) repositories.

#### 2. Initial Access

- **Objective**: Gain a foothold within the CI/CD pipeline or access associated developer accounts.
- **TTPs**:
  - **Techniques**:
    - **T1199** - Trusted Relationship (exploit collaboration tools, insecure configurations, or authorized connections).
    - **T1078** - Valid Accounts (compromise developer credentials, such as GitHub or GitLab access tokens).
  - **Procedures**: Use phishing, credential stuffing, or social engineering to obtain CI/CD access credentials; identify and target Single Sign-On integrations for possible exploitation.

#### 3. Execution

- **Objective**: Introduce malicious code into the build pipeline or manipulate build processes.
- **TTPs**:
  - **Techniques**:
    - **T1071** - Application Layer Protocol (inject or modify build scripts, introduce malicious artifacts).
    - **T1059** - Command and Scripting Interpreter (insert unauthorized scripts into the CI/CD environment).
  - **Procedures**: Inject code modifications in build scripts, add scripts to deployment files, and modify configurations to escalate privilege or create backdoors.

#### 4. Persistence

- **Objective**: Maintain access within the CI/CD pipeline for repeated or long-term access.
- **TTPs**:
  - **Techniques**:
    - **T1547** - Boot or Logon Autostart Execution (leverage build and deploy triggers to reinitiate access).
    - **T1136** - Create Account (add a new, hidden account with high privileges in the CI/CD system).
  - **Procedures**: Modify permissions on repositories, add SSH keys, and leverage CI/CD webhook configurations to retain access to deployments.

#### 5. Defense Evasion

- **Objective**: Avoid detection by CI/CD logging and security monitoring.
- **TTPs**:
  - **Techniques**:
    - **T1027** - Obfuscated Files or Information (encode or obfuscate malicious code in deployment scripts).
    - **T1562** - Impair Defenses (disable security logging or alerting in CI/CD).
  - **Procedures**: Obfuscate payloads in scripts, selectively disable logs, manipulate timestamps, and clear system trails in build logs.

#### 6. Impact

- **Objective**: Deploy a payload that affects the integrity of the deployed application.
- **TTPs**:
  - **Techniques**:
    - **T1485** - Data Destruction (delete or alter crucial build artifacts).
    - **T1499** - Endpoint Denial of Service (introduce flaws or bottlenecks).
  - **Procedures**: Deploy modified applications to production to showcase impact, cause intentional failures in applications, or exfiltrate sensitive data for impact demonstration.

---

### Notes
- Use this as a structured plan for CI/CD-focused red teaming efforts.
- Maintain operational security (OPSEC) to avoid detection until the “Impact” phase.
- This plan assumes leveraging company-approved, realistic threat simulations without affecting actual production operations.

---

### References
- [MITRE ATT&CK Techniques for Enterprise](https://attack.mitre.org/techniques/enterprise/)
- Main Question (Base Prompt): Generate 1 Red Team Operation focusing on CICD attacks
- User-Provided Source: [NCC Group - 10 Real-World Stories of How We’ve Compromised CI/CD Pipelines](https://www.nccgroup.com/us/research-blog/10-real-world-stories-of-how-we-ve-compromised-cicd-pipelines/)
- GPT Version: GPT-4-Plus
