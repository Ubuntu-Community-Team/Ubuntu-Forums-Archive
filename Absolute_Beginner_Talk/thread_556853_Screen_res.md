---
title: "Screen res"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-09-21
hi guys.. my problem is someone accidnetally kicked the power plug and when I turned on the pc It was in a very bad screen resolution.. how do i restore it? GUI wont let me :S

thx in advance

---

### Post by 900donuts on 2007-09-21
try looking at this its when i had a screen res problem in the past [http://ubuntuforums.org/showthread.php?t=481486](http://ubuntuforums.org/showthread.php?t=481486)

---

### Post by alienexplorers on 2007-09-21
Can you explain in more detail.  What video board, drivers, screen resolution, refresh rates.

---

### Post by johnnyw on 2007-09-21
here is what I got as a result of the command:.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```



> xserver-xorg postinst warning: overwriting possibly-customised configuration   file; backup in /etc/X11/xorg.conf.20070921230947


> **alienexplorers said:**
> Can you explain in more detail.  What video board, drivers, screen resolution, refresh rates.

Ive got ubuntu dapper, my monitor is a viewsonic e70f+.. my vga card is a radeon 9200 se (agp)

---

### Post by 900donuts on 2007-09-21
i say just remember where the back up is and keep going but the first time did any thing like this it messed up and i thought broke xserver and to this day i have no idea how i fixed it (i was every more noob back then) i guess every thing fell into place after i restarted for the second time (the link i gave was the second time i did stuff concerning graphics so don't worry to much)

---

