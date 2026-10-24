# Speak To Your Database (STYD)

**Ask your Odoo, PostgreSQL or MySQL data in plain words, from the AI app you already use. Real numbers, computed read-only from your data.**

[![Speak To Your Database MCP connector](https://glama.ai/mcp/connectors/com.speaktoyourdatabase/styd/badges/score.svg)](https://glama.ai/mcp/connectors/com.speaktoyourdatabase/styd)

STYD is a hosted MCP server. Connect it once to Claude, ChatGPT, Le Chat, VS Code or any app that supports remote MCP servers, then ask things like:

- "How much revenue did we make last month, compared with the month before?"
- "Which customer invoices are overdue, and how much does each customer owe?"
- "Show all sales orders grouped by customer and status, with the number of orders, the total amount and the date range."
- "Top 10 products by sales this year"
- "Why did sales drop this month?"

Follow-ups work too: after the sales orders question, ask *"and only the confirmed ones?"* and STYD keeps the same grouping.

STYD works out the answer from your data and sends back the numbers, with the period and the definition it used (for example, *revenue = posted customer invoices, excluding tax*).

- Website: https://speaktoyourdatabase.com
- MCP endpoint: `https://speaktoyourdatabase.com/mcp`
- Demo video: https://www.youtube.com/watch?v=PZffAbynuc0
- Docs: https://speaktoyourdatabase.com/docs/mcp

> This repository holds the public setup guide and the registry file. STYD itself is a hosted service; its source code is not public.

---

## Try it in 2 minutes

1. Add the connector to your AI app (see below).
2. Sign in to STYD when your app asks. The free plan includes sample data, so you can ask questions straight away.
3. When you are ready, connect your own Odoo, PostgreSQL or MySQL database at https://speaktoyourdatabase.com/connections.

## Set up in your AI app

### Claude (web, desktop, mobile)

Open **Settings → Connectors**, search the directory for **Speak To Your Database**, and click **Connect**.
Directory page: https://claude.ai/directory/speak-to-your-database

### Claude Code

```bash
claude mcp add --transport http styd https://speaktoyourdatabase.com/mcp
```

Then run `/mcp` in Claude Code and sign in.

### VS Code (GitHub Copilot)

Run **MCP: Add Server** from the Command Palette, choose **HTTP**, and paste `https://speaktoyourdatabase.com/mcp`. Or add this to `.vscode/mcp.json`:

```json
{
  "servers": {
    "styd": {
      "type": "http",
      "url": "https://speaktoyourdatabase.com/mcp"
    }
  }
}
```

Start the server, sign in when VS Code asks, then use Copilot Chat in **Agent** mode.

### Le Chat (Mistral)

Add a custom MCP connector with the URL `https://speaktoyourdatabase.com/mcp`, then sign in to STYD when asked.

### ChatGPT

Open **Plugins** in ChatGPT, search for **Speak To Your Database**, and click **Install plugin**. Sign in to STYD when asked.
Plugin page: CHATGPT_LINK

### Cursor and other apps

Any app that supports remote MCP servers with OAuth sign-in can use `https://speaktoyourdatabase.com/mcp`. For Cursor and apps without sign-in support, use a workspace API key: see https://speaktoyourdatabase.com/docs/mcp/other-apps.

## Tools

| Tool | What it does |
| --- | --- |
| `list_workspaces` | Lists the STYD workspaces (companies) you belong to |
| `list_connections` | Lists the data sources in a workspace: Odoo, PostgreSQL, MySQL, sample data |
| `describe_available_data` | Shows what a connection can answer, with example questions |
| `ask_question` | Asks one business question and returns the answer computed from your data |
| `get_answer` | Fetches the result of a longer-running question |

Every answer names the workspace it comes from, so data from different companies is never mixed.

## Security

STYD reads your data; it never changes it.

- **Read-only:** STYD cannot create, change or delete anything in Odoo or your databases.
- **Secrets protected:** database passwords and API keys are stored encrypted and never shown back.
- **Standard sign-in:** AI apps connect through OAuth. You approve each app on a STYD consent page, and you can revoke it at any time.
- **Uploaded files checked** with a malware scan before use.
- **Backups** with an encrypted off-site copy.
- **Abuse protection** and rate limits.
- **Not used for training:** your data and questions are not used to train AI models.

Details: https://speaktoyourdatabase.com/security and https://speaktoyourdatabase.com/privacy

Need STYD on your own server, with nothing leaving your network? See https://speaktoyourdatabase.com/private.

## Registry

STYD is published in the official MCP Registry as `com.speaktoyourdatabase/styd`. The [`server.json`](server.json) in this repository is the registry entry.

Also listed in the [ChatGPT plugin directory](CHATGPT_LINK), the [Claude connectors directory](https://claude.ai/directory/speak-to-your-database) and on [Glama](https://glama.ai/mcp/connectors/com.speaktoyourdatabase/styd).

## Support

Questions, a source you would like supported, or something that did not work: https://speaktoyourdatabase.com/support, or open an issue in this repository.

Built by [Florian Assous](https://www.linkedin.com/in/florian-assous/).