---
title: "how to revert back to the drivers installed by ubuntu"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Fibre on 2005-12-30
Can someone help me revert back to the old drivers I had for my ati card please

I've gone terribly wrong and just want to go back to what was working.

---

### Post by az on 2005-12-30
boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

and then run

init 2


You won't be asked any questions and everythingabout your X server will be reset to default.  If you want to customise some settings, omit the -phigh

---

