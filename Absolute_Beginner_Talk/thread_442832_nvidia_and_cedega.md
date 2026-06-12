---
title: "nvidia and cedega"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by perfect_cobalt on 2007-05-13
hey all. 

I'm a recent windows convert and i recently figured out how to install the drivers for my video card...or so i thought. 

i just finished installing Cedega and when it tried to auto detect my card all it could tell me was that i had 512mb of video ram. 

everything else seems to be working fine. the nvidia driver seems to be installed and i have access to the nvidia x server settings pannel and all that jazz. 

i have a 7950GTX if that makes any kind of difference.  

thanks! 

ps 
i installed ubuntu for the first time last night so... i'm a total n00b. TOTAL n00b. like, i found out what root was less an hour ago. that's how n00b i am. :p

---

### Post by eyelessfade on 2007-05-14
you need to install the nvidia-glx-new package. And make sure that it says  "Driver  "nvidia" in /etc/X11/xorg.conf under the device section.

---

### Post by perfect_cobalt on 2007-05-22
sorry for the late reply. (i've had ISP issues). so, i'ver already installed the glx-new package but when i put that into the terminal, i get: 

ben@zero-1six:~$ sudo bash
root@zero-1six:~# /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
root@zero-1six:~# 

why?!??!?!?!?!?

---

### Post by justin whitaker on 2007-05-22
> **perfect_cobalt said:**
> sorry for the late reply. (i've had ISP issues). so, i'ver already installed the glx-new package but when i put that into the terminal, i get: 

ben@zero-1six:~$ sudo bash
root@zero-1six:~# /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
root@zero-1six:~# 

why?!??!?!?!?!?

I think you need to become root first. 

su
password
gedit /etc/X11/xorg.conf

although if you are on Feisty, you could just use the restricted drivers manager to autoinstall/configure the Nvidia drivers.

---

### Post by perfect_cobalt on 2007-05-22
ohhhhhhhh! 

i though sudo bash would get me root. guess not. thanks. i'lltry it and report back

---

### Post by justin whitaker on 2007-05-22
> **perfect_cobalt said:**
> ohhhhhhhh! 

i though sudo bash would get me root. guess not. thanks. i'lltry it and report back

Sudo lets you act as root in many cases, but on kernel level stuff, you need to actually go the su route.

---

### Post by perfect_cobalt on 2007-05-23
ok, 

this is what my xorg.conf looks like: 

Section "Monitor"
    Identifier     "L203WT"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GTX]"
    Driver         "nvidia"
EndSection 

i still get this in Cedega: 

cpu: AMD Athlon(tm) 64 X2 Dual Core 3800+
cpu_ghz: 2.01
memory: 2012
[B][U]videocard_manufacturer: 
videocard_type: 
videocard_ram: 512
agp_aperture_size: 
videocard_driver_version: [/U][/B]
soundcard: NVidia CK804 with CMI9780 at 0xfebfd000, irq 2
soundcard_driver: ALSA Version 1.0.13
machine_bitness: 64
kernel: 2.6.20-15-generic
x_version: Xorg Version 7.2.0
distro: Debian 4.0
GUI version: 6.0

I'm not sure what's going on. 

what else could i be doing wrong?

---

