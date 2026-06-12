---
title: "Cannot delete usesless folder"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by G_force on 2007-02-13
I have a useless empty folder that i cannot delete

i went to terminal and typed

<code>

sudo su

</code>

and logged in as root and it still would let me delete it

i am a newbie, point me in the right direction

---

### Post by ewankho on 2007-02-13
No hidden files? what command did you use to delete?

---

### Post by G_force on 2007-02-13
i used the gui

---

### Post by renzokuken on 2007-02-13
to remove a directory run

```
sudo rm -r /path/to/directory
```

from CLI

---

### Post by G_force on 2007-02-13
cheers fellas

---

### Post by mixmaster on 2007-02-13
Just for future reference, becoming root on a terminal does not make you root for all the other sessions running.  In this case it sounds as though you set up a root session in a terminal (by the way, sudo -i will do that for you) but then used a GUI to attempt to do the delete.  Unless the GUI was started from the root session it will still be running with the permissions of the ID you logged on as.

If you really want to perform root-level functions from a gui, then use

*gksudo <command>*

In this case, "*gksudo nautillus*" would bring up a file manager with root priviliges.

If you do this, make sure you close the root-enabled app immediately you have done what you need to 'cause you can do a hell of a lot of damage if you forget it has root access.

---

