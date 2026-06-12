---
title: "How do I get a list of commands?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by bdemers on 2007-04-09
I know that "man" will give me syntax of command, but how do I list out the available commands? 

Seems stupid, but I can't copy a file.   This is rather basic.

---

### Post by teaker1s on 2007-04-09
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

[https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1s%29#head-99d622157c4f48a986be26f45f7f1c025014bf1d]("https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1s%29#head-99d622157c4f48a986be26f45f7f1c025014bf1d")

---

### Post by YourSurrogateGod on 2007-04-09
> **bdemers said:**
> I know that "man" will give me syntax of command, but how do I list out the available commands? 

Seems stupid, but I can't copy a file.   This is rather basic.
Here's a pretty comprehensive list alphabetized and all. And if you click on any of them, you can get to the man page behind it.

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by bdemers on 2007-04-09
Yes!!!!!!!!!!!!!!!!!!!!!!

---

### Post by ardchoille42 on 2007-04-09
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

---

### Post by userundefine on 2007-04-09
You can also just press TAB TAB in a terminal and get all available commands on your box. :)

---

### Post by x1a4 on 2007-04-09
Hi,

Look in: 

[I]/bin/
/sbin/
/usr/bin/
/usr/sbin/
/usr/local/bin/
/usr/local/sbin/
/usr/X11R6/bin/
/usr/games/[/I]

EDIT: Also look in the Ubuntu Help Centre

---

### Post by dwblas on 2007-04-09
It's easier to use a GUI like MC (Midnight Commander).  F5=copy from one panel to the other.  I'm not using Gnome Ubuntu, but I think it is in the Gnome install by default.

---

### Post by Austin_KW on 2007-04-09
There a a few basic commands you should learn; (ls,cd,cat,less) for browsing but most people learn them as they use them.

A good start is to use apropos to search man pages

so "apropos copy" will give you a list of all commands that 'do' some sort of copy; a quick scan will then show you 'cp (1)               - copy files and directories'


or "apropos copy | grep file" will show all the copy commands for file


"apropos copy | grep remote" or "apropos remote | grep copy" will show you show to do a remote copy

"apropos text | grep edit" will give you a list of your text editors

then "man commandName" will tell you how to use it

---

