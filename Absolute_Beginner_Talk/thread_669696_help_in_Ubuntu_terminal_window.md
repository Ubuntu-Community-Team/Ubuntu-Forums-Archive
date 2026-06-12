---
title: "help in Ubuntu terminal window"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-16
how can i access help information on a particular command when in terminal window on Ubuntu 7.10?  (the equivalent of ***command /?*** under windows DOS.  thanks.

---

### Post by kellemes on 2008-01-16
man command

---

### Post by bodhi.zazen on 2008-01-16
type help, that will list (all ? ) commands

(you may want to help | less )

then man <command>

or go here : [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Matt26 on 2008-01-16
thanks- how can i exit/escape the manual once i have found information on the command?  it just displays pages of information and i'm not sure how to get back to the command line again.

---

### Post by lgambett on 2008-01-16
just press q

---

### Post by lgambett on 2008-01-16
Some more infos on the command line help system
help gives advice only on the so called "Internals", commands contained in the bash executable
you can also use the command
**apropos something**
e.g. apropos keyboard to have a list of all commands containing in their description the word keyboard.
You can also use the **info** command instead of **man**; the man information is sometimes obsolete, while the info information is sometimes more up-to-date.

---

