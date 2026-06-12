---
title: "How to make vim settings persistent?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Olnex on 2008-01-08
I use vim to write code, the syntax highlighting feature is cool, but I need to turn it on every time I run vim, by :syntax on or from the menu of vim-gnome, vim-gnome also support theme, also, I need to reset it every time, my question is, how to make these settings persistent so that I don't need to reset it each time I use it?
Thanks a lot.

---

### Post by peabody on 2008-01-08
Short answer

Open terminal
```
echo >> ~/.vimrc syntax enable
```

Long answer:

Learn how to setup a vimrc file.  :help usr_05

---

