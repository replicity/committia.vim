More Pleasant Editing on Commit Message
=======================================

When you type `git commit`, Vim starts and opens a commit buffer.  This plugin improves
the commit buffer.

Split the buffer to 3 windows; edit window, status window and diff window.  You no longer
need to repeat scroll and back to former position in order to see long commit diff.
If the width of Vim window is too narrow (160 characters by default), committia opens
normal commit buffer.

![screen shot](https://dl.dropboxusercontent.com/u/2753138/screenshot_committia.jpg)

## Hooks

You can hook on opening the windows.
A vimrc example is below.

```vim
let g:committia_hooks = {}
function! g:committia_hooks.edit_open()
    setlocal spell

    " If there is already no message, start with insert mode
    " You can get the information about windows with 'self' dictionary
    "
    "   self.vcs            : vcs type (e.g. 'git')
    "   self.edit_winnr     : winnr of edit window
    "   self.edit_bufnr     : bufnr of edit window
    "   self.diff_winnr     : winnr of diff window
    "   self.diff_bufnr     : bufnr of diff window
    "   self.status_winnr   : winnr of status window
    "   self.status_bufnr   : bufnr of status window

    if getline(1) ==# ''
        startinsert
    end
endfunction
```

## Future

- Scroll diff window from insert mode in edit window.
- Cooperate with [vim-fugitive](https://github.com/tpope/vim-fugitive).
- Add more hooks.
- More VCS supports

## License

    Copyright (c) 2014 rhysd

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
    of the Software, and to permit persons to whom the Software is furnished to do so,
    subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
    INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
    PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
    LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
    TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR
    THE USE OR OTHER DEALINGS IN THE SOFTWARE.