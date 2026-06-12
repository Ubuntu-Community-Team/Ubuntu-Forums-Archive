---
title: "Some sort of script file thing :-S"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by daon on 2007-02-28
Hi ladies and gents, new to Linux but certainly not to computers.
I need to know how to create a file that will run a set of terminal commands. For example, make a file called "Internet Connection" that will run:

$ pon ueagle-atm

(which is the command I use to connect my modem to the Internet) when I open it. Maybe this isn't an Absolute Beginner type question, but I'm an absolute beginner myself so it shouldn't be a problem ;)

---

### Post by kerry_s on 2007-02-28
Just create a launcher/icon and put your command in the command box and tick the run in terminal if it has to run in terminal, but i think the command is enough.

---

### Post by yabbadabbadont on 2007-02-28
```
#! /bin/bash
pon ueagle-atm
```
Save the file as InternetConnection or similar.  Then change it permissions so that it is executable.  "chmod 755 InternetConnection"  If you create a shortcut for this, be sure to check the box that reads something like, "Run in terminal".

Edit: Too slow.  :D  His solution is simpler.

---

### Post by daon on 2007-02-28
Excellent guys, cheers. I like this forum - fast responses!

---

