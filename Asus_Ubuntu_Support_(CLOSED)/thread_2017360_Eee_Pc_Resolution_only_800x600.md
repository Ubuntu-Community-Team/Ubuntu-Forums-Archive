---
title: "Eee Pc Resolution only 800x600"
date: 2012-07-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by daniwaber on 2012-07-05
I have bought an Asus Eee Pc Netbook. I have windows 7 on it which works with 1024x600 max resolution which is enough. However when I try ubuntu 12.04 or 11.04 live usb, it shows max resolution as 800x600. I tried to change it with xrandr but no method has worked. I also added new mode by xrandr but it told me that the mode could not be applied when I selected.
Please help me!

---

### Post by daniwaber on 2012-07-06
Please help... I have not yet bought it...
If there is another linux which will work it is all right. But please help soon!

---

### Post by LonelyStar on 2012-07-06
I have installed Fedora 17 on my Asus r052c.
That works, but I would much prefer ubuntu.

---

### Post by LonelyStar on 2012-07-07
I got ubuntu working, but with a custom compiled kernel ...

---

### Post by OldAdamUser2 on 2012-08-29
Ubuntu 11.10 works perfectly on my Eee 900, but at times I have had the problem you describe when running other versions of Linux. Make sure that you have 915resolution.static in SYSTEM/usr/sbin. If you do have that, you might tried editing the boot parameters to include the command -- xvesa=1024x600x32. That assumes, of course, that you are willing to use xvesa.

I know how to do that in older versions of grub, but not in the current version. There must be a way.

There are also ways to drop out of the Ubuntu gui into a plain terminal and then using 915resolution to achieve the same thing after the computer has booted up. I don't recall the details.

---

### Post by Chris11 on 2012-09-01
I have a EeePc 1015 and any Ubuntu versn from 11.04 in advance works out of the box. Did you mad a fresh install ore do you run Ubuntu side by side"

check out this page 

[https://sites.google.com/site/mtrons/howtos/eeepc-1015pn#TOC-Gnome-Shell-Tweakshttp://]("https://sites.google.com/site/mtrons/howtos/eeepc-1015pn#TOC-Gnome-Shell-Tweakshttp://")

---

### Post by daniwaber on 2013-07-14
Hey everyone, thanks for your help. I finally found out that after I installed Ubuntu 13.04 through wubi, it works properly and the resolution is full at 1024x600. Thanks for help again.:D

---

