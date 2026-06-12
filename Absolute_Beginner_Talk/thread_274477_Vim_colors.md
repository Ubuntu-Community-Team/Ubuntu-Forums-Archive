---
title: "Vim colors"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2006-10-09
I am having trouble getting VIM to recognize a file extension ".def" as a c++ file, thus I get no syntax highlitghing. Any tips on how I can fix that?

---

### Post by mitch.c on 2006-10-10
> **mdecler2 said:**
> I am having trouble getting VIM to recognize a file extension ".def" as a c++ file, thus I get no syntax highlitghing. Any tips on how I can fix that?

Add the following to .vimrc:
```
# ~/.vimrc
filetype plugin on
filetype indent on
syntax on

au BufRead,BufNewFile *.def set filetype=cpp
```

---

### Post by mdecler2 on 2006-11-01
The above suggestion did not seem to work when I restarted vim.

I have attached my entire .vimrc file.
Note I added
```
filetype plugin on
filetype indent on
syntax on

au BufNewFile,BufNewFile *.def set filetype=cpp

```
on line 28 proceeding my environment sets. I have not installed any plugins for vim, so I am wondering if "filetype" is actually a special plugin I need for highlighting files other than .cpp's.

Any advice or comments are appreciated.

(It does not seem like my attachment attached. I am going to try again below).

---

### Post by mdecler2 on 2006-11-01
> **mdecler2 said:**
> The above suggestion did not seem to work when I restarted vim.

I have attached my entire .vimrc file.
Note I added
```
filetype plugin on
filetype indent on
syntax on

au BufNewFile,BufNewFile *.def set filetype=cpp

```
on line 28 proceeding my environment sets. I have not installed any plugins for vim, so I am wondering if "filetype" is actually a special plugin I need for highlighting files other than .cpp's.

Any advice or comments are appreciated.

(It does not seem like my attachment attached. I am going to try again below).

So, the file attachment system is not allowing my attachment due to "Invalid file"....
here it is :

```
set backspace=2
set cindent
set clipboard=unnamed
set cpoptions+=$
set expandtab
set ignorecase
set incsearch
set laststatus=2
set nobackup
set noerrorbells
set noesckeys
set nohlsearch
set nowrap
set ruler
set shiftwidth=3
set shortmess+=I
set showcmd
set showmode
set smartcase
set t_vb=
set ts=3
set visualbell
set whichwrap=b,s
set wildmode=longest,list
set writebackup

filetype plugin on
filetype indent on
syntax on

au BufNewFile,BufNewFile *.def set filetype=cpp

fu! SynFolds()
   set foldmethod=syntax
   set foldcolumn=5
   syn region myFold start="{" end="}" transparent fold
endf

fu! OnEditELF()
   set foldmethod=manual
   set foldcolumn=5
   %!readelf -a "<afile>:p"; echo XXXXXX; objdump --source "<afile>:p"
   :1,/^XXXXXX$/-fo
   " :1foldopen
   :/^XXXXXX$/+,$fo
   :$foldopen
   :/^XXXXXX$/d
   :1
   set buftype=nofile
endf

fu! OnEditFile()
   syn sync fromstart
   set foldmethod=manual
   set foldlevel=99

   syn match EvilSpace " \+$" containedin=ALL
   hi link EvilSpace Error
   syn match EvilSpace2 "\t" containedin=ALL
   hi link EvilSpace2 Error
endf

"au BufNewFile,BufRead   *                      silent call OnEditFile()
"au BufNewFile,BufRead   *.c,*.C,*.h,*.cpp,*.pl silent call SynFolds()
"au BufNewFile,BufRead   *.o,*.elf              silent call OnEditELF()

hi FoldColumn ctermbg=darkblue ctermfg=white
hi! Comment term=bold ctermfg=cyan


```

You are dedicated if you read through all that :rolleyes:

---

### Post by mitch.c on 2006-11-03
'filetype plugin on' loads: $VIMRUNTIME/filetype.vim which handles automatic detection of file types. In ubuntu, $VIMRUNTIME is usually /usr/share/vim/vim64.

You can check to make sure it's enabled in vim by using the command:
```
:filetype
```
which should return something like:
```
filetype detection:ON  plugin:ON  indent:ON
```
When editing a .def file, you could also try the command:
```
:set filetype?
```
Which should return **one** of the following:
```
filetype=def
filetype=cpp
```
Load an existing .def file to check highlighting, vim isn't good about filetype detection until a file has been saved with the appropriate extension.

If all else fails, read: [http://vimdoc.sourceforge.net/htmldoc/filetype.html#filetype](http://vimdoc.sourceforge.net/htmldoc/filetype.html#filetype)

---

