# KeyboardNavigation
Keyboard movement and selection and deletion to custom delimeters. Navigate fast between contiguous boundaries. For SublimeText.

## Package Installation
* Manual method: Download ZIP from github. Extract the files to [Sublime_Data_Dir](http://docs.sublimetext.info/en/latest/basic_concepts.html#the-data-directory)\Packages\KeyboardNavigation
* Automatic method: Install 'KeyboardNavigation' from [Package Control](http://packagecontrol.io).

## Key Bindings
Sample Keybindings:
* <kbd>ctrl+left</kbd> move cursor to beginning of next contiguous boundary demarcated by a whitespace
* <kbd>ctrl+right</kbd> move cursor to beginning of previous contiguous boundary demarcated by a whitespace
* <kbd>alt+left</kbd> move cursor to beginning of previous subword boundary delineated by ", ., +, _, <, >, [, ], {, }, -, (, )
* <kbd>alt+right</kbd> move cursor to beginning of next subword boundary delineated by ", ., +, _, <, >, [, ], {, }, -, (, )
* <kbd>ctrl+shift+left</kbd> select to beginning of next contiguous boundary demarcated by a whitespace
* <kbd>ctrl+shift+right</kbd> select to beginning of previous contiguous boundary demarcated by a whitespace
* <kbd>alt+shift+left</kbd> select to beginning of previous subword boundary delineated by ", ., +, _, <, >, [, ], {, }, -, (, )
* <kbd>alt+shift+right</kbd> select to beginning of next subword boundary delineated by ", ., +, _, <, >, [, ], {, }, -, (, )
* <kbd>ctrl+shift+w</kbd> expand_selection_to_whitespace - expand selection to whitespace
* <kbd>ctrl+shift+e</kbd> expand_selection_to_delims - expand selection to (space), (tab), (newline), ", ', %, @, &, :, (period), (comma), +, _, -, <, >, (, ), [, ], {, }, |, \
* <kbd>ctrl+shift+q</kbd> expand_selection_to_quotes - expand selection to ", '
* <kbd>ctrl+shift+b</kbd> expand_selection_to_brackets - expand selection to (, ), <, >, [, ], {, }
* <kbd>home</kbd> move cursor to beginning of line (this one goes all the way to the beginning whereas the native one goes to the beginning of indentation)
* <kbd>end</kbd> move cursor to end of line
* <kbd>ctrl+alt+-</kbd> indent less (to the left)
* <kbd>ctrl+alt+=</kbd> indent more (to the right) (even works with blank line which the native one does not)
* <kbd>ctrl+backspace</kbd> delete(backspace) to previous contiguous boundary demarcated by a whitespace
* <kbd>ctrl+delete</kbd> delete to next contiguous boundary demarcated by a whitespace

Other Miscellaneous Keybindings (some are duplicates of innate functionality):
* <kbd>ctrl+alt+l</kbd> select line without linebreak
* <kbd>ctrl+alt+shift+l</kbd> select line with linebreak
* <kbd>ctrl+alt+d</kbd> delete line without linebreak
* <kbd>ctrl+alt+shift+d</kbd> delete line with linebreak

Since these are redefining / replacing your very basic navigational keys, the package does not automatically overwrite your existing key bindings. You must choose to add the keybindings yourself specific to your OS.

For Windows, you can use the recommended sample keybindings by adding the following lines to [Sublime_Data_Dir]\User\Default (Windows).sublime-keymap
```
{ "keys": ["ctrl+left"], "command": "move_to_beg_of_contig_boundary", "args": {"forward": false} },
{ "keys": ["ctrl+right"], "command": "move_to_beg_of_contig_boundary", "args": {"forward": true} },

{ "keys": ["alt+left"], "command": "move_to_beg_of_subword_boundary", "args": {"forward": false} },
{ "keys": ["alt+right"], "command": "move_to_beg_of_subword_boundary", "args": {"forward": true} },

{ "keys": ["ctrl+shift+left"], "command": "select_to_beg_of_contig_boundary", "args": {"forward": false} },
{ "keys": ["ctrl+shift+right"], "command": "select_to_beg_of_contig_boundary", "args": {"forward": true} },

{ "keys": ["alt+shift+left"], "command": select_to_beg_of_subword_boundary "args": {"forward": false} },
{ "keys": ["alt+shift+right"], "command": "select_to_beg_of_subword_boundary", "args": {"forward": true} },

{ "keys": ["ctrl+shift+w"], "command": "expand_selection_to_whitespace" },
{ "keys": ["ctrl+shift+e"], "command": "expand_selection_to_delims" },
{ "keys": ["ctrl+shift+q"], "command": "expand_selection_to_quotes"},
{ "keys": ["ctrl+shift+b"], "command": "expand_selection_to_brackets"},
{ "keys": ["ctrl+shift+l"], "command": "expand_selection", "args": {"to": "line"} },

{ "keys": ["home"], "command": "homeendbeginning", "args": {"forward": false} },
{ "keys": ["end"], "command": "homeendbeginning", "args": {"forward": true} },

{ "keys": ["ctrl+alt+-"], "command": "indentblankline", "args": {"forward": false} },
{ "keys": ["ctrl+alt+="], "command": "indentblankline", "args": {"forward": true} }

{ "keys": ["ctrl+backspace"], "command": "delete_to_beg_of_contig_boundary", "args": {"forward": false} },
{ "keys": ["ctrl+delete"], "command": "delete_to_beg_of_contig_boundary", "args": {"forward": true} },

{ "keys": ["ctrl+alt+l"], "command": select_line_wo_linebreak },
{ "keys": ["ctrl+alt+shift+l"], "command": "select_line" },
{ "keys": ["ctrl+alt+d"], "command": "delete_line_wo_linebreak" },
{ "keys": ["ctrl+alt+shift+d"], "command": "delete_line" },
```
## how this compares with vim
For a paradigm of where this is implemented in vim -  
[https://docs.oracle.com/cd/E19683-01/806-7612/6jgfmsvqf/index.html](https://docs.oracle.com/cd/E19683-01/806-7612/6jgfmsvqf/index.html)  
[https://stackoverflow.com/questions/22931032/vim-word-vs-word](https://stackoverflow.com/questions/22931032/vim-word-vs-word)  
[https://www.computerhope.com/unix/vim.htm](https://www.computerhope.com/unix/vim.htm) - "Moving From Word To Word"  
[https://vim.rtorr.com/](https://vim.rtorr.com/)  
[https://forum.sublimetext.com/t/change-cursor-position-at-beginning-of-next-word-when-moving/21474](https://forum.sublimetext.com/t/change-cursor-position-at-beginning-of-next-word-when-moving/21474)
```
Press�w (�word�) to move the cursor to the right one word at a time.
Press�b�(�back�) to move the cursor to the left one word at a time.
```
I found that Sublime's move "words" and "words_ends" keybindings of vim's "b" and "w" emulation mode still stop at punctuation characters even if you make "word_separators" blank.

KeyboardNavigation allows vim "w" and "b" like movement fastly through contiguous boundaries.
