---
title: "Made two default screens, no screens found, I NEED HELP!"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Aryding on 2008-01-11
It now says "No Screens found" when I enter startx.  Before I had change accidentally to two default monitors (one notebook, and another external lcd).  Then I reconfigured xserver-xorg and am now at the no screens found part when I enter startx.  What is the best way to get back to normal?

Any help would be great, THANKS!

---

### Post by Aryding on 2008-01-11
Well I replaced xorg.conf with a fresh one from the live cd.  Now I just have some glitches to take care of within ubuntu as well as build my xorg.conf again.

---

### Post by chewearn on 2008-01-11
> **Aryding said:**
> Well I replaced xorg.conf with a fresh one from the live cd.  Now I just have some glitches to take care of within ubuntu as well as build my xorg.conf again.


#-o#-oback-up back-up before changing:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

