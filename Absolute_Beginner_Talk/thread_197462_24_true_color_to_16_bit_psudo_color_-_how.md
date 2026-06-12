---
title: "24 true color to 16 bit psudo color - how?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-15
How can I change form 24 true color to 16 psudo color?

---

### Post by muep on 2006-06-15
```
gksudo gedit /etc/X11/xorg.conf
```

Find a line like:
        DefaultDepth    24

and change it into:
        DefaultDepth    16

Restart X or reboot computer

done

---

