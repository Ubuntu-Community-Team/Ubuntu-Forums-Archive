---
title: "Getting right display driver on install"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by BeardedOne on 2007-07-24
I finally got the s3 unichrome display on my laptop working by telling the 7.04 live CD to use safe graphics mode.  I understand this forces it to use VESA.  That's fine with me, it works.

Question: Now that I've got it working with VESA, when I install 7.04 for real will it automatically use VESA or do I need to tell it somehow?  Please bear in mind that I need to tell it before it tries to run in order to avoid having an almost helpless desktop.

Suggestions?

Thanks

---

### Post by Rocket2DMn on 2007-07-24
I think you should go for the install.  If the VESA driver is not setup despite telling the LiveCD to use it, you will be able to access a terminal if the X-server fails to show.  From here you can reconfigure X to use the VESA driver with the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
You will either be dropped to the terminal if X-server doesn't load, or if the screen just goes blank you can hit CTRL+ALT+F2 (all the way to F7) to get to a terminal

---

### Post by Seisen on 2007-07-24
It might and it might not but it is a relatively easy fix if it doesn't.

---

### Post by BeardedOne on 2007-07-24
Thanks.

What I understand is that once I get it to load from the CD with VESA, it will use that driver when I install.  Also, that if it doesn't, the code above will force VESA.

---

