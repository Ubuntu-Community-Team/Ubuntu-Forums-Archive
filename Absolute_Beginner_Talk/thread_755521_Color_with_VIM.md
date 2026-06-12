---
title: "Color with VIM"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by linuxneeewb on 2008-04-14
I would like to know how to use color with VIM. I followed the url below and was able to get color to work in vim, but I have to type the command :syntax enable     each time.

I would like VIM to have color by default. I can get color if I type that command above, but by default the text is always black. I would like color to be default. Any and all help is appreciated. Thanks.

[http://ubuntuforums.org/showthread.php?t=569099](http://ubuntuforums.org/showthread.php?t=569099)

:guitar:

---

### Post by cm.squared on 2008-04-14
If you create a file called .vimrc in your home directory vim will execute the commands inside of it every time you start vim.  Add the command "syntax on" (without the quotes, and you don't need the colon since vim knows you will be executing commands) to the file and you should be set.

---

### Post by linuxneeewb on 2008-04-14
Thanks works perfectly now!!!
:popcorn:

---

### Post by cm.squared on 2008-04-14
Awesome.  Glad I could help.

---

