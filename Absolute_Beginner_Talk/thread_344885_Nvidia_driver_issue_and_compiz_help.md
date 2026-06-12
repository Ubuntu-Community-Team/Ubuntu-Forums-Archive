---
title: "Nvidia driver issue and compiz help"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by letitsnow on 2007-01-23
i have been trying to install compiz for a couple of days now, i got to the point where i could turn the GL desktop on and the title bars would disappear, i did a lot of searching to try and fix this and found Envy. i gave it a try and when i would reboot it would fail loading the driver. it said something about not being able to load the GLX module. i tried reinstalling the driver i used before with [this]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION") guide. it still gives the same error message. 

i am using the "nv" driver right now.

i'm using Edgy.

i'm not overly worried about compiz right now, i just want the right driver.
Thanks for any help.

---

### Post by pizzutz on 2007-01-23
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

should help.

---

### Post by letitsnow on 2007-01-23
same errors
```
Failed to load /usr/lib/xorg/modules/libglx.so
Failed to load module "glx"
Could not open /lib/modules/2.6.17-10-generic/volatile/nvidia.ko no such file or directory
```

---

### Post by pizzutz on 2007-01-23
check your /etc/X11/xorg.conf file.  

Does it still have nv listed under the device section as the driver?  if so, change it to nvidia and reboot.

---

### Post by letitsnow on 2007-01-23
it only gives me problems when i have nvidia listed as the driver. i installed this driver before and it worked great, i think envy changed something else.

---

### Post by letitsnow on 2007-01-24
i uninstalled everything using envy and synaptic, then reinstalled using envy. now i only get the error:

Failed to load Nvidia kernel module.

when i try to use nvidia as the driver

---

### Post by lamego on 2007-01-24
On the terminal, type "dmesg"
And check the output for the driver errors.

---

### Post by letitsnow on 2007-01-24
is that after the xserver failed to start?

---

### Post by letitsnow on 2007-01-24
i did something, i don't remember what but now all i get is a black screen. i'm just going to reinstall ubuntu.:(

---

### Post by letitsnow on 2007-01-25
reinstalled, tried envy again and it worked GREAT!! installed Beryl without a hitch and it ROCKS!!! runs perfectly.
my system:
p3 933mhz
Asus P3V4x mobo
1gig ram
Nvidia MX440 64mb

---

