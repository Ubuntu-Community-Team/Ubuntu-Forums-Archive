---
title: "Screen resolution at startup"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by bob74 on 2007-05-29
I used Dapper for over six months on a daily basis without a single glitch. Since upgrading to 
Feisty I find that about every third switch-on the system starts with a resolution 640*480
with no other resolutions listed. When I switch off and back on again everything is back to normal.
Anyone any ideas as to how to prevent this annoyance-- thanks

---

### Post by techno-mole on 2007-05-29
you could try editing /etc/X11/xorg.conf i had to edit mine in order to set my resolution to 1280x800 at start up
gksudo gedit  /etc/X11/xorg.conf

then look for the "screen" section and add the resolution you want to each of the resolutions listed and that should do it.
so for me what i had to do was add "1280x800" to the start of each line that had a resoltuion in it.
cheers

---

### Post by Aniongap on 2007-05-29
Hi, some month ago I haved the same problem. It is because Ubuntu uses old graphic driver for nVidia cards. Older driver is 845GM and you need 915GM, which supports the driving for any resolution you want to use. So:

sudo apt-get install 915resolution

This will install the dirver. Next step you should create and automation script to enable it every X start. For this you can use:

[https://answers.launchpad.net/ubuntu/+question/4465](https://answers.launchpad.net/ubuntu/+question/4465)

So good luck.

---

### Post by lazyart on 2007-05-29
845GM and 915GM are intel cards, not nVidia...

---

### Post by pablo66 on 2007-05-29
I am trying to change my refresh rate running feisty from 50hz to 60hz(the native refresh rate) and when I open: /etc/X11/xorg.conf the file is empty, nothing in it, nada.

---

