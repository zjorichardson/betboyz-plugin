# Bet Boyz — AI Agent Plugin

AI agent skill for the [Bet Boyz](https://betboyz.app) sports betting analytics API.

Give your AI agent the ability to track bets, detect cognitive biases, analyze performance across sportsbooks, and query live odds.

## What's in here

`SKILL.md` — A complete API reference designed for AI agents. Drop it into your agent's context and it knows how to use every endpoint.

## Supported capabilities

- **13 bet types** — moneyline, spread, total, parlay, same-game parlay, teaser, round robin, props, futures, live bets, if bets, reverses
- **Sportsbook accounts** — Track real and paper (simulated) accounts across 8 major books
- **Settlement** — Manually settle bets with per-leg outcomes
- **Analytics** — Summary stats, breakdowns by sport/type/book, win/loss streaks, time patterns
- **Bias detection** — Flags chasing losses, parlay-heavy betting, favorite bias, tilt
- **Live odds** — Sports, events, and odds from multiple bookmakers
- **Search** — Fuzzy team and player search via PostgreSQL trigram matching

## Quick start

### 1. Get an API key

```
POST https://api.betboyz.app/v1/customers/register
{ "email": "you@example.com", "password": "YourPassword1" }

POST https://api.betboyz.app/v1/customers/login
{ "email": "you@example.com", "password": "YourPassword1" }
# Returns session token

POST https://api.betboyz.app/v1/keys
Authorization: Bearer session_...
{ "name": "My Agent Key" }
# Returns API key — save it, shown only once
```

### 2. Give your agent the skill

**Claude Code:** Copy `SKILL.md` into your project's `.claude/skills/betboyz/` directory.

**Other agents:** Load the contents of `SKILL.md` into your agent's system prompt or tool context. Set these environment variables:

```
BETBOYZ_BASE_URL=https://api.betboyz.app
BETBOYZ_API_KEY=<your key from step 1>
```

### 3. Start using it

Your agent can now create sportsbook accounts, log bets, settle outcomes, run analytics, check for biases, and query live odds.

## API scopes

| Scope | Access |
|-------|--------|
| `bets:read` | List/get bets, team/player search |
| `bets:write` | Create, update, delete, settle bets |
| `analytics:read` | All analytics endpoints |
| `odds:read` | Sports, events, odds |
| `accounts:write` | Sportsbook account management |

Keys default to all scopes. Create scoped keys for least-privilege access.

## Rate limits

| Tier | Per Minute | Per Day |
|------|-----------|---------|
| trial | 30 | 500 |
| starter | 60 | 10,000 |
| growth | 120 | 100,000 |
| scale | 300 | 1,000,000 |

## Links

- **API:** https://api.betboyz.app
- **Website:** https://betboyz.app
- **Status:** https://stats.uptimerobot.com/00IhZCpGCn

## License

MIT
