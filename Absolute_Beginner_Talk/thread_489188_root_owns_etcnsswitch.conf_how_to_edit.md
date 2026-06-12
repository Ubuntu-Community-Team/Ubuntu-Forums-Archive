---
title: "root owns /etc/nsswitch.conf how to edit"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by jc508 on 2007-07-01
Hi,
One of the other threads suggests to "Then edit /etc/nsswitch.conf and modify the hosts line by adding wins to the end"

Well root seems to own this file and it wont let me edit it.
So the questions become ?
* What is the default root passwd ?
* How do you 'be' root to edit files like this ?

Thanks in advance
JC

---

### Post by bodhi.zazen on 2007-07-01
To edit the file use:

```
gksudo gedit /etc/nsswitch.conf
```

Ubuntu uses sudo rather then root :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can become root with sudo -i or gksudo nautilus

---

### Post by jc508 on 2007-07-01
Thanks,
that did it.  I searched for 'root but not 'sudo' 

Can this be accessed via the GUI or only as a command ?

---

### Post by davidjmayo on 2007-07-01
Code:

gksudo gedit /etc/nsswitch.conf

The gksudo before the command executes (runs) that command as root (i.e. with root privieges) You use gksudo before (not all) GUI applications. So the command runs gedit as root.

Use sudo for the command line to do something as root

---

### Post by Atomic Dog on 2007-07-01
You could always type "sudo su" and become root.  It is not recommended, but it does work well if doing a lot of things as root.

---

