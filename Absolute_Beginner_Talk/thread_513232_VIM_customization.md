---
title: "VIM customization"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by n.aggel on 2007-07-30
hi, this is a thread for customization of vi...

firstly for anyone who wants to install gVim on ubuntu:

go to Systems->Administration-> Synaptic Package Manager-> search and install "vim-gnome" {with no quotes"

you can edit vim's properties by changing a file called vimrc located::: ~/vimrc

i post my vimrc file::

```

" lines with quotes are comments
set showcmd
"set guifont=Courier_New:h12:b:cGREEK
set incsearch
filetype plugin indent on
"colorscheme torte
set nu
set cindent
syntax on
set nocompatible
set cmdheight=3
source $VIMRUNTIME/vimrc_example.vim
source $VIMRUNTIME/mswin.vim
"behave mswin

set diffexpr=MyDiff()
function MyDiff()
  let opt = '-a --binary '
  if &diffopt =~ 'icase' | let opt = opt . '-i ' | endif
  if &diffopt =~ 'iwhite' | let opt = opt . '-b ' | endif
  let arg1 = v:fname_in
  if arg1 =~ ' ' | let arg1 = '"' . arg1 . '"' | endif
  let arg2 = v:fname_new
  if arg2 =~ ' ' | let arg2 = '"' . arg2 . '"' | endif
  let arg3 = v:fname_out
  if arg3 =~ ' ' | let arg3 = '"' . arg3 . '"' | endif
  let eq = ''
  if $VIMRUNTIME =~ ' '
    if &sh =~ '\<cmd'
      let cmd = '""' . $VIMRUNTIME . '\diff"'
      let eq = '"'
    else
      let cmd = substitute($VIMRUNTIME, ' ', '" ', '') . '\diff"'
    endif
  else
    let cmd = $VIMRUNTIME . '\diff'
  endif
  silent execute '!' . cmd . ' ' . opt . arg1 . ' ' . arg2 . ' > ' . arg3 . eq
endfunction

"some new settings!!!
set incsearch	"for incremental searching
	
	"for some smarter searching
set ignorecase
set smartcase

set scrolloff=4

	"completition mode
	"for more options check:::>> :help wildmode
set wildmode=longest,list

"set showmatch		"==== set sm 		
			"points out matching ( or { when closing ) or } 
 			" automatic matching braces
                        " set sm        ---> switch on brace matching
                        " set nosm      ---> switch off brace matching


	"enable folding!!!

set foldmethod=marker

	"set home path!!
"set path=/home/aggelidis/Programming/c++

"also some customizations...
set smarttab
set smartindent                 " Indent in smart fashion
set autoindent
set sm                          " automatic matching braces

set mouse=a                     " Use the mouse in all modes
set mousemodel=popup            " Turn on the popup menu
"set mousefocus                  " Use the mouse to focus windows
set mousehide                   " Hide the mouse cursor when the user types
set selectmode=mouse,key,cmd  " Use both mouse and shift keys to select

"----------------------
set dir=~/vi_swap              " swap directory

"------------------------
"Make Vim completion popup menu work just like in an IDE
set completeopt=longest,menuone


```

if anyone has a better vimrc file he may post it here....

{i use vi mainly for programming...}

---

### Post by n.aggel on 2007-07-30
does anyone know, how can i prevent vi from creating back up files each time, i edit one??

preferably i would also like to know, how can i make vi store a back up copy of every file i edit, in a paricular folder of my choice...{i.e. texts_backup}.........

---

### Post by asmoore82 on 2007-07-30
I love the power of vim but currently use it under ubuntu defaults ...

I find writing a multiline script in vim faster than using a for loop.

let's say i want to rename a bunch of mp3's to track numbers in ABC order ...

```
~ $ cd mp3
mp3 $ ls *.mp3 > run
mp3 $ vi run

:0,$s:^:mv -v 
:0,$s:$:\=" Track_" . line(".") . ".mp3"
:wq

mp3 $ . run
mp3 $ rm run
```

"vi users can move mountains with a few keystrokes at the cost of
not being able to accomplish anything in very few keystrokes."

true but the ability to
:0,.s:^:#
in config files is priceless

---

