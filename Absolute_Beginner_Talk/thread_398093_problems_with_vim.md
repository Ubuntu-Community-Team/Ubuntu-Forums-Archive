---
title: "problems with vim"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by gil michael on 2007-03-31
hi,

i have 2 problems with vim:

1. when i enter the command   :syntax
the next error pops up: E319: Sorry, the command is not available in this version

how do i download/install a better version?

2. when i type and press enter at the end of a line the cursor goes to the BEGINNING of the next line. i don't want it to go to the beginning because i write code in blocks, and not all blocks start at the beginning. i want it to go to the next line, but to the same place that the previous line starts. 

how do i do that?

thanks,

Gil

---

### Post by taurus on 2007-03-31
```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by djrosen on 2007-03-31
You dont say what version you are using but I can tell you that I am using the version of vi that comes with dapper and  it works just as you describe. TAB type some stuff and hit enter and I am under that block of text, tab again, type and enter and I am under the new block, not the beginning and :synatx returns "No Syntax items defined for this buffer"

So, what version of vi[m] / Ubuntu are you using?

---

### Post by x1a4 on 2007-03-31
it's supposed to be 

*:syntax **on***

to enable syntax highlighting, 

or

*:set syntax=<syntax>*

eg:
*:set syntax=vim*

to enable highlighting for specific syntax.  In the above example it's for a vim (rc and syntax) file.  

To enable syntax highlighting by default, add this to your _~/.vimrc_

**syntax on**

and this 

**set autoindent**

to enable automatic indenting.  

Visit [dotfiles.com](http://www.dotfiles.com/) for good examples of .vimrc files, and read the vim man page for details.  If you installed *vim-doc* you should also have comprehensive documentation at file:///usr/share/doc/vim-doc/doc/html/index.html
Also checkout vim's global rc file: _/etc/vim/vimrc_

This is my ~/.vimrc 

```

"~/.vimrc

if filereadable("/etc/vim/vimrc")
	source /etc/vim/vimrc
endif

set nocompatible
set backspace=indent,eol,start
if has("vms")
	set nobackup
else
	set backup
endif
set ffs=unix,mac,dos
set viminfo+=! " ensure it can save viminfo
set isk+=_,$,@,%,#,-,?,%,& " none of these should be word dividers, so make them not be
set lz " do not redraw while running macros (much faster) (LazyRedraw)
set history=50
set shortmess=at
set ruler
set rulerformat=%15(%c%V\ %p%%%)
set showcmd 
set showmode
set showtabline=1
" set spell
" set spelllang=en_ca,en_gb,en_us,en
set startofline
set incsearch
set background=dark
set smartindent
set autoindent
set cindent
set noerrorbells
set nowrap
set showmatch
set tabstop=5
set softtabstop=5
set shiftwidth=5
set expandtab 
set nosmarttab
" set mouse=a " use mouse everywhere - turns out I don't like this
set ignorecase
set gcr=a:blinkon0
set selectmode=mouse
set mousehide
set ttyfast
set ttybuiltin
set nolist
set printheader=%<%F%h%=%N
" filetail(buff#)[+][RO][GZ][help][Preview] [fileformat]:[filetype]:[charset]   [line,col]  [% of doc]
set statusline=%t(%1.3n)%m%r%{VarExists('b:gzflag','\ [GZ]')}%h%w\ %([%{&ff}]%)%(:%y%)%(:[%{&fenc}]%)\ %=[%1.7l,%1.7c]\ \ [%p%%]
" set statusline=%r%h%w\ %([%{&ff}]%)%(:%y%)%(:[%{&fenc}]%)\ BUFF[%1.20n]%=%1.7l,%1.7c\ \ [%p%%]
set laststatus=2 " always show the status line
set guipty " allegedly improves terminal emulation

" highlight embedded code
let perl_extended_vars=1
let php_sql_query=1
let php_htmlInString=1
let php_folding=1
let php_parent_error_close=1
let html_use_css=1

let g:calendar_monday=1

if has("autocmd")
	autocmd FileType text setlocal textwidth=79
	filetype on
	filetype plugin on " load filetype plugins
	filetype indent on
	filetype plugin indent on
	autocmd BufEnter * :syntax sync fromstart " ensure every file does syntax highlighting (full)

	" jump to last position when reopening a file
	au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
	\| exe "normal g'\"" | endif
endif

if &t_Co>2 || has("gui_running")
     syntax on
     set hlsearch
endif

if has("gui_running")
	cab Q :quit!
else
	cab Q q
endif
cab W w

function VarExists(var, val)
	if exists(a:var) | return a:val | else | return '' | endif
endfunction

```

---

