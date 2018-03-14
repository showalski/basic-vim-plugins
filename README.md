# basic-vim-plugins
vim plugins that enhance your vim interface with extra sub-windows. It provides source code and project directory navigation and file searching. It looks like source insight. 3 plugins are used:
* Tag list
* NERDTree
* CtrIP

Below is the overview:

![Image of overview](https://github.com/showalski/basic-vim-plugins/blob/master/pics/overview.png)

## Installation
The installation is quite simple. Copy all files into your ~/.vim/ directory. If you don't want to install all of them, read following subsecionts. You might hit a few issues when using it. Don't worry. Below sub-sctions will show how to use each plugin and trouble-shoot some FAQs.

## Tag list
[Tag list](https://github.com/vim-scripts/taglist.vim) provides an overview of the structure, mainly global variables and functions, of source code files and allows you to efficiently browse through source code files for different programming languages. Below is a screenshot of Tag list.

![Image of tag list](https://github.com/showalski/basic-vim-plugins/blob/master/pics/taglist.png)
### Installation:
	1. Copy vim/plugin/taglist.vim to ~/.vim/plugin/taglist.vim.
	2. Copy vim/doc/taglist.txt to ~/.vim/doc/taglist.txt
### Configuration:
Copy below line to your `~/.vimrc`, which maps `F8` key to open tag list window.

`Set shortcut: nnoremap <silent> <F8> :TlistToggle<CR>`

Below line can adjust the width of taglist windown:

`let Tlist_WinWidth = somenumber`

### Usage:
	1. Press F8 to open or close Taglist window.
	2. p: Put crusor at a variable or function in Taglist window and press p then you will jump to its definition.
	3. Hit enter: Your cursor and source code window will move to its definition at the same time.
### Error1:
```
Taglist: Failed to generate tags for /users/foobar/.vim/plugin/taglist.vim
ctags: unrecognized option '--format=2'^@^ITry `ctags --help' for a complete list of options.^@
```

This error is caused by improperly setting of ctags. Setting correct ctags executable within .vimrc can solve it, like below:

`let Tlist_Ctags_Cmd="//bin/ctags-5.6`

### Error2:
```
E484: Can't open file /tmp/vUPw0po/0
```

This is caused by improperly setting of shell. Setting below variable to `.vimrc` can solve it:

`set shell=/bin/bash`

## NERDTree

The [NERD tree](https://github.com/scrooloose/nerdtree) allows you to explore your filesystem and to open files and directories. It presents the filesystem to you in the form of a tree which you manipulate with the keyboard and/or mouse. It also allows you to perform simple filesystem operations. Below is a screenshot of NERDTree:

![Image of tag NERDTree](https://github.com/showalski/basic-vim-plugins/blob/master/pics/nerdtree.png)

### Installation:
	1. Copy vim/plugin/NERD_tree.vim to ~/.vim/plugin/NERD_tree.vim
	2. Copy vim/doc/NERD_tree.txt to ~/.vim/doc/NERD_tree.txt
### Configuration:
Copy below lines to your `~/.vimrc`, which maps `F9` key to open NERDTree window.

```
" NERDTree
" Set the window width
let g:NERDTreeWinSize = 23
" Set the window position
let g:NERDTreeWinPos = "right"
" Auto centre
let g:NERDTreeAutoCenter = 0
" Not Highlight the cursor line
let g:NERDTreeHighlightCursorline = 0
" Map F9 to open or close NERDTree window
nnoremap <silent> <F9> : NERDTreeToggle<CR>
" After setting this i can open files form NERDTree window
set modifiable
```
### Usage:
	1. o:Open files, directories and bookmarks
	2. X:Recursively close all children of the current node
	3. C:Change the tree root to the selected dir
	4. go:Open selected file, but leave cursor in the NERDTree
	5. m and a: "m" brings up NERDTree filesystem menu and choose "a" for "add child node"
  
For more usage you can refer to help doc at " 2.3. NERD tree Mappings" by entering "help NERDTree" within VIM.

## CtrIP
[CtrIP](https://kien.github.io/ctrlp.vim/) is a finder for Vim:Full path fuzzy file, buffer, mru, tag, ... finder for Vim. When you open this plugin at first it will search all files(of cause, any specific files, like .a, .o or .exe, could be excluded by special configuration) of your workspace and create a buffer in memory for fast searching. You can search files with full name or regexp without closing Vim, open multiple files at once and open recently used files, etc. Below is a shortcut of CtrIP:

![Image of tag CtrIP](https://github.com/showalski/basic-vim-plugins/blob/master/pics/controlIP.png)

### Installation:
	1. Copy vim/bundle/ctrlp.vim/ and its subdirectories to ~/.vim/bundle/ctrlp.vim/
### Configuration:
	1. Add `set runtimepath^=~/.vim/bundle/ctrlp.vim` to your vimrc
	2. Enter this command `helptags ~/.vim/bundle/ctrlp.vim/doc` within Vim
	3. Set shortcut `let g:ctrlp_map = ',,'`. When you double hit comma CtrIP window will be opened.
	4. Set open command `let g:ctrlp_cmd = 'CtrlP' `
	5. Set the directory, which you run Vim, to CtrIP working directory: ` let g:ctrlp_working_path_mode = 'ra' `  
	6. If you don't want to limit the file number of CtrIP included you can use this ` let g:ctrlp_max_files=0 `
For other usage you can refer to this [link](https://kien.github.io/ctrlp.vim/).
