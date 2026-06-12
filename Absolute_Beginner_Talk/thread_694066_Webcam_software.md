---
title: "Webcam software?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-11
[http://www.logitech.com/index.cfm/435/281&cl=ca,en](http://www.logitech.com/index.cfm/435/281&cl=ca,en)
That's my webcam plus the drivers for Windows where do I get the linux ones, my cam is all plugged in.

---

### Post by spiderbatdad on 2008-02-11
you might try camorama from add/remove to see if your cam is readily available...or kopete. Most logitech cams work with video4linux no other drivers needed.

---

### Post by asmiller-ke6seh on 2008-02-11
If you have the correct edition, it is already supported. Go to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) and look at the listing of supported cams.

In TERMINAL, type the following:
> lsusb

look for your camera in the list for the vendor and product id. If your camera has a **product id **of **0x08a3**, **0x092c**, **0x092e**, or **0x092f **(the vendor id is 0x046d), then it should work right out of the box.

---

