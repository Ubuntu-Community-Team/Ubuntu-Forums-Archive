---
title: "i broke the x server!"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by djbenny on 2007-05-19
hello

i tried installing nvidirtera drivers and then restarted the x server now it comes up with a blue screen saying it can not be started, i removed the drivers but it still does not work again saying there are no devices!

help is much appreciated

---

### Post by Titus A Duxass on 2007-05-19
sudo dpkg-reconfigure xserver-xorg

---

### Post by heimo on 2007-05-19
As Titus suggests above. During reconfiguring, instead of nvidia, you can try selecting nv driver.

---

### Post by djbenny on 2007-05-19
ok, well i tried selecting the nvidia driver and it still didnt wor i shall have to try again in a minute

---

### Post by gn2 on 2007-05-19
Have you tried installing the NVidia driver through Automatix?

[www.getautomatix.com](www.getautomatix.com)

---

### Post by heimo on 2007-05-19
> **djbenny said:**
> ok, well i tried selecting the nvidia driver and it still didnt wor i shall have to try again in a minute

You could also try selecting nv driver (which is the free one and lacks 3d acceleration). At least that way you may get your Xorg back.

---

### Post by djbenny on 2007-05-20
ok well i got it back its just not going up to the full resolution of the screen and also games are going very slow i tested on tuxkart and its frame rate is about 2fps or so :(

help me out please i used the nvdriver on the xorg config

---

### Post by abhishek456 on 2007-05-20
try replacing Driver nvidia or what so it is with "vesa" under Section "Device" in /etc/X11/xorg.conf

---

### Post by djbenny on 2007-05-20
i do not understand what you mean lol?

---

### Post by djbenny on 2007-05-21
i used automatix to install nvidia drivers and they worked but every time i reboot i hasve to reeset the resolution

---

