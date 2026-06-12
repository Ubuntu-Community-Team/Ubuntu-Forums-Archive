---
title: "Ubuntu 6.10 firefox is closing"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by ndworecki on 2007-01-11
hey guys firefox is closes when i login into sites like gmail, and myspace, and i dont know whats wrong


Any Ideas???


Thanx

           -Nathaniel

---

### Post by x1a4 on 2007-01-12
Hi,

When Firefox crashes, do the pages you try to view have flash?  If so, the culprit is probably
an incorrect setting in your *xorg.conf* file.  

With superuser priviledges, open */etc/X11/xorg.conf* and make sure your default depth (as in colour depth) is set to 24. 

Good luck.

---

