# Steam Skill for AI Agents

Use SteamWebAPI in Codex, Claude Code, Cursor and other agents that support
Agent Skills. Find endpoints and read live schemas for Steam inventories,
profiles, prices, item catalogs and CS2 skin images.

SteamWebAPI is an independent service with its own endpoints, API keys and
plans. SteamWebAPI is not affiliated with Valve.

[Steam Skill overview and examples](https://www.steamwebapi.com/steam-skill)

## Install the skill

```sh
npx skills add steamwebapi/steam-skill --skill steam-api
```

The installer asks which agents to set up. Run `npx skills update` to get newer
versions. To install by hand, save [SKILL.md](skills/steam-api/SKILL.md) as
`steam-api/SKILL.md` in your agent's skills directory.

If you installed the standalone skill under its old `steamwebapi` name, install
`steam-api`, then run `npx skills remove steamwebapi` using the same project or
global scope as your old installation.

Try asking:

> Use the Steam API skill to build a CS2 inventory valuation endpoint. Check the
> live schema and explain how missing prices should be handled.

## Install the Claude Code plugin

The Claude Code plugin bundles the same skill and the hosted MCP connection.

```text
/plugin marketplace add steamwebapi/steam-skill
/plugin install steamwebapi@steamwebapi
```

Run `/steamwebapi:steam-api` to open the skill. The previous
`/steamwebapi:steamwebapi` command opens the same instructions. Existing plugin
users can refresh the marketplace and update `steamwebapi@steamwebapi`.

Claude clients that support custom plugin uploads can use
`steamwebapi-claude.zip`. To load the extracted plugin locally in Claude Code,
run `claude --plugin-dir /absolute/path/to/steamwebapi`.

## Connect MCP

The skill can use the [public OpenAPI specification](https://www.steamwebapi.com/api/doc.json)
directly. To enable endpoint discovery inside your agent, configure the hosted
Streamable HTTP MCP server.

```text
https://mcp.steamwebapi.com/mcp
```

Endpoint documentation and discovery are public. Eligible live read-only
requests require your SteamWebAPI key and sufficient access and quota. Configure
the key in private client settings with the `X-Api-Key` header, or keep it in
server-side configuration for your own application.

[Client setup and examples](https://www.steamwebapi.com/mcp) · [SteamWebAPI documentation](https://www.steamwebapi.com/api/steam/documentation)
