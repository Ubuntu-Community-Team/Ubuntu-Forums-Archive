---
title: "IBM Netvista A30P screen resolution"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by tiki28 on 2007-05-17
:lolflag:IBM Netvista A30P screen resolution
I am trying to install 7.04...............But It will not recognize the integrated video . So it is in 640x 480 only, and it will not allow me to change it.

Help?

---

### Post by heimo on 2007-05-17
Try reconfiguring Xorg using these instructions:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by tiki28 on 2007-05-17
That sounds like it would fix the problem. Except,  I can't  complete the install because I can't see the bottom of the screen.

Is there any way of install the intel viedio driver up front?

---

### Post by heimo on 2007-05-17
> **tiki28 said:**
> That sounds like it would fix the problem. Except,  I can't  complete the install because I can't see the bottom of the screen.


But you do see top half (or so) of the screen correctly? Drag windows with left ALT and left mouse button to see the rest... :) That's [a kludge]("http://en.wikipedia.org/wiki/Kludge"). Or you could try changing resolution with ctrl+alt+numpad plus or minus. Or dropping to virtual console using ctrl+alt+F2 before install, stopping Xorg with ```
sudo /etc/init.d/gdm stop
```changing driver line in /etc/X11/xorg.conf to vesa ```
sudo nano /etc/X11/xorg.conf
```and starting Xorg using ```
sudo /etc/init.d/gdm start
```

---

### Post by tiki28 on 2007-05-17
Thanks...............................................

---

