---
title: "[SOLVED] Possible problem with VIM editor"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-02-22
I think that there may be a possible problem with the VIM editor in the Edgy Eft release. When I was pushing my arrow keys, instead of navigating the cursor it printed out characters, A,B,C,D. I checked the keyboard layout and it should be working....

---

### Post by tonyr1988 on 2007-02-23
You're in INSERT mode. Press Escape and use your arrow keys. Plus, VIM wasn't really designed for use with the arrow keys. You're supposed to use the hjkl keys to move around (faster editing). If you just need a simple console-based editor, you may wanna try nano or pico.

Please don't take any offense to that, it's just that VIM is a weird beast and can take a while to learn. If you want to learn it, it's not too hard. If you don't want to, there are definitely better alternatives. :)

---

### Post by nickoli_02 on 2007-02-23
yea... vim does some really weird stuff... it's best to have the manual or at least a list of common commands at your side while using vim, at least until you're quite comfortable with it :)

---

### Post by Stedwick on 2007-02-23
I am hardly an expert, but if you create a blank "~/.vimrc" file

~$ vim .vimrc
:wq

it will fix the arrow keys. I think what this does is initialize vim with the default settings, and with the default settings the arrow keys do what you'd expect them to do. I'm not sure why Ubuntu has it set up so the arrow keys are weird.

Woohoo, my first post on these forums, and I'm actually helpful!

Stedwick

---

### Post by g0rdy on 2007-02-28
reopen that blank  .vimrc like the poster above said to make and add  "syntax on"  without the quotes and now all files, bash scripts, configs (.pinerc,etc) will have syntax highlighting...

very annoying why the default is the way it is.........

---

### Post by taurus on 2007-02-28
```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by noorez on 2007-02-28
Whats the difference then between vim and vim-full?

---

### Post by Maestro23 on 2007-02-28
Taken from the Synaptic Entry for Vim-Full:

> Vi IMproved - enhanced vi editor - full fledged version
Vim is an almost compatible version of the UNIX editor Vi.

Many new features have been added: multi level undo, syntax
highlighting, command line history, on-line help, filename
completion, block operations, folding, Unicode support, etc.

This package contains a version of vim compiled with support for
the GNOME2 GUI and scripting support for Perl, Python, Ruby, and
TCL.

---

