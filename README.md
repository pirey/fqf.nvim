# FQF.nvim - Fuzzy QuickFix

Enhanced quickfix and location list UI with fuzzy filtering for Neovim.

## Demo

<video src="fqf-demo.mp4" muted autoplay loop></video>

## Features

- **Fuzzy filtering** for quickfix/location lists with live filtering as you type
- **Intelligent formatting** - aligns file paths, line/column numbers, and messages
- **Split opens** - open items in vsplit, split, or new tab
- **Replaces `vim.ui.select`** - provides fuzzy filtering for picker UIs
- **Customizable keymaps** for both prompt and list views

## Installation

Using [lazy.nvim](https://github.com/folke/lazy.nvim):

```lua
{
  "pirey/fqf.nvim",
  event = "VeryLazy",
  config = function()
    local fqf = require("fqf")
    fqf.setup()
    vim.keymap.set("n", "<leader>f", fqf.builtins.files)
    vim.keymap.set("n", "<leader>p", fqf.builtins.smart_files)
    vim.keymap.set("n", "<leader>d", fqf.builtins.dirs)
    vim.keymap.set("n", "<leader>,", fqf.builtins.grep)
    vim.keymap.set("n", "<leader><leader>,", fqf.builtins.live_grep)
    vim.keymap.set("n", "<leader>'", fqf.builtins.oldfiles)
    vim.keymap.set("n", "<leader>gq", fqf.builtins.git_changes)
    vim.keymap.set("n", "<leader>/", fqf.builtins.buffer_lines)
  end,
},
```

## Keymaps

| Key | Action |
|-----|--------|
| `<cr>` | Open item |
| `<c-s>` | Open in split |
| `<c-v>` | Open in vsplit |
| `<c-t>` | Open in new tab |
| `<c-n>` | Next item |
| `<c-p>` | Previous item |
| `<c-q>` | Cancel |
| `<tab>` | Focus prompt/list |
| `<esc>` | Close |

## Configuration

```lua
require("fqf").setup({
  ui_select = { enabled = true },
  formatter = { enabled = true },
  prompt = {
    prefix = "> ",
    keymaps = {
      close = { "<esc>", "<c-c>" },
      focus_list = { "<tab>" },
      open = { "<cr>" },
      open_vsplit = { "<c-v>" },
      open_split = { "<c-s>" },
      open_tab = { "<c-t>" },
      up = { "<c-p>" },
      down = { "<c-n>" },
      cancel = { "<c-q>" },
    },
  },
  list = {
    keymaps = {
      cancel = { "<c-q>" },
      close = { "<esc>", "<c-c>" },
      focus_prompt = { "<tab>" },
      open = { "<cr>" },
      open_vsplit = { "<c-v>" },
      open_split = { "<c-s>" },
      open_tab = { "<c-t>" },
      up = { "<c-p>" },
      down = { "<c-n>" },
    },
  },
})
```
