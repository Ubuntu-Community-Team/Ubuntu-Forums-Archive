---
title: "Nvidia Driver / Nividia Kernel Mismatch"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by savage.stoo on 2007-06-11
hello

OK, still very new to linux and ubuntu so please bear with me.

Have recently updated the drivers for my Nvidia 8600GT though envy and then manually configured them in Xorg which was fine. 

Now my kernel has been updated and Xorg is complaining that I have a API mismatch, that my Nvidia driver 100.14.09 and Nvidia kernel do not match.

Is there a way round this? 
Do need to keep my kernel up to date? 
Do I need to re-install my drivers?

All help appreciated.

---

### Post by EndPerform on 2007-06-11
You need to reinstall the drivers again.  When the drivers are installed, they are built against the current version of the kernel.  If the version changes, you get the issue you see.  This will occur when a kernel update occurs, which isn't too often, really.  Unfortunately, there's no way around driver re-installation, and yes, I would recommend keeping the kernel up to date.  Hope this helps.

---

### Post by lazyart on 2007-06-11
when you boot into ubuntu and get that message it will dump you into a command line.  Log in, then do```
sudo apt-get install nvidia-glx-new
```Once installed, reboot and you should be in the clear.

---

### Post by Sockerdrickan on 2007-06-11
Or get the new one released a few days ago (With support for your GPU) and do the script

GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALL, JUST PRESS ENTER ALL THE TIME

sudo /etc/init.d/gdm start

---

