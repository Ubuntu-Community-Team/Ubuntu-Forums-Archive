---
title: "Capturing video question."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-05-20
How would i go about capturing video from my Hauppauge PVR-150 card? Im trying to capture from the a/v plugs on the card from a video camera

---

### Post by ccfjeff on 2007-06-06
> **adt41287 said:**
> How would i go about capturing video from my Hauppauge PVR-150 card? Im trying to capture from the a/v plugs on the card from a video camera

SourceForge has some programs that might do the trick for you:

[http://sourceforge.net/softwaremap/trove_list.php?form_cat=126](http://sourceforge.net/softwaremap/trove_list.php?form_cat=126)

---

### Post by adt41287 on 2007-06-25
for future reference:
[http://mythtv.org/pipermail/mythtv-users/2006-December/160856.html](http://mythtv.org/pipermail/mythtv-users/2006-December/160856.html)

to set to composite:
v4l2-ctl --device=0 --set-input=2

to set back to tuner:
v4l2-ctl --device=0 --set-input=0

---

