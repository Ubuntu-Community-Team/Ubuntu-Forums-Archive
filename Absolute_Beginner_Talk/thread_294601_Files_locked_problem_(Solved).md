---
title: "Files locked problem (Solved)"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by qwwq on 2006-11-06
Many files i need are locked. the sources list, a file i made on my dekstop where i mount drives when i need them, and many other things. what caused this?

---

### Post by ner0tic on 2006-11-06
are you trying to access them as a normal user when they are needed to be root (sudo)?

the source list for example you have to be root to edit.

> sudo vi /etc/apt/source.list

---

### Post by qwwq on 2006-11-06
i typed that in the terminal and i got this.


E325: ATTENTION
Found a swap file by the name "/etc/apt/.source.list.swp"
          owned by: root   dated: Tue Nov  7 18:54:52 2006
         file name: /etc/apt/source.list
          modified: YES
         user name: root   host name: Khaderpc
        process ID: 6560
While opening file "/etc/apt/source.list"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/source.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.source.list.swp"
    to avoid this message.

Swap file "/etc/apt/.source.list.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (Q)uit, (A)bort, (D)elete it:



so i typed E and got this.



~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
"/etc/apt/source.list" [New File]                             0,0-1         All

if i open the source.list file in Text Editor, it is read only but  can see the sources

---

### Post by aysiu on 2006-11-06
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) should help you out.

---

### Post by qwwq on 2006-11-06
hey thanks that worked

---

