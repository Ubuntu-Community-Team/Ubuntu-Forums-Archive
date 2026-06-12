---
title: "Refresh rate"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by infinitewisdom on 2006-07-05
Hi,
I am a complete noob to Linux but are very happy so far with Ubuntu. Problem is my refresh rate is fixed at 60hz and its really hurting my eyes. I have an Asus Pundit P2-AE2 sff with via graphics and I have the dapper drake vers. I literally know nothing of Linux but are happy tojump into the deep endwith some guidance. Any help appreciated.

---

### Post by MaximB on 2006-07-05
welcome to the forum !
in order to change the refresh rate you need to go : (if you are using gnome)
system - preferences - screen resolution
there you can change it and the screen resolution
if you don't see option higher then 60hz you might need to install your video card properly

---

### Post by infinitewisdom on 2006-07-05
Thank you!
Right, I have integrated graphics as I am using Linux on my 2nd pc by router. Where would I locate drivers for Linux? Would that be from Asus or Via?

---

### Post by MaximB on 2006-07-05
sorry but I never heard of your video card
try searching in your companies sites for LINUX drivers for your video card
you may need to edit some stuff after the installation

search the forum - maybe somone already posted somthing about your video card

---

### Post by confused57 on 2006-07-05
I think Ubuntu has a "via" driver for your integrated graphics.

You can:
```
sudo dpkg-reconfigure xserver-xorg
```

On the first screen, select "no" to autodetect your monitor, then you can probably just select the default options, until you get to the video driver selection...if "via" is an option, select it and continue.

You can also look into your xorg.conf file to see what driver you're currently using:
```
cat /etc/X11/xorg.conf
```

---

