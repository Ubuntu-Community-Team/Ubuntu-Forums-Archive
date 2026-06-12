---
title: "Nvidia glx driver will not"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Grunabfuhr on 2006-11-10
I have downloaded edgy 64 and 32 bit. Both have problems with my Nvidia 6600 with two monitors attached.  I can live with a certain amount of troubleshooting and for the 32 bit install disconnect one monitor not just depower but physically disconnect. In the end I get to the point where I am informed that I do not have the right driver for my Kernel even though I have followed the advice Here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I recive the message about the incorrect driver for the kernel after I type this in the terminal. 

sudo nvidia-glx-config enable

This lack of cooperation with nvidia both before and after the installation is disheartening.

---

### Post by rlozano on 2006-11-10
what do u have with lspci -v?

---

### Post by tzulberti on 2006-11-10
You should try:
sudo dpkg-reconfigure xserver-xorg...

When it ask you for a driver look por Nvidia...

---

### Post by Grunabfuhr on 2006-11-10
Well I tried the above no Joy.  Guess it is back to open Suse 10.1 which in my opinion has a much better installer and doesn't choke on Nvidia.  I did once manage to get the drivers installed on the live cd but since then nothing.  Somthing somewhere is broken if you look at the Ubuntu forums Nvidia is a thorn in the eye all over the place:-| .  I would like to try again but I will wait till the Nvidia issues have been resolved.

---

