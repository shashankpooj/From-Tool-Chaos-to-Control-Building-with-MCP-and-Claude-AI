# From-Tool-Chaos-to-Control-Building-with-MCP-and-Claude-AI

Absolutely! Here's the **entire README content in plain text format**, so you can **copy-paste it directly** into your `README.md` file on GitHub — no markdown syntax formatting required if you don’t want it.

---

**Claude + MCP Integration**

This project demonstrates how to connect Claude AI (Anthropic LLM) to external tools (like web search) using a smart middleware layer called MCP (Model Context Protocol).

Instead of hardcoding tool logic into your LLM or application, this setup uses a local MCP server to handle tool calls modularly and efficiently.

---

**What is MCP?**

MCP (Model Context Protocol) acts as a smart controller between your LLM (like Claude) and multiple tools. When Claude identifies the need for a tool (e.g., web search), it triggers a tool call. MCP receives that call, determines which tool is needed, executes it, and returns the result back to Claude.

Benefits of MCP:

* Cleaner separation of tool logic from LLM
* Easier to scale, debug, and extend tools
* Centralized error handling and retry logic

---

**Project Structure**

ask\_claude.py — Main script to ask Claude a query via CLI
claude\_mcp\_client.py — Claude client that sends messages and handles tool use
mcp\_integration.py — Tool call logic using Claude and DuckDuckGo
mcp\_server.py — Flask server acting as the MCP server
requirements.txt — Python dependencies
README.md — This file

---

**Setup Instructions**

1. Clone the repo

```
git clone https://github.com/your-username/claude-mcp-integration.git
cd claude-mcp-integration
```

2. (Optional) Create a virtual environment

```
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
```

3. Install dependencies

```
pip install -r requirements.txt
```

4. Set environment variables

You’ll need your Anthropic Claude API Key.

Linux/macOS:

```
export CLAUDE_API_KEY=your_claude_api_key
export MCP_SERVER_URL=http://localhost:5001
```

Windows PowerShell:

```
$env:CLAUDE_API_KEY="your_claude_api_key"
$env:MCP_SERVER_URL="http://localhost:5001"
```

---

**How to Use**

Step 1: Start the MCP server

```
python mcp_server.py
```

Step 2: Ask Claude a question from the command line

```
python ask_claude.py "What is Python programming?"
```

Claude will:

* Understand your query
* Trigger a tool call to the MCP server (if needed)
* MCP will select and run the correct tool (like DuckDuckGo)
* Return the result back to Claude for a final response

---

**Adding New Tools**

To add more tools:

* Add them to the `tools` list in `ClaudeClient`
* Implement the logic in `mcp_integration.py`
* Route them in the `/tool_call` endpoint of `mcp_server.py`

The architecture is modular and easy to extend.

---

**Requirements**

* Python 3.8+
* Libraries:

  * requests
  * flask
  * openai
  * anthropic
  * dataclasses

---

**Example Use Cases**

* Let LLMs fetch real-time information from the web
* Create AI agents with flexible tool selection
* Build scalable interfaces between AI and APIs
* Extend Claude’s intelligence with custom modules

---

**Contact**

Feel free to open issues or connect if you're working on a similar project or want to extend this one!

---

**License**

MIT License — free to use, modify, and share.

---

Let me know if you’d like to turn this into a visual walkthrough or architecture diagram as well!
