# wikipedia-trends-mcp

[![Wikipedia Trends](https://img.shields.io/badge/Wikipedia%20Trends-636466?style=flat-square)](https://trendsmcp.ai/wikipedia-trends)
[![MCP](https://img.shields.io/badge/MCP-compatible-blue?style=flat-square)](https://modelcontextprotocol.io)
[![Works with Claude](https://img.shields.io/badge/Claude-supported-orange?style=flat-square)](https://trendsmcp.ai/mcp-server-for-claude)
[![Works with Cursor](https://img.shields.io/badge/Cursor-supported-purple?style=flat-square)](https://trendsmcp.ai/mcp-server-for-cursor)

> **Wikipedia page view trend data for AI**
> Wikipedia page views reveal what the world is suddenly curious about. Spike detection, historical page traffic, and cross-platform comparison - giving your AI a unique information-demand signal that precedes mainstream search.

**Full docs and live demo:** [https://trendsmcp.ai/wikipedia-trends](https://trendsmcp.ai/wikipedia-trends)

Part of **[Trends MCP](https://trendsmcp.ai)** - the MCP server for live trend data across 12+ sources.
See the main repo: [https://github.com/trendsmcp/trends-mcp](https://github.com/trendsmcp/trends-mcp)

---

## Get started in 2 steps

**Step 1:** Get your free API key at **[trendsmcp.ai](https://trendsmcp.ai)**
100 requests/day, no credit card required.

**Step 2:** Add to your AI client (replace `YOUR_API_KEY`):

[**+ Add to Cursor (one click)**](cursor://anysphere.cursor-deeplink/mcp/install?name=trends-mcp&config=eyJ1cmwiOiAiaHR0cHM6Ly9hcGkudHJlbmRzbWNwLmFpL21jcCIsICJ0cmFuc3BvcnQiOiAiaHR0cCJ9)

**Cursor / Windsurf / Cline** &nbsp; (`~/.cursor/mcp.json` or equivalent)
```json
{
  "mcpServers": {
    "trends-mcp": {
      "url": "https://api.trendsmcp.ai/mcp",
      "transport": "http",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**VS Code / GitHub Copilot** &nbsp; (`.vscode/mcp.json`)
```json
{
  "servers": {
    "trends-mcp": {
      "type": "http",
      "url": "https://api.trendsmcp.ai/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude Desktop** &nbsp; (`claude_desktop_config.json`)
```json
{
  "mcpServers": {
    "trends-mcp": {
      "url": "https://api.trendsmcp.ai/mcp",
      "transport": "http",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude.ai** (browser) &nbsp; Settings -> Connectors -> Add custom connector:
```
https://api.trendsmcp.ai/mcp
```

---

## Example query

After connecting, ask your AI:
```
get_trends(keyword='quantum computing', source='wikipedia', data_mode='weekly')
```

---

## Available tools

| Tool | What it does |
|------|-------------|
| `get_trends` | Time-series for a keyword on this source |
| `get_growth` | Growth % over 1W, 1M, 3M, 6M, 1Y periods |
| `get_top_trends` | What is trending right now on this source |
| `get_ranked_trends` | Top topics ranked by volume |

---

## FAQ

### What Wikipedia data does Trends MCP provide?

Wikipedia page view trends - normalized traffic to the Wikipedia article for a given topic over time. This is a strong information-demand signal: when something breaks in the news, Wikipedia views spike before Google Search catches up.

### How is Wikipedia data useful as a trend signal?

Wikipedia spikes often lead Google Trends by 24-72 hours for news-driven events. It is a leading indicator of public curiosity - useful for media, research, and investment applications.

### Does it track the English Wikipedia only?

Yes, currently English Wikipedia page views are tracked. Multi-language support is on the roadmap.

### Can I track a person, company, or event?

Yes. Any topic with a Wikipedia article can be tracked. Company pages, political figures, scientific concepts, and current events all work.

---

## All data sources

Trends MCP covers 12+ sources in one connection:
Google Search, YouTube, TikTok, Reddit, Amazon, Wikipedia,
News Sentiment, Web Traffic, App Downloads, Steam, npm, and more.

Browse all: [https://trendsmcp.ai/data-sources](https://trendsmcp.ai/data-sources)


---

## Also works as a Python client

Same API key works directly in Python - no MCP host needed.

```bash
pip install wikipedia-trends-mcp
```

```python
import os
from wikipedia_trends_mcp import TrendsMcpClient, SOURCE

client = TrendsMcpClient(api_key=os.environ["TRENDSMCP_API_KEY"])

series  = client.get_trends(source=SOURCE, keyword="your keyword")
growth  = client.get_growth(source=SOURCE, keyword="your keyword", percent_growth=["1M", "3M", "12M"])
top     = client.get_top_trends(type="Wikipedia", limit=10)
```

Full Python docs: [trendsmcp.ai/docs](https://trendsmcp.ai/docs)
---

## License

MIT &copy; [Trends MCP](https://trendsmcp.ai)