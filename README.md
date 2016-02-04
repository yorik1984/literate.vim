# Literate.vim

This is a vim plugin for the [Literate] (https://github.com/zyedidia/Literate) programming system.

See the [Literate Manual](http://literate.zbyedidia.webfactional.com/manual.php#vim-plugin) for how to use it.

This plugin provides all sorts of niceties like syntax highlighting (it correctly syntax highlights the language embedded in code blocks using information from the @code_type), and keybindings to let you jump between code blocks. Also, if you have [Neomake]() installed then this plugin will report errors from inside vim. If you use the `@compiler` feature of Literate, this plugin will even report compiler errors from any compiler or linter (like gcc, pyflakes, jshint...).

When you first open a `.lit` file, vim will syntax highlight commands like `@code_type`, and `@title`... correctly, but it will not syntax highlight the embedded code blocks right away. This is because when you opened the empty file, the code type was not defined, so vim was unable to know what language you are using. You can execute :e to reload the syntax highlighting (make sure the file is saved) once you have defined the codetype with the `@code_type command`.

### Installation

To install, just use your favorite plugin manager:

Vundle:
```vimL
Plugin 'zyedidia/literate.vim'
```

### Mappings

Literate.vim has three mappings:

* `<C-]>` lets you jump to a code block definition from a code block use and back. If your cursor is on `@{block name}` and you press `<C-]>`, your cursor will jump to the next use/definition and vice versa.
* `<leader>c` will use `lit` (make sure it's in your `PATH`) to compile only the code for the current file and open it in a new window. Just make sure that the output file has the same basename as the lit file (and the `@code_type` is defined).
* `<leader>h` will use `lit` to compile only html and run `open` on it to open in a web browser.

These are just default mappings and can be remapped in your `.vimrc`:

```vimL
let g:literate_find_codeblock = "<C-]>"
let g:literate_open_code = "<leader>c"
let g:literate_open_html = "<leader>h"
```
