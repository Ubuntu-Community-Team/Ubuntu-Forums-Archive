---
title: "Remove keys from Gconf"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by TonKi on 2007-03-02
How to remove keys from gconf?
eg. /apps/kiba and all thats below
:-k

---

### Post by sanone on 2007-03-09
Well the stuff is inside the ~/.gconf directory. 

So if you want to remove kiba stuff I suggest you take a look at [b]/home/username/.gconf/apps[b] to see if there is some directory named kiba and remove it. At a restart from gnome it should be gone...

Cheers,
San

---

