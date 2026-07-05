# Content Creator Skills

Claude Code Skills for automated content creation pipelines.

---

## Skills

### `tech-blog-writer`

A bilingual (Chinese + English) technical blog writing pipeline powered by Claude Code.

**Triggers:** "写一篇文章" / "帮我写博客" / "选个话题写" / "我想写关于 X 的文章"

**What it does:**

1. Searches Chinese internet trends (Zhihu, Xiaohongshu, Bilibili, Sspai) to find current topics
2. Proposes 3 angles — auto-selects the recommended one unless you specify
3. Generates a bilingual draft: Chinese article (1200–2000 字) + independent English version (800–1500 words)
4. Fetches a cover image from Unsplash automatically
5. Generates a Chinese infographic (HTML, responsive, dark/light mode)
6. Review loop — revise until you're satisfied
7. Builds and deploys with safety checks before every push

**Safety features:**
- Verifies `scripts/config.json` is in `.gitignore` before deploying (prevents accidental API key leak)
- Shows `git status` diff for confirmation before pushing
- Stages only `content/` — never blindly runs `git add -A`

---

## Installation

### Prerequisites

- [Claude Code](https://claude.ai/code) installed
- Node.js 18+
- A blog repo with `scripts/build-blog.js` and `npm run deploy` configured
- An [Unsplash Developer](https://unsplash.com/developers) account (free)

### Install a skill

In Claude Code, run:

```
/install-skill https://github.com/x-tian-lab/content-creater-skills
```

Or install a specific skill file directly via the Claude Code UI.

### Configure your blog repo

**1. Add to `.gitignore`** (your blog repo, not this one):

```
scripts/config.json
```

**2. Create `scripts/config.json`** in your blog repo:

```json
{ "unsplash_access_key": "YOUR_UNSPLASH_ACCESS_KEY" }
```

Get your key at [unsplash.com/developers](https://unsplash.com/developers) → Your apps → New Application → Access Key.

**3. Tell Claude Code your repo path** the first time you use the skill — it will ask automatically.

---

## Repo structure

```
content-creater-skills/
└── tech-blog-writer-v5.skill   # Bilingual blog writing pipeline
```

---

## License

MIT
