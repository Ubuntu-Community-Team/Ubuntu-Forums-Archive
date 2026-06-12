---
title: "change openoffice splash"
date: 2004-12-03
forum: Art &amp; Design
---

### Post by doni on 2004-12-03
hi there...


is there a way to change the openoffice splash? i would like to have one that fits more into the ubuntu colors...

thanks
doni

---

### Post by amoser on 2004-12-14
I found out how to change the start splash in open office, just create an image, save it as bmp.  The open a terminal, type sudo <where the image is saved at>/intro.bmp /usr/lib/openoffice/program/intro.bmp.  That should do it for you.  But, if you don't want a splash screen (and faster OOo startup time) install ooqstart-gnome.

~Alan

P.S. I am going to start working on a OOo splash right now

---

### Post by MGStreak on 2007-04-20
Hi there, for the longer answer, you can read a discussion here: 
[http://ubuntuforums.org/showthread.php?t=346908](http://ubuntuforums.org/showthread.php?t=346908)

or to get right to it, this site has the specific step-by-step instructions:
[http://www.newsforge.com/software/03/04/22/1931223.shtml?tid=51](http://www.newsforge.com/software/03/04/22/1931223.shtml?tid=51)

It worked for me, so I hope this helps!

---

### Post by WishMaster on 2007-05-02
[SIZE=4][B]For Feisty:

[/B][/SIZE] 1) Download (or make your own) splash-screen in .bmp-format.

2) Backup the original splash:
```
sudo mv  /usr/lib/openoffice/program/openintro_ubuntu.bmp /usr/lib/openoffice/program/openintro_ubuntu.bmp_BAK
```

3) Set your own splash:
```
sudo cp <image>.bmp /usr/lib/openoffice/program/openintro_ubuntu.bmp
```

---

