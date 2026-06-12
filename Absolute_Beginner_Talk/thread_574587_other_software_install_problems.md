---
title: "other software install problems"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by markiv on 2007-10-13
hello, new here. Just got Ubuntu yesterday.

whenever i try to install anything using Applications>Add/Remove... I get this error:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

tried running 'dpkg --configure -a' in terminal.
got this msg: "dpkg: requested operation requires superuser privilege"

so, could i please get some help here?

---

### Post by markiv on 2007-10-13
aargh.
same error while trying to update Ubuntu even.

---

### Post by WanderingKnight on 2007-10-13
You need to have root access to use the dpkg command. To do so under a terminal, you need to type "sudo" before the command, which will give you root privileges just for that action. Before performing the action, the shell will ask you for your password--keep in mind that your keystrokes won't print on the screen when inputting it.

---

### Post by cornel_me on 2007-10-13
superuser privilege means you need to run the command as sudo:

sudo dpkg --configure -a

---

### Post by markiv on 2007-10-13
thanks a lot.

---

### Post by markiv on 2007-10-13
anyway, what exactly did that command do?

---

