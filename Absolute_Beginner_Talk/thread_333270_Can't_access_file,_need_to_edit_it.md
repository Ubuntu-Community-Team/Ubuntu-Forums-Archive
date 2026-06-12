---
title: "Can't access file, need to edit it"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Oputres on 2007-01-07
Hi!

I need to edit a file that has an red box with a X in it. I can't access it, probably cause I'm not logged in as a SU. I would like to edit this file in a text editor, not in the terminal. Is there a way to log in as a SU in Ubuntu GUI?

---

### Post by Sasa_Ivanovic on 2007-01-07
use :
```

sudo gedit xxx

```
where xxx is the location to your file

---

### Post by Scorpuk on 2007-01-07
Another option would be:

```
gksudo nautilus
```


This would open nautilus with superuser rights.


[COLOR="Red"]**Be warned you CAN kill your system by deleteing the wrong file while running nautilus as superuser as you can delete system files too.**[/COLOR]

---

### Post by Sasa_Ivanovic on 2007-01-07
what's diffrence betwen sudo and gksudo ?

---

### Post by Scorpuk on 2007-01-07
not 100% sure, but I was told to use gksudo to open nautilus as root.

Might be a graphical version of sudo.

I know if I type sudo gedit in the terminal I get a few grunts from the OS, but it still works.

Never tried gksudo gedit.


heh oh well.

---

### Post by ajgreeny on 2007-01-07
*Sudo* is really for root operation in terminal applications and utilities, eg nano, but *gksudo* is for gnome GUI applications such as gedit, and for KDE apps it's *kdesu.*  Mostly nothing ghastly happens if you use sudo, but it is possible to lose root access completely and even be unable to boot if things do go wrong, so try to remember to use the appropriate command rather than sudo for all gui apps.

    *

      NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.


The above comes from the following site:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Read and learn from that, it could save you some heartache in future.

---

