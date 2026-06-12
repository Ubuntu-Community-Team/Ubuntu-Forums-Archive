---
title: "Strange warning or error with gedit"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by phr0ze on 2007-06-19
I use gksudo gedit file syntax in the terminal and I get the warning below.

(gedit:16373): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Do I need to be concerned? Gedit does appear and work fine after this.

---

### Post by Seisen on 2007-06-19
I think it might be a bug with gedit and gksudo. I get that error everytime I use gksudo with gedit. I personally wouldn't worry about it.

---

### Post by starcraft.man on 2007-06-19
> **phr0ze said:**
> I use gksudo gedit file syntax in the terminal and I get the warning below.

(gedit:16373): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Do I need to be concerned? Gedit does appear and work fine after this.

Ignore it, nothing of any importance. It has already been [reported as a bug ]("https://launchpad.net/ubuntu/+source/gksu/+bug/23917")and since its low priority I imagine it will get done some time, eventually....

---

