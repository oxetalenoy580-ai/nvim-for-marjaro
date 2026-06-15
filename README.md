# nvim

Modern Neovim configuration with built-in `vim.pack.add`, Catppuccin Mocha, and full LSP/formatting support.

## Structure

```
init.lua          # Entry point, plugin declarations
lua/
├── core/         # Options, keymaps, autocmds, terminal, neovide
├── lsp/          # lspconfig (LSP + cmp + efm), jdtls
├── plugins/      # nvim-tree, treesitter, fzf-lua, gitsigns, mini.nvim, mason, obsidian, venv-selector
└── ui/           # colorscheme (transparent), statusline
```

## Plugins

- **Colorscheme**: [catppuccin/nvim](https://github.com/catppuccin/nvim)
- **File explorer**: [nvim-tree/nvim-tree.lua](https://github.com/nvim-tree/nvim-tree.lua)
- **Fuzzy finder**: [ibhagwan/fzf-lua](https://github.com/ibhagwan/fzf-lua)
- **Statusline**: Custom (focus-aware, Nerd Font icons)
- **Terminal**: Floating toggle (`<C-\>`)
- **Git**: [lewis6991/gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim)
- **Editor suite**: [echasnovski/mini.nvim](https://github.com/echasnovski/mini.nvim) (ai, comment, surround, move, pairs, etc.)
- **Syntax**: [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
- **Completion**: [nvim-cmp](https://github.com/hrsh7th/nvim-cmp) + LuaSnip + friendly-snippets
- **LSP**: 7 servers (lua_ls, pyright, bashls, ts_ls, gopls, clangd, jdtls) + efm for formatting/linting
- **Formatter/Linter**: [efmls-configs-nvim](https://github.com/creativenull/efmls-configs-nvim) via Mason
- **Notes**: [obsidian.nvim](https://github.com/obsidian-nvim/obsidian.nvim) (optional)
- **Python venv**: [venv-selector.nvim](https://github.com/linux-cultist/venv-selector.nvim) (optional)

## Keymaps

Leader key is `<Space>`.

### Navigation & Motion

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `j` / `k` | `n` | Wrap-aware line movement (`gj`/`gk`) |
| `H` / `L` | `n,v` | Move to start/end of line (`^` / `$`) |
| `n` / `N` | `n` | Next/prev search result (centered) |
| `<C-d>` / `<C-u>` | `n` | Half page down/up (centered) |
| `<C-h>` / `<C-j>` / `<C-k>` / `<C-l>` | `n` | Navigate windows left/down/up/right |
| `<C-Up>` / `<C-Down>` | `n` | Resize window height ±2 |
| `<C-Left>` / `<C-Right>` | `n` | Resize window width ±2 |

### Buffer & Window Management

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<leader>bn` | `n` | Next buffer |
| `<leader>bp` | `n` | Previous buffer |
| `<leader>sv` | `n` | Vertical split |
| `<leader>sh` | `n` | Horizontal split |

### File Explorer

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<leader>e` | `n` | Open parent directory (oil.nvim) |

### Fuzzy Finding (fzf-lua)

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<leader>ff` | `n` | Find files |
| `<leader>fg` | `n` | Live grep |
| `<leader>fb` | `n` | Switch buffer |
| `<leader>fh` | `n` | Help tags |
| `<leader>fx` | `n` | Document diagnostics |
| `<leader>fX` | `n` | Workspace diagnostics |
| `<leader>fd` | `n` | LSP definitions |
| `<leader>fr` | `n` | LSP references |
| `<leader>ft` | `n` | LSP type definitions |
| `<leader>fs` | `n` | Document symbols |
| `<leader>fw` | `n` | Workspace symbols |
| `<leader>fi` | `n` | LSP implementations |

### LSP

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `K` | `n` | Hover documentation |
| `<leader>gd` | `n` | Go to definition |
| `<leader>gD` | `n` | Go to definition (vsplit) |
| `<leader>ca` | `n` | Code action |
| `<leader>rn` | `n` | Rename symbol |
| `<leader>D` | `n` | Line diagnostics |
| `<leader>d` | `n` | Cursor diagnostics |
| `<leader>nd` | `n` | Next diagnostic |
| `<leader>pd` | `n` | Previous diagnostic |
| `<leader>oi` | `n` | Organize imports & format |
| `<leader>q` | `n` | Open diagnostic list (loclist) |
| `<leader>dl` | `n` | Show line diagnostics float |

### Completion (nvim-cmp)

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<C-Space>` | `i` | Trigger completion |
| `<C-j>` / `<C-k>` | `i` | Select next/prev item |
| `<CR>` | `i,c` | Confirm selection |
| `<Tab>` / `<S-Tab>` | `i,s,c` | Smart navigation / fallback |

### Git (gitsigns)

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `]h` / `[h` | `n` | Next/prev git hunk |
| `<leader>hs` | `n` | Stage hunk |
| `<leader>hr` | `n` | Reset hunk |
| `<leader>hp` | `n` | Preview hunk |
| `<leader>hb` | `n` | Blame line |
| `<leader>hB` | `n` | Toggle inline blame |
| `<leader>hd` | `n` | Diff this |

### Editing

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `jk` / `kj` | `i` | Exit insert mode |
| `<leader>p` | `x` | Paste without yanking |
| `x` | `n,v` | Delete char (no register) |
| `xx` | `n` | Delete line (no register) |
| `<A-j>` / `<A-k>` | `n` | Move line down/up |
| `<A-j>` / `<A-k>` | `v` | Move selection down/up |
| `<` / `>` | `v` | Indent and reselect |
| `J` | `n` | Join lines (preserve cursor) |
| `<leader>pa` | `n` | Copy full file path |
| `<leader>c` | `n` | Clear search highlights |
| `<leader>td` | `n` | Toggle diagnostics |

### Multiple Cursors

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<leader>m` | `n,v` | Toggle / match cursors |
| `<Esc>` | `n` | Clear multi-cursors |

### Terminal

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<C-\>` | `n,t` | Toggle floating terminal |

### OpenCode AI

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<leader>oa` | `n` | Ask about current buffer |
| `<leader>oa` | `v` | Ask about visual selection |
| `<leader>of` | `n` | Fix |
| `<leader>of` | `v` | Fix selection |

### Obsidian Notes

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<leader>nn` | `n` | New note |
| `<leader>nf` | `n` | Find note |
| `<leader>ns` | `n` | Search notes |
| `<leader>nt` | `n` | Today's daily note |
| `<leader>nw` | `n` | Switch workspace |

### Python

| Keys | Mode | Action |
| ---- | ---- | ------ |
| `<leader>cv` | `n` | Select Python virtual env |

## Format on save

Enabled for: lua, python, go, js/ts/jsx/tsx, json, css/scss, html, sh, c/cpp via efm.

## Requirements

- Neovim >= 0.10 (for `vim.pack.add`)
- Nerd Font (for icons)
- [Mason](https://github.com/mason-org/mason.nvim) for installing LSP/formatter/linter binaries
