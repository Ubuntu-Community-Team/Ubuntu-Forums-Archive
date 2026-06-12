---
title: "3D acceleration impossibly slow with 6200LE"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by volksolwagen57 on 2007-11-15
I changed up my hardware recently, backed up my data and installed XP and 7.10 x64 on a new sata hard drive. When I enable 3d acceleration by installing the nvidia-glx-new and restart. The toolbars on the top and bottom have missing buttons and there are black rectangles and the computer is extremely slow. Is the GeForce 6200LE supported by Ubuntu? If so what is my problem? Can anyone help me? Thank you for your time in advance.:confused:

---

### Post by Nano Geek on 2007-11-15
> **volksolwagen57 said:**
> I changed up my hardware recently, backed up my data and installed XP and 7.10 x64 on a new sata hard drive. When I enable 3d acceleration by installing the nvidia-glx-new and restart. The toolbars on the top and bottom have missing buttons and there are black rectangles and the computer is extremely slow. Is the GeForce 6200LE supported by Ubuntu? If so what is my problem? Can anyone help me? Thank you for your time in advance.:confused:I think the problem is that your card is not supported by the new Nivida driver. Try this:```
sudo apt-get remove --purge nvidia-glx-new && sudo reboot
```That will un-install the current driver and restart your computer. 
After it reboots, run this:```
sudo apt-get install nvidia-glx && sudo reboot
```Hopefully that will install the older driver that will work better on your computer.

---

