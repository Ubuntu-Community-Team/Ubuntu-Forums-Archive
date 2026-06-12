---
title: "Nvidia geforce 2 driver"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-09-26
hi,

 my system is amd athlon xp 2000+ with nvidia geforce 2

 i want to know how can i install the drivers for nvidia geforce 2
 i need the command line for installing and setting up nvidia geforce 2..

---

### Post by Gotterdammerung on 2006-09-26
install nvidia drivers (nvidia-glx) from synaptic (or sudo apt-get install nvidia-glx), them edit /etc/X11/xorg.conf and change from nv to nvidia in video card device.

---

### Post by Gotterdammerung on 2006-09-26
More info here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

[https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting)

---

### Post by eggy1962 on 2007-07-19
trying to install but getting this message
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.28_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

yet the pc is connected to the internet ok
the card is a geforce 2 64mb

---

