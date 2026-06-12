---
title: "monitor,video card not detected"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by stlcoptony on 2007-05-22
I am trying to install ubuntu 7.04 on my desktop for the first time. The live CD worked fine as did the installation. However when i rebooted, it failed to start the X server. It says that my video card and monitor are not detected. It is an Nvidia Geforce 6600 Verto card and a Samsung Syncmaster 940 BW monitor. I am extremely interested in trying ubuntu and would appreciate any help you can provide


thanks

---

### Post by S15_88 on 2007-05-22
after it gives u the error u get the command line interface correct?  If so type:

sudo dpkg-reconfigure xserver-xorg

and it will set u on a muti step path to configuring ur monitor and screen resolution and so on, then reboot.

---

### Post by stlcoptony on 2007-05-22
thanks, you are a life saver!!

---

