---
title: "Nvidia Driver and xorg.conf"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2006-12-27
I have been trying to get the 3d graphics acceleration working for my graphics card (a nVidia Quadro NVS 110M) following the instructions on [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html), but every time I try the command in the third step I get “Error: unable to load nvidia kernel driver! Be sure to have installed the nvidia driver for your running kernel.”
I searched the forums here, thinking that someone else would have had a similar problem, but in the process of trying to fix things myself I have messed up the xorg.conf file on my computer (as it tells me it can't run the previous terminal command on the file anymore). Is there any way to reset the file to its original settings, or to reinstall Xserver (as xorg.conf seems to be a file from this application)?

Please help - I'm starting to think that Beryl is an unattainable goal for a new ubuntu user!

---

### Post by xfceslacker on 2006-12-27
Hi,
I think this will reset the xorg.conf file:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by usererror on 2007-02-07
Hi, that 2nd post with the re-configuration of X worked for me.  Once i ran that command I was able to enable 3D acceleration without any errors.  Hopefully it's really going to work now!  Thank you for your posts!

This is on Ubuntu 6.10

UPDATE: I Just rebooted and right after the ubuntu flash screen and before the GDM window, I see a nice flashy NVIDIA logo!  woo hoo!  3D Acceleration works!

---

