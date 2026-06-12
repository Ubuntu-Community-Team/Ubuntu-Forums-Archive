---
title: "install the nvidia beta drivers gutsy?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by sc30317 on 2007-11-12
does anyone know how to install the nvidia beta drivers on gutsy? 

Thanks!

---

### Post by reckless2k2 on 2007-11-12
i'm just saying...i heard they are buggy and don't work with a lot of cards...especially the 8000 series.

---

### Post by sc30317 on 2007-11-12
I have A nvidia 5600 graphics card, and when I use the restricted drivers manager and install the restricted drivers for my card, When I restart, the computer stops before it gets to GDM

I figured that the NVIDIA binary drivers would fix this

When this happens, I can go into recovery mode, change the
driver  "nvidia"  line to
driver "nv"

and it will work, with no 3D rendering

Anyone know how to fix this?

---

### Post by sc30317 on 2007-11-12
pretty please?

---

### Post by reckless2k2 on 2007-11-13
well it sounds like not everything is loading correctly. are you installing the beta or standard nvidia? i don't know if you've got it running on the old kernel or new. if you upgraded kernels, then driver doesn't cross over. you have to --reinstall from command line. uninstall old along with restricted yadda.....then reinstall for the new kernel. 

i don't know if this is your problem but it might be. this subject is well documented in the community docs.

---

### Post by sc30317 on 2007-11-13
Yea, I couldn't find any documentation for it in gutsy tho.

---

### Post by SOULRiDER on 2007-11-13
How are you installing your drivers? Try doing
```
sudo aptitude install nvidia-glx
``` and then change your driver from nv to nvidia and restart your machine (or just xorg if you want)

---

### Post by Christmas on 2007-11-13
I have a Gigabyte GeForce FX 7600GS card and the drivers in Gutsy work fine, however I installed the driver from the official website ([http://www.nvidia.com](http://www.nvidia.com) and it works well. Maybe try to install that? ALT+CTRL+F1 to go in console, stop the X server ("sudo /etc/init.d/gdm stop"), make the driver executable, run it, then edit your /etc/X11/xorg.conf file to "nvidia" instead of "nv" and restart your X server. It should work.

---

