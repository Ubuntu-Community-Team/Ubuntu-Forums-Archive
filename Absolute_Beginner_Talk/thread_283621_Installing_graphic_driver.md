---
title: "Installing graphic driver"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by schyffe on 2006-10-24
Hi, I just installed ubuntu and now I'd like to install my gfx drivers. I have a Leadtek WinFast PX7900 GS TDH graphic card, but I have no clue how to install the drivers. I can't find any tutorial either, I'd really appreciate if anyone could point me how to do this.

---

### Post by dbd on 2006-10-24
Your card uses an Nvidia chipset, so you need to install the nvidia drivers, see here for how:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by schyffe on 2006-10-24
I tried installing both the normal and later the legacy driver, but when I restart X, I get an error message saying it can't load.

---

### Post by bulldog on 2006-10-24
Well remove the legacy drivers and install nvidia-glx don't think your card is on the legacy list.

Then change the driver from "nv" into "nvidia" in your xorg.conf.

---

### Post by darthcoder on 2006-10-24
Or you can try to search for installing automatix2 and after installing automatix2, you can install the drivers for Nvidia by clicking the checkbox in the miscellaneous>nvidia drivers checkbox and clicking next(simple!,thats what I did!!).

---

### Post by schyffe on 2006-10-24
Allright, I'll give it a shot darthcoder, I've already tried what bulldog suggested but it didn't work.

---

### Post by bulldog on 2006-10-24
Installing your drivers with automatix will not work if you have drivers installed.

Why isn't it working?
What's the error?

Try```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` if you get xserver fault.

---

### Post by schyffe on 2006-10-24
Well I lost the original xorg.conf and couldn't restore, so I'm gonna re-install ubuntu tomorrow and try again. Thanks for all the tips, I hope it'll work tomorrow.

---

### Post by myflugel on 2006-10-24
hey im a total noob in ubuntu but i had the same problem and i followed this guide and it worked [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by schyffe on 2006-10-26
I just installed ubuntu 6.10 and I had the same problem. It says it doesn't find screen. I have a syncmaster 910T... I guess there is a logfile somewhere, should I include it here?

---

### Post by schyffe on 2006-10-26
Here is the log file.

---

### Post by gothic3n on 2006-10-30
hi
 im also a noob at Linux, i have a tnt2 nvidia card with ubuntu 6.10. i followed the instructions above and i think i installed everything correctly, the nvidia splash screen shows up at the beginning. but when i use glxinfo | grep rendering to check if hardware rendering is on i get a bunch of strings like the one below:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


was my installation successful?

---

