---
title: "Touchpad not installed on my laptop"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by jongleberry on 2007-03-24
hi guys i just installed ubuntu 6.10 on my old falling apart alienware sentia.  however when i installed it, my touchpad never worked.  anyone know how to make it work? it sucks having to use a mouse on a laptop all the time...

---

### Post by Bachstelze on 2007-03-24
YOu mean it doesn't work at all (i.e. it doesn't move when you touch it) ? If so, are you sure it is enabled in your BIOS and you don't have a button on your laptop to turn it on/off ?

---

### Post by jongleberry on 2007-03-24
it does not work at ALL.  i do not konw how to go to bios and what doy ou mean to turn it on and off?

---

### Post by HereInOz on 2007-03-24
This may not help, but I have an old NEC M300 where neither the keyboard nor the touchpad worked with Dapper or Edgy.  However, wonder of all wonders, everything works with the Beta release of Feisty.

You may wish to give Feisty a try with the Live CD and see what you get.

---

### Post by Bachstelze on 2007-03-24
jongleberry : please paste the output of

```
ls /dev/input
```

---

### Post by jongleberry on 2007-03-24
ls /dev/input
by-id by-path event0 event1 event2 event3 mice mouse0 mouse1 ts0 ts1

---

### Post by Bachstelze on 2007-03-24
All right, you have mouse0 and mouse1, your touchpad is certainly one of these. Do you know what kind of touchpad you have ?

---

