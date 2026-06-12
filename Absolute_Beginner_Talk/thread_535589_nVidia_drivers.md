---
title: "nVidia drivers"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Foxblood on 2007-08-26
Hi, I'm trying to install the NVidia drivers without success. I tried first using automatix and then tried apt-get. The error message I got is this:

et:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted nvidia-glx 1:1.0.963                              1+2.6.20.5-16.29 [4492kB]
Fetched 4492kB in 44s (102kB/s)
(Reading database ... 158996 files and directories currently installed.)
Removing nvidia-settings ...
Removing nvidia-xconfig ...
Selecting previously deselected package nvidia-glx.
(Reading database ... 158968 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb)                               ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xli                              bmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/                              nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-                              16.29_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know how to correct this? Thanks, in advance.

---

### Post by Jimmyfj on 2007-08-26
The nVidia restricted driver should be installed through System/Administration/Restricted Drivers Manager. 

I install the driver for my G-Force TI4200SE through that and never have issues with it this way.

---

### Post by Foxblood on 2007-08-26
> **Jimmyfj said:**
> The nVidia restricted driver should be installed through System/Administration/Restricted Drivers Manager. 

I install the driver for my G-Force TI4200SE through that and never have issues with it this way.

Sorry, I should have mentioned that it's Kubuntu I'm running.

---

### Post by Her Ghost on 2007-08-26
are you not able to install it through Add/Remove Programs (Adept installer)?

I use Kubuntu and I installed NVidia binary X.Org Driver through this method and got it working without too much trouble

---

### Post by alienexplorers on 2007-08-26
Try using the ENVY script to load your nvidia drivers.  You can access it at:
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by logos34 on 2007-08-26
> dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xli bmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/ nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'

I think this means it couldn't create a link because one already exists (leftover from nvidia-glx-new installed by Automatix??).  I wonder why mine is different because the libGL.so links point to 'libGL.so.1.0.9755' (I'm using the nvidia-glx-new) in the same dir, not to 'libGL.so.1.xlibmesa' in /usr/lib/nvidia 

See if Automatix2 will allow you to uninstall nvidia-glx-new.  Then either try

**sudo apt-get --fix-broken**

or in Adept
**edit>fix broken packages**

And/or try reinstalling using Add/Remove (nvidia-glx 9631 driver), or from the terminal

[B]sudo apt-get install nvidia-glx-new

sudo nvidia-glx-config enable [/B]


EDIT: or use Envy script as Alienexplorers suggested above.

---

### Post by Foxblood on 2007-08-28
Thanks to all who replied. The question is now moot since I hosed my Kubuntu. (No, I won't say how, it's too embarrasing). I think Logos34 was right on the money about something having been left behind by Automatix. Lesson learned. Tho' I never got the opportunity to try Alienexplorers' suggestion. Again, thank you all.

---

