<div align="center">

# apktool-mcp-server (Part of Zin's Reverse Engineering MCP Suite)

[![MCP Toplist](https://mcptoplist.com/badge/glama%2Fzinja-coder%2Fapktool-mcp-server.svg)](https://mcptoplist.com/server/glama%2Fzinja-coder%2Fapktool-mcp-server)

⚡ Fully automated MCP server built on top of apktool to analyze Android APKs using LLMs like Claude — uncover vulnerabilities, parse manifests, and reverse engineer effortlessly.

![GitHub contributors apktool-mcp-server](https://img.shields.io/github/contributors/zinja-coder/apktool-mcp-server)
![GitHub all releases](https://img.shields.io/github/downloads/zinja-coder/apktool-mcp-server/total)
![GitHub release (latest by SemVer)](https://img.shields.io/github/downloads/zinja-coder/apktool-mcp-server/latest/total)
![Latest release](https://img.shields.io/github/release/zinja-coder/apktool-mcp-server.svg)
![Python 3.10+](https://img.shields.io/badge/python-3%2E10%2B-blue)
[![License](http://img.shields.io/:license-apache-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)

</div>

<!-- It is a still in early stage of development, so expects bugs, crashes and logical erros.-->

<div align="center">
    <img alt="banner" height="480px" widht="620px" src="https://github.com/user-attachments/assets/eb9037f2-d1c7-45e0-8871-ca8aaade0dd0">
</div>

<!--![apktool-mcp-server-banner.png](docs/assets/apktool-mcp-server-banner.png)-->

Image generated using AI tools.

---

## 🤖 What is apktool-mcp-server?

**apktool-mcp-server** is a MCP server for the [Apk Tool](https://github.com/iBotPeaches/apktool) that integrates directly with [Model Context Protocol (MCP)](https://github.com/anthropic/mcp) to provide **live reverse engineering support with LLMs like Claude**.

Think: "Decompile → Context-Aware Code Review → AI Recommendations" — all in real time.

Watch the demo!

https://github.com/user-attachments/assets/d50251b8-6b1c-4341-b18e-ae54eb24a847

- **Solving the CTFs**



https://github.com/user-attachments/assets/c783a604-a636-4e70-9fa8-37e3d219b20b


## Other projects in Zin MCP Suite
 - **[JADX-AI-MCP](https://github.com/zinja-coder/jadx-ai-mcp)**
 - **[JADX-MCP-Server](https://github.com/zinja-coder/jadx-mcp-server)**
 - **[ZIN-MCP-Client](https://github.com/zinja-coder/zin-mcp-client)**

## Current MCP Tools

The following MCP tools are available:

- `build_apk()` — Build an APK from a decoded APKTool Project.
- `get_manifest()` — Get the AndroidManifest.xml content from a decoded APK project. 
- `get_apktool_yml()` — Get apktool.yml information from a decoded APK project. 
- `list_smali_directories()` — List all smali directories in a project. 
- `list_smali_files()` — List smali files in a specific smali directory, optinally filtered by package prefix.
- `get_smali_file()` — Get content of a specific smali file by class name. 
- `modify_smali_file()` — Modify the content of a specific smali file. 
- `list_resources()` — List resources in a project, optionally filtered by resource type. 
- `get_resource_file()` — Get Content of a specific resource file. 
- `modify_resource_file()` — Modify the content of a specific resource file. 
- `search_in_file()` — Search for a pattern in files with specified extensions. 
- `clean_project()` — Clean a project directory to prepare for rebuilding.
- `decode_apk()` — Decode an APK file using APKTool, extracting resources and smali code. 

---

## 🗒️ Sample Prompts


### 🔍 Basic Code Understanding

- “List all smali directories for the dvac project.”

- “Show me all the smali files under the package prefix com.vulnerable.component in the dvac project.”

- “Get the smali code for the class com.vulnerable.component.MainActivity.”

- “Compare MainActivity.smali with its previous version and show differences.”

- “Search for usage of startActivity in smali files of dvac project.”

### 🛡️ Vulnerability Detection

- “Analyze declared permissions in the dvac AndroidManifest.xml and flag dangerous ones.”

- “Search for hardcoded URLs or IPs in all .xml and .smali files in the project.”

- “Find all uses of PendingIntent.getActivity in smali files.”

- “Check for exported activities or receivers in dvac’s AndroidManifest.xml.”

- “List all smali files that access android.permission.SEND_SMS or READ_CONTACTS.”

### 🛠️ Reverse Engineering Helpers

- “Decode this APK: dvac.apk and create a project called dvac.”

- “Create a new APKTool project called test-harness.”

- “Clean the dvac project before rebuild.”

- “Extract DEX files from dvac project for external analysis.”

- “Modify MainActivity.smali to insert a log line at the beginning of onCreate().”

### 📦 Static Analysis

- “Get the complete AndroidManifest.xml from dvac project.”

- “Show the contents of apktool.yml for the dvac project.”

- “List all resource files of type layout.”

- “Search for the word password in all resource and smali files.”

- “Check which permissions are used and compare them against typical over-permissioning risks.”

### 🤖 AI Code Modification

- “Modify the onCreate() method in MainActivity.smali to add a toast message.”

- “Replace all http:// links with https:// in strings.xml.”

- “Add the android:exported=false attribute to all activities in the AndroidManifest.xml.”

- “Patch the method validateLogin in LoginManager.smali to always return true.”

- “Add logging statements to every method in MainActivity.smali.”

### 📄 Documentation & Metadata

- “List all decoded APKTool projects in the workspace.”

- “Show me the apktool.yml config to review the version, original APK metadata, and compression settings.”

- “Get all available Android devices connected via ADB. (To be migrated to ADB MCP Server.)”

- “Get metadata about the project dvac from its apktool.yml.”

- “Check which APKTool version is currently installed on the server.”
---

## 🛠️ Getting Started 
### 1. Downlaod from Releases: https://github.com/zinja-coder/apktool-mcp-server/releases

```bash
# 0. Download and install apktool
https://apktool.org/docs/install

# 1. Test whether apktool has been correctly configured in the environment variables
$ apktool -version

# 2. Download the apktool-mcp-server-<version>.zip
https://github.com/zinja-coder/apktool-mcp-server/releases

# 3. 
unzip apktool-mcp-server-<version>.zip

├apktool-mcp-server/
  ├── apktool_mcp_server.py
  ├── requirements.txt
  ├── README.md
  ├── LICENSE

# 4. Navigate to apktool-mcp-server directory
cd apktool-mcp-server

# 5. This project uses uv - https://github.com/astral-sh/uv instead of pip for dependency management.
    ## a. Install uv (if you dont have it yet)
curl -LsSf https://astral.sh/uv/install.sh | sh
    ## b. OPTIONAL, if for any reasons, you get dependecy errors in apktool-mcp-server, Set up the environment
uv venv
source .venv/bin/activate  # or .venv\Scripts\activate on Windows
    ## c. OPTIONAL Install dependencies
uv pip install httpx fastmcp

# The setup for apktool-mcp-server is done.
```

## 2. Running on Local LLM Using Ollama and Zin MCP Client - Recommended

<div align="center">
    <a href="https://github.com/zinja-coder/zin-mcp-client">
    <img alt="zin-mcp-client" height="360px" widht="480px" src="https://github.com/user-attachments/assets/0e8e0ecd-0520-422e-a007-03dc62c4118e">
    </a>
</div>

⚡ Lightweight, Fast, Simple, CLI-Based MCP Client for STDIO MCP Servers, to fill the gap and provide bridge between your local LLMs running Ollama and MCP Servers.

Check Now: https://github.com/zinja-coder/zin-mcp-client

Demo: Coming soon...

## 🤖 3. Claude Desktop Setup

Make sure Claude Desktop is running with MCP enabled.

For instance, I have used following for Kali Linux: https://github.com/aaddrick/claude-desktop-debian

Configure and add MCP server to LLM file:
```bash
nano ~/.config/Claude/claude_desktop_config.json
```

   - Windows: `%APPDATA%\Claude\claude_desktop_config.json`
   - macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`

And following content in it:
```json
{
    "mcpServers": {
        "apktool-mcp-server": {
            "command": "/<path>/<to>/uv", 
            "args": [
                "--directory",
                "</PATH/TO/>apktool-mcp-server/",
                "run",
                "apktool_mcp_server.py"
            ]
        }
    }
}
```

Replace:

- `path/to/uv` with the actual path to your `uv` executable
- `path/to/apktool-mcp-server` with the absolute path to where you cloned this
repository

Then, navigate code and interact via real-time code review prompts using the built-in integration.

## 4. Cherry Studio Setup

If you want to configure the MCP tool in Cherry Studio, you can refer to the following configuration.
- Type: stdio
- command: uv
- argument:
```bash
--directory
path/to/apktool-mcp-server
run
apktool_mcp_server.py
```
- `path/to/apktool-mcp-server` with the absolute path to where you cloned this
repository

## To report bugs, issues, feature suggestion, Performance issue, general question, Documentation issue.
 - Kindly open an issue with respective template.

 - Tested on Claude Desktop Client, support for other AI will be tested soon!

## 🙏 Credits

This project is a MCP Server for [Apktool](https://github.com/iBotPeaches/apktool), an amazing open-source Android reverse engineering tool created and maintained by [@iBotPeaches](https://github.com/iBotPeaches). All core APK decoding and resource processing logic belongs to them. I have only extended it to support my MCP server with AI capabilities.

[📎 Original README (Apktool)](https://github.com/iBotPeaches/apktool)

The original README.md from Apktool is included here in this repository for reference and credit.

Also huge thanks to [@aaddrick](https://github.com/aaddrick) for developing Claude desktop for Debian based Linux.

And in last, thanks to [@anthropics](https://github.com/anthropics) for developing the Model Context Protocol and [@FastMCP](https://github.com/jlowin/fastmcp) team.

And all open source project maintainers and contributos which provies libraries and dependencies to make project like this possible.

## 📄 License

apktool-mcp-server and all related projects inherits the Apache 2.0 

## ⚖️ Legal Warning

**Disclaimer**

The tools `apktool-mcp-server` and all related tools under this project are intended strictly for educational, research, and ethical security assessment purposes. They are provided "as-is" without any warranties, expressed or implied. Users are solely responsible for ensuring that their use of these tools complies with all applicable laws, regulations, and ethical guidelines.

By using `apktool-mcp-server`, you agree to use them only in environments you are authorized to test, such as applications you own or have explicit permission to analyze. Any misuse of these tools for unauthorized reverse engineering, infringement of intellectual property rights, or malicious activity is strictly prohibited.

The developers of `apktool-mcp-server` shall not be held liable for any damage, data loss, legal consequences, or other consequences resulting from the use or misuse of these tools. Users assume full responsibility for their actions and any impact caused by their usage.

Use responsibly. Respect intellectual property. Follow ethical hacking practices.

---

## 🙌 Contribute or Support

## Contributing

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat-square)](CONTRIBUTE.md)

- Found it useful? Give it a ⭐️
- Got ideas? Open an [issue](https://github.com/zinja-coder/apktool-mcp-server/issues) or submit a PR
- Built something on top? DM me or mention me — I’ll add it to the README!

---
## Audited and Received Assessment Badge

[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/zinja-coder-apktool-mcp-server-badge.png)](https://mseep.ai/app/zinja-coder-apktool-mcp-server)

Thank you Mseep.net for auditing and providing Assessment Badge.
---

Built with ❤️ for the reverse engineering and AI communities.
