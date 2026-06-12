---
title: "nvidia problems with Ubuntustudio"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Tooch on 2008-02-06
I recently installed Gutsy and was able to start in safe graphics mode and had no problem getting the nvidia 6200 agp video card working. I installed ubuntustudio(on another harddrive) and it doesn't have this mode. After the splash screen (UbuntuStudio) the screen turns to a bunch of vertical lines and  I can't read or see whats going on. Is there a way to put this in safe graphics mode? or a way to install the driver? Thanks ahead of time.

---

### Post by Metaleks on 2008-02-06
Just download the driver from the nvidia website.  You can find that right here.

[http://www.nvidia.com/object/linux_display_ia32_169.09.html](http://www.nvidia.com/object/linux_display_ia32_169.09.html)

If that isn't your system, then find your system's driver.  For example, having a 64bit OS requires that you get the 64bit driver.  Google will help you here.

After you download it, put it in your home directory.  Then run
```
sudo apt-get install build-essential
```
to install build dependencies.  And then 
```
sudo /etc/init.d/gdm stop
```
to close xorg, since installing the driver requires it.  After this, assuming you're still in the same directory, run
```
sudo sh NVIDIA*
```
The * is a wildcard.  I'm assuming that you have only one file in your home directory starting with NVIDIA.  After that, follow the instructions to install.  To bring back the GUI, just do
```
sudo /etc/init.d/gdm start
```

---

