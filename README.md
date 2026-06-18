# Book Editor — a writing coach toolkit

Two paired skills that work as a book editor and writing coach for memoir,
narrative non-fiction, and literary fiction. Draft freely and ignore grammar; the
editor shapes the raw material, removes AI tells, and teaches you *why* as it goes.

## The two skills

### `book-editor/`
A full editor that works the way a professional does: it **assesses the
manuscript first**, then edits in staged passes from big to small —
developmental (structure, pacing, arc), line editing (flow, rhythm, redundancy,
reader engagement), a voice pass, copyediting, and proofreading. It auto-fixes
obvious mechanical errors and proposes everything substantive for approval, and
it works **alongside you as a coach**, explaining the principle behind each change.

Grounded in the craft canon: Browne & King (*Self-Editing for Fiction Writers*),
Joseph Williams (*Style*), Le Guin (*Steering the Craft*), Stephen King (*On
Writing*), Strunk & White, McPhee (*Draft No. 4*), and Saunders.

Includes:
- `scripts/prose_stats.py` — objective rhythm/redundancy/readability stats.
- `scripts/check_tells.py` — bundled mechanical AI-tell sweep.
- `reference/` — developmental, line-editing, copyedit/proof, and craft-canon guides.

### `humanizer/`
The voice specialist. Works **voice-first**: establish the author's voice, then
strip AI tells (em dashes, reflective-summary endings, telling-not-showing, stock
fiction clichés, course-outcome boilerplate) while protecting the voice. Includes
an **enforced checker** that hard-blocks delivery while em dashes or curly quotes
remain, plus a voice-discovery mode for new authors.

Includes:
- `scripts/check_tells.py` — the enforced sweep (hard-fails on dashes/curly quotes).
- `reference/patterns.md` — the full AI-tell catalogue.
- `reference/voice-discovery.md` — the new-author voice interview.

The `book-editor` runs the `humanizer` as its voice pass, so they're designed to
work together.

## How they work in a session
1. **Assess** — the editor reads the whole piece and tells you where it is and what
   it needs (a rough draft needs developmental work, not proofreading).
2. **Stage the passes** — biggest structural questions first, smallest commas last.
3. **Propose, don't impose** — substantive changes come with before/after; only
   clear mechanical errors are auto-fixed.
4. **Coach** — every change comes with the *why*, so you become a stronger
   self-editor over time.

## Installing

### Claude Code — plugin marketplace (recommended)
This repo is a Claude Code [plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces).
Add it once, then install either plugin:

```text
/plugin marketplace add nuwrldnf8r/book_editor_skill
/plugin install book-editor@book-editor-skill
```

`book-editor` lists `humanizer` as a dependency, so installing it pulls the
humanizer in automatically. To install the voice pass on its own:

```text
/plugin install humanizer@book-editor-skill
```

Update later with `/plugin marketplace update book-editor-skill`, and manage what's
installed from the `/plugin` menu. You can also add the marketplace from a full URL
(`/plugin marketplace add https://github.com/nuwrldnf8r/book_editor_skill`) or a
local clone (`/plugin marketplace add ./book_editor_skill`).

### Claude Desktop / Cowork — manual
- **Settings → Capabilities → add a skill**, and point it at each skill folder
  (`book-editor/` and `humanizer/`) or its packaged `.skill` file.

Either way, the skills are self-contained Markdown + small Python scripts; no
dependencies beyond Python 3.

## Using the scripts directly
```bash
python3 humanizer/scripts/check_tells.py path/to/draft.md      # enforced AI-tell sweep
python3 book-editor/scripts/prose_stats.py path/to/draft.md    # rhythm & redundancy stats
```

## License
MIT — see [LICENSE](LICENSE).
