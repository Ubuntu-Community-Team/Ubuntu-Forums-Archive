---
title: "GnomeUI-WARNING **: While connecting to session manager:"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-08-01
Now started getting these are they because of updates?

$ gksudo gedit /etc/X11/xorg.conf

(gedit:26450): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

$ gksudo nautilus

(nautilus:26575): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Anybody know why this is happening the run fine. But it is a bit annoying.

---

### Post by aysiu on 2006-08-01
Read [this](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917) and [this](http://www.psychocats.net/ubuntu/graphicalsudo).

---

### Post by orb9220 on 2006-08-01
Thanks as my X girlfriend's use to say "That was Quick!"

Thanks for the info.

---

