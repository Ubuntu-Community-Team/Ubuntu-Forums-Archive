---
title: "cant get into xorg.conf anymore?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-12
I've been messing around with xorg.conf to try to get my tablet to work properly...so far this is really pissing me off...when i try to do sudo nano etc/X11/xorg.conf it brings me to a blank document now but when i open it outside terminal i can see the texts...just cant edit and save that way....how do i fix it so i can get back to xorg in terminal?

---

### Post by mikewhatever on 2008-04-12
<gksudo gedit /etc/X11/xorg.conf> or <sudo nano /etc/X11/xorg.conf>.

---

### Post by waggingwabbit on 2008-04-12
but when i type that in i just get a blank document....

---

### Post by sam hassell on 2008-04-12
in your original post you typed etc/X11, when you should have typed /etc/X11. was that a typo?

---

### Post by mikewhatever on 2008-04-12
When you miss a slash or point to a location that does not exist, it just opens an empty file. Double check the path you enter.

---

### Post by waggingwabbit on 2008-04-12
dam...i guess i been typing that in too much and somehow forgot? x.x

thanks guys =D

---

