---
title: "will reinstall 7.04 solve cdrom mount problem?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by David4 on 2007-05-30
Installed Ubuntu 7.04 about 1 month ago, I liked it, however having a lot of difficulties with my cdrom and dvd'.
They are not mounted and have been trying thru the help of various members to solve it, yet have to go back to windows every time I need to use use a cd burner or whatever.
Wonder if I should reinstall Ubuntu, will that perhaps help?
It seems to me that on install the OS should recognize and mount all drives including the cd/dvd drives?
I manage computers at a practical level but certainly not prepared to deal with commands and syntax issues.
Your comments appreciated
David

---

### Post by alienexplorers on 2007-05-30
In your ftab file do you have a line like this:
> /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

If not try adding it.

---

### Post by David4 on 2007-05-30
Sorry, what is a ftab?
David

---

