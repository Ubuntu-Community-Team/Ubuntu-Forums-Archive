---
title: "vi problems after upgrading to edgy"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-10-29
I'm a newbie, but I've been working a lot with vim.  Now that I've upgraded to edgy, vi is acting really weird.  I type i to go into insert mode, but there is no indication that I am in insert mode.  If I hit backspace to delete a character, the character doesn't get deleted.  Since I'm new at vi, this is really confusing.  Maybe my vim config files are messed up?  Here they are (the ones I know about) if that's the case:

/etc/vim/vimrc:
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
set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark

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
"set showcmd		" Show (partial) command in status line.
"set showmatch		" Show matching brackets.
"set ignorecase		" Do case insensitive matching
"set smartcase		" Do smart case matching
"set incsearch		" Incremental search
"set autowrite		" Automatically save before commands like :next and :make
"set hidden             " Hide buffers when they are abandoned
"set mouse=a		" Enable mouse usage (all modes) in terminals

" Source a global configuration file if available
" XXX Deprecated, please move your changes here in /etc/vim/vimrc
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif


```

I don't know if this is the problem, or what is.  Any help would be appreciated.  Thanks

---

### Post by meng on 2006-10-29
I found this also. In addition, I can't navigate while in insert mode, at least not using the arrow keys. Actually backspace does work, but the screen doesn't refresh immediately. I suspect this has something to do with the terminal rather than vi per se. I have noticed the same thing while using vi in PCLinuxOS and Zenwalk.

---

### Post by 5-HT on 2006-10-29
I'm experiencing the same thing, but haven't had the time to look into it (except for noticing that the vi executable doesn't seem to link directly to vim, but rather vim.tiny).
Vim, however, works fine. Have you two tried calling vim directly?

---

### Post by meng on 2006-10-29
> **5-HT said:**
> Vim, however, works fine. Have you two tried vim?
Thanks for the tip, so I guess it is vi after all and nothing to do with the terminal. Didn't vi link automatically to vim in the past, or am I imagining things?

---

### Post by 5-HT on 2006-10-29
> **meng said:**
> Thanks for the tip, so I guess it is vi after all and nothing to do with the terminal. Didn't vi link automatically to vim in the past, or am I imagining things?

I thought it did, but I'm not sure.

---

### Post by meng on 2006-10-29
I should have clarified. vim certainly does work in the way I'm accustomed.

---

### Post by 5-HT on 2006-10-29
> **meng said:**
> I should have clarified. vim certainly does work in the way I'm accustomed.

Sorry, was refering to your mention of vi linking directly to vim in previous releases. I thought it did as well.

Glad vim's working for you.

---

### Post by David_T on 2006-10-29
I'm pretty sure this is because in your /etc/vim/vimrc, you have
the line:  set compatible.
From within vim (when invoked as ``vi''), what happens when you type
:set nocompatible
?

(edit:  yep, I'm positive this is it.  try alternating between ``:set compatible'' and ``:set nocompatible'' from within vim and you'll see the difference)

---

### Post by AgenT on 2006-10-29
CeeDub,

Diff shows that you have differences:
```
diff /etc/vim/vimrc Desktop/your_vim_cfg 
16c16
< "set compatible
---
> set compatible
20c20
< "syntax on
---
> syntax on
36,38c36,38
< "if has("autocmd")
< "  filetype indent on
< "endif
---
> if has("autocmd")
>   filetype indent on
> endif
56d55
< 
```This means you edited your system wide vimrc file. You should *not* edit /etc/vim/vimrc. Instead, edit your own vim config ~/vimrc. 

Maybe that config is the problem. And vim works fine in Edgy, so there is something wrong with your setup. Arrow keys work. TIP: you should not use the arrow keys, use h,j,k, and l in visual mode instead. Backspace works fine as well.
```
vim --version
VIM - Vi IMproved 7.0 (2006 May 7, compiled Oct 20 2006 09:48:09)
Included patches: 1-35

gnome-terminal --version
Gnome gnome-terminal 2.16.1
```Remove /etc/vim/vimrc and reinstall vim-common. Doing this will fix any future config problems as your edited config will not be replaced when upgrading.

---

### Post by David_T on 2006-10-29
So to actually solve the problem, you would want to comment out that line again in your /etc/vim/.vimrc so
```

set compatible

```
becomes
```

"set compatible

```

Compatibility mode means making vim act like the original vi, which you might want if you were used to working in other versions of Unix.  nocompatible is what you use if you want to use all the features specific to vim.

---

### Post by CeeDub on 2006-10-29
Thanks David_T. That was it.  Vim is working like it used to.  I got a bit nervous there, but thanks to everyone for they're help.

---

