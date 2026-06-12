---
title: "GRUB error message at startup"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Bludge on 2007-08-08
I have Ubuntu 6.10 Edgy Eft installed in my computer, and it always worked beautifully. However today the screen froze and I had to shutt if off pressing the button.

When I reboot the machine, I got the following messages:

GRUB Loading stage 1.5
GRUB loading, please wait...
Error 24

In order to solve the problem (the machine does not boot, it stops there, at the error message), I inserted the CD and tried the option Recovery of a Broken System, but it does not seem to be working.

I guess a track might be damaged. Any of you guys now of any command I could use in the command line to check and restore flawed tracks? I would hate to have to reinstall Linux in my system.

Finally, my hd is a Sata one.

Thanks in advance for any tip

---

### Post by Cypher on 2007-08-08
If you have the Live CD boot into Ubuntu and then open a terminal and type
```

fdisk -l

```
For each of the Linux/EXT3 partitions listed, dp
```

e2fsck -y /dev/XXX

```
Where XXX is whatever fdisk shows you. This will check the HD's and automatically fix whatever it can.

---

