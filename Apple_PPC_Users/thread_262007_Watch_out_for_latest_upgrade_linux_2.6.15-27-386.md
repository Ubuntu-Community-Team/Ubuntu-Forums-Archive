---
title: "Watch out for latest upgrade linux 2.6.15-27-386"
date: 2006-09-21
forum: Apple PPC Users
---

### Post by goneskiing on 2006-09-21
Apparently I am not the only one with a boot failure after upgrading with the latest linux upgrade - see warnings on desktop forum 

What is going on with quality control ?

---

### Post by stmiller on 2006-09-21
Yee-ouch that sucks. I'm using my own compiled kernel and don't follow the ubuntu kernel updates. But yeah this is pretty bad! Wish they would test it before uploading it to the update servers.

---

### Post by mrfelker on 2006-09-21
I haven't experienced boot problems yet with the newest kernel (running software RAID 5) but shuting down or reboot the screen displays, apparently harmless video strangeness (white boxes covering log and others).  Could this be  realated.  Guess we may find out at the next  kernel upgrade.

---

### Post by cneil on 2006-09-21
In my computer is seemed that hardware acceleration just stopped.  Glxgears worked, but it slowed down to only a few frames per second.  When I scrolled in a web brower, the screen flickered.  

The new kernel did have some new features for my Broadcomm wireless card, but other than that everything else ran much worse.  XGL compiz stopped working properly.  I'd post some error messages, but I'm not sure which ones are relevant.  I'm using the old kernel and everything is working find.  

I've said it in another post, by my graphics card is an ATI x600.  Maybe someone will come up with a solution.

---

### Post by calvinthomas on 2006-09-21
The Kernel upgrade worked fine for me, I always compile the latest driver for my ati card from the wiki on it. I had to compile it again after the kernel update (which you always have to) and then everything worked perfectly. I am using xgl/compiz with no problems at all, my graphics card is an x700 mobility

Calv

---

### Post by frigaut on 2006-09-21
cneil: I have exactly the same problem. I have a macbook pro, and can't make fglrx (the ATI driver) work anymore. It seems to compile OK, but then a lsmod does not return any fglrx module. also, trying to load by hand gives:

poliahu:~/Desktop% sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.15-26-686/misc/fglrx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
poliahu:~/Desktop% dmesg | grep fglrx
[...]
[17215086.400000] fglrx: disagrees about version of symbol boot_cpu_data
[17215086.400000] fglrx: Unknown symbol boot_cpu_data
poliahu:~/Desktop% 

The Xorg.0.log gives some indication:
[...]
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************
(II) fglrx(0): FBADPhys: 0x80000000 FBMappedSize: 0x0ffe0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1472 x 7288
(WW) fglrx(0): XVideo not supported without DRI enabled

even though there is no error (EE) per se, this doesn't sound normal (about DRI).

Anyone experiencing the same (beside cneil)?
Solution or work around?
Thanks!

---

### Post by BLTicklemonster on 2006-09-21
For once, I'm not normal. I rebooted to recovery, ran envy so my nvidia would work, and hit the desktop, rebooted to k7 and viola, no problem.

---

