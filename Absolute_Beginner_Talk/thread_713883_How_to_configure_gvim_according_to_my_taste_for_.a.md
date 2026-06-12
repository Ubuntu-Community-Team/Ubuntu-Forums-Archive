---
title: "How to configure gvim according to my taste for .any extension file"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by ashishsontakke on 2008-03-03
Hi,
I want to configure gvim for some extension file like .c, .tcl 

Like in .c, i want to have differnt colors for keywords, constants etc.
So i want to do this for any extension file.
Thanks

---

### Post by linfidel on 2008-03-03
> **ashishsontakke said:**
> Hi,
I want to configure gvim for some extension file like .c, .tcl 

Like in .c, i want to have differnt colors for keywords, constants etc.
So i want to do this for any extension file.
ThanksIt's pretty easy, actually. It uses two files together, a syntax file and a colors file, both text files with .vim extensions. You can find them in the vim directory; I think it may be in /usr/share/vim, but I'm not at my Ubuntu system right now.  

If you can locate the vim directory, you will see subdirectories including systax and colors.  For customized versions, you should copy one of each to your profile directory, to ~/.vim/syntax and .vim/colors.  If you don't have a .vim, just create one.

Try to pick a syntax file that might be close,; c.vim is standard c, cpp.vim is c++, etc.  Get a language you know well, so you'll understand what's going on.  But you'll have to figure out a lot on your own, and hopefully know some regex.  In gvim, type :help syntax to get some documentation.

The colors are not language specific, but you may want to customize that, too.  The tags are referenced by the syntax file.

Hope this helps a little.

---

### Post by seventhc on 2008-03-03
an easier way may be to open a terminal and paste this in
```
sudo vim /etc/vim/vimrc
```then uncomment line 20 '*syntax on*
also might want to add a specific line for whatever your using. I add a line for python, but the syntax on will most likely work too, and will carry over to gvim.
here is mine
```

" All system-wide defaults are set in $VIMRUNTIME/debian.vim (usually just
" /usr/share/vim/vimcurrent/debian.vim) and sourced by the call to :runtime
" you can find below.  If you wish to change any of those settings, you should
" do it in this file (/etc/vim/vimrc), since debian.vim will be overwritten
" everytime an upgrade of the vim packages is performed.  It is recommended to
" make changes after sourcing debian.vim since it alters the value of the
" 'compatible' option.

" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
runtime! debian.vim

" Uncomment the next line to make Vim more Vi-compatible
" NOTE: debian.vim sets 'nocompatible'.  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
" set background=dark

" Uncomment the following to have Vim jump to the last position when
" reopening a file
"if has("autocmd")
"  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
"    \| exe "normal g'\"" | endif
"endif

" Uncomment the following to have Vim load indentation rules according to the
" detected filetype. Per default Debian Vim only load filetype specific
" plugins.
if has("autocmd")
  filetype indent on
endif

" The following are commented out as they cause vim to behave a lot
" differently from regular Vi. They are highly recommended though.
"set showcmd        " Show (partial) command in status line.
"set showmatch        " Show matching brackets.
set ignorecase        " Do case insensitive matching
set smartcase        " Do smart case matching
set incsearch        " Incremental search
"set autowrite        " Automatically save before commands like :next and :make
"set hidden             " Hide buffers when they are abandoned
"set mouse=a        " Enable mouse usage (all modes) in terminals

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" added
set backup              " produce *~ backup files
set backupext=~         " add ~ to the end of backup files
set nu                  " enable line numbering

" python stuff
set et
set sw=4
set ts=4
set smarttab
autocmd BufRead,BufNewFile *.py syntax on
autocmd BufRead,BufNewFile *.py set ai
autocmd BufRead *.py set smartindent cinwords=if,elif,else,for,while,try,except,finally,def,class
map <f2> :w\|!python %<cr>" Source a global configuration file if available
" end of python stuff
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" XXX Deprecated, please move your changes here in /etc/vim/vimrc
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif

``` and it highlights anytime I open code.
Note, if you want to use gedit then use
```
gksu gedit /etc/vim/vimrc
```
or if its in your home dir already then just 
```
gedit .vimrc
```
Hope this helps.

---

### Post by linfidel on 2008-03-03
> **seventhc said:**
> an easier way may be to open a terminal and paste this in
```
sudo vim /etc/vim/vimrc
```then uncomment line 20 '*syntax on*
also might want to add a specific line for whatever your using. I add a line for python, but the syntax on will most likely work too, and will carry over to gvim. Easier, maybe; but not a good idea.
If you want to modify .vimrc (is there really a vimrc without the leading dot?), the place to do it is in your home directory, not the global one that might get replaced.

But it seems as if the original poster already has syntax highlighting on, he just seems to want to add more filetypes,  like the ones for c or c++.

By the way, I'm a programmer who uses gvim every day, so I have a fairly good idea how it works. People that are looking for the easier way probably won't be learning vim anyway.  :-)

---

### Post by seventhc on 2008-03-03
yes, the one in etc/vim is a global config and doesn't have the leading dot.
etc/vim/vimrc
I create a local one with the dot, but since I'm not sure of his set up i gave both examples. 
Free to choose whatever works.

---

### Post by ashishsontakke on 2008-03-04
Thanks to both of you... :)
I will try to do what you suggested.

---

