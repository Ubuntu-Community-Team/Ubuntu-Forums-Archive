---
title: "How can I know what video card Im using?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-01-01
titl

---

### Post by NilsE on 2008-01-01
Do the following in a terminal and it will tell you all you want to know about  your hardware.  You can scroll back through it if it is long.

ALL HARDWARE DO:  sudo lshw

OR

JUST VIDEO DO: sudo lshw -C video

OR

Go into: System > Preferences > Hardware Information

---

### Post by spydon on 2008-01-01
You can do this:
```
lspci | grep 'VGA'
```

---

### Post by Fixman on 2008-01-01
Cool thanks.

---

