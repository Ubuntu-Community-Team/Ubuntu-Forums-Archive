---
title: "HP g6s new install stalls while loading (unless I use i915.modeset=0)"
date: 2011-12-26
forum: Any Other OS
---

### Post by Cavalier1723 on 2011-12-26
its an hp g6s with intel i5 and intel hd graphics 3000.

Anyone have a any thoughts on this? I had to use i915.modeset=0 to install it and now I have to use this to get it boot. It hangs right after a "check battery" state message. 

I looked through dmesg for a hint as to what might be going on but can't find much. 

Any thoughts as to where I might look for hints about what is going on?

(i'm actually using linux mint but hoping someone with original ubuntu might have experienced this as well)

thanks for any help or suggestions!

---

### Post by wolfen69 on 2011-12-26
Which version of mint? I have the same chipsets in my laptop, and the latest ubuntu installed no problem. Be aware this may get moved to Other OS talk.

---

### Post by Cavalier1723 on 2011-12-26
its mint 12. I figured it would happen with ubuntu as well but maybe thats not the case.

Did a little more research.

potentially relevant portions of xorg log:

successful with i915.modeset=0:
[    13.446] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.446] (II) Loading sub module "vbe"
[    13.446] (II) LoadModule: "vbe"
[    13.463] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    13.489] (II) Module vbe: vendor="X.Org Foundation"
[    13.489] 	compiled for 1.10.4, module version = 1.1.0
[    13.489] 	ABI class: X.Org Video Driver, version 10.0
[    13.489] (II) Loading sub module "int10"
[    13.489] (II) LoadModule: "int10"
[    13.489] (II) Loading /usr/lib/xorg/modules/libint10.so
[    13.499] (II) Module int10: vendor="X.Org Foundation"
[    13.499] 	compiled for 1.10.4, module version = 1.0.0
[    13.499] 	ABI class: X.Org Video Driver, version 10.0

unsuccessful with defaulting to modeset=1:

[    12.293] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.293] vesa: Ignoring device with a bound kernel driver
[    12.293] (WW) Falling back to old probe method for vesa
[    12.293] (II) UnloadModule: "vesa"
[    12.293] (II) Unloading vesa
[    12.293] (EE) Screen(s) found, but none have a usable configuration.
[    12.293] 
Fatal server error     ....

---

### Post by Perfect Storm on 2011-12-27
Moved to Other OS/Distro Talk.

---

