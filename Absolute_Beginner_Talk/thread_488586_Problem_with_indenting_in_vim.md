---
title: "Problem with indenting in vim"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by hyjkim on 2007-06-30
Hey guys,
I have problem I can't figure out. I just installed feisty and compiz fusion on my computer. I'm a vim user but I've never run into a problem like this. When I use visual mode to highlight some code, I usually use == to fix the indentation of my code. On this computer, there has been some unusual behavior.

After highlighting some text, I press = the first time, the status bar of vim tells gives the message "12 lines filtered" or whatever number of lines I've highlighted. Pressing = again inserts the following line into my code:
"indent:Standard input:2:Error:Unexpected end of file"

No matter how many times in the past my code was messy or just wrong, vim never gave me this message. Any ideas on how to fix it?

I was messing around with customizing xterm previously, could this have something to do with it? I believe I downloaded a friend's .Xdefault file or wherever the configuration for xterm is located. Should I delete the file?

Also, a random vim/xterm question, how the heck do I get color syntax highlighting to work?

Many Thanks,
John Kim

Ubuntu nubbin.

---

### Post by hyjkim on 2007-06-30
forgot to post my .vimrc, here it is:

set nocompatible
"set autoindent
set smartindent
set tabstop=4
set shiftwidth=4
"set shiftround
set expandtab
set showmatch
set vb t_vb=
set ruler
set incsearch

if &term =~ "xterm"
if has("terminfo")
set t_Co=8
set t_Sf=<Esc>[3%p1%dm
set t_Sb=<Esc>[4%p1%dm
else
set t_Co=8
set t_Sf=<Esc>[3%dm
set t_Sb=<Esc>[4%dm
endif
endif

---

### Post by hyjkim on 2007-06-30
Should I take this to the vim forums?

---

### Post by hyjkim on 2007-06-30
Problem solved, It was kind of silly but I was unaware that ubuntu came installed with vim-tiny.

---

