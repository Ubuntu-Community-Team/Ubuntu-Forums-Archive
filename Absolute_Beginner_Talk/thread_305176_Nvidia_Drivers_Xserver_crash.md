---
title: "Nvidia Drivers Xserver crash"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-22
Hello,
each time i update my nvidia 6600 drivers, i get xserver crash when i boot edgy. This happened since yesterday. 
Now i'm stuck to default drivers.
PLz help

---

### Post by taurus on 2006-11-22
How did you install nvidia driver for your graphic card?

---

### Post by That_Geek on 2006-11-22
go to the sudo nano /etc/X11/xorg.conf

make sure that the horizontal and vertical refresh rates are right, that was my problem when i installed the "nv" drivers

---

### Post by kiyometane on 2006-11-22
i installed the drivers using both automatix2.
i've also tried
"sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig "

this is the output of glxinfo
glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
kyo@kyo-desktop:~$

---

### Post by kiyometane on 2006-11-23
the output of "glxinfo" was different before experiencing craches.

---

### Post by Bachstelze on 2006-11-23
Oh yeah, Automatix is sooooo great...

If I were you, I'd do a clean reinstall and stay the hell away from that *abomination* forever.

---

### Post by kiyometane on 2006-11-23
i believe i dont need a fresh install after all the work i've done to optimise my system. There should be a way.

---

### Post by Bachstelze on 2006-11-23
Certainly there is a way but I think Automatix spoiled a lot of other stuff too so you'll experience more problems in the future... Anyway does this command output something ?

```
dpkg -l | grep restricted-modules
```

---

### Post by kiyometane on 2006-11-23
desktop:~$ dpkg -l | grep restricted-modules
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.6-1                           Non-free Linux 2.6.17 modules on x86_64 gene
ii  linux-restricted-modules-common            2.6.17.6-1                           Non-free Linux 2.6.17 modules helper script
ii  linux-restricted-modules-generic           2.6.17.10                            Restricted Linux modules for generic kernels

---

### Post by Bachstelze on 2006-11-23
Same thing with *nvidia-glx* instead of *restricted-modules* please.

---

### Post by kiyometane on 2006-11-23
desktop:~$ dpkg -l | grep nvidia-glx
ii  nvidia-glx                                 1.0.8776+2.6.17.6-1                  NVIDIA binary XFree86 4.x/X.Org driver

---

