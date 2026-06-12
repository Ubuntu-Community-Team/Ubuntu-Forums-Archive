---
title: "[driver] Set - up nVidia 6800 GO"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Raan03 on 2006-12-31
Hi,

I have trouble with setting up my display driver... Can somebody advice me? I installed the drivers from tweakers.net [[Link](http://tweakers.net/meuktracker/14285/nVidia-Linux-Display-Driver-1.0-9631.html)]

I went to the terminal and stopped succesfull the gdm; it installs very well without any kinds of error (except that he had to compile; but I have the headers and he did compile it succesfully ;)). But when I restart my computer; he has trouble to start the Xserver because he couldn 't find any matching configuration (or so). I know from the past that Windows also had problems with recognizing my nVidia 6800 GO; so had to manually force him to install the drivers... :S Also, he likes to complain that there is an API mismatch (or so) but I don 't think that 's the main problem

(nvidia installer log)
```
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86 (version: 1.0-9631) is
   now complete.

```

(X log)
```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

```

I am running Ubuntu 6.10 (Linux raan03-laptop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux) on an Alienware laptop m5700

Ow, before I forget. I am running ubuntu as my first Linux OS since December 26th, so if you could be so kind to help me in a way I can understand :D

Thanks alot
( + happy new year )

---

### Post by taurus on 2006-12-31
Try booting into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by tseliot on 2006-12-31
> **Raan03 said:**
> Also, he likes to complain that there is an API mismatch (or so) but I don 't think that 's the main problem
That can be the main problem ;)

Try envy, it should solve your problems:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

