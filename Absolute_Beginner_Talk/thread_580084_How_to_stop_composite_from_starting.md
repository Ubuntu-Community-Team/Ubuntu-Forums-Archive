---
title: "How to stop composite from starting?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by SmokingGun on 2007-10-18
On Gutsy?  My videos don't play as well on Gutsy.  Even if i turn desktop effects off.  I'm sure it's the composite extension?

---

### Post by smacattack on 2007-11-15
As far as I understand it all you need to do is

sudo gedit /etc/X11/xorg.conf

and add


Section "Extensions"
Option "Composite" "Disable"
EndSection

to the end.

I think that's what you mean anyways...

---

