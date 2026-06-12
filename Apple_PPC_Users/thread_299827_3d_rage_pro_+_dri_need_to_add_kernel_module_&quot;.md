---
title: "3d rage pro + dri: need to add kernel module &quot;mach64&quot;"
date: 2006-11-14
forum: Apple PPC Users
---

### Post by iomicifikko on 2006-11-14
Hi all, i just installed ubuntu Edgy on my old imac g3 333mhz tray-loading 160mb ram, with a 3d rage pro 215gp. 
For video I'm using mesa drivers, but i'm not able to enable dri/3d support. According to Xorg.0.log, it can't find mach64 module (needed for rage cards -not rage128 type-). I used modprobe command to load mach64 module and as expected returned me an error: there is not mach64 in the kernel.

Now i have read a few guides on adding mach64 kernel module but all use packages from [http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots). they are "i386" packages so i think i cant use with my ppc hardware. the only way seems to be via SVC (is that right?) but i dunno what i need and how to make the process.

Anyone can help me about it (or find another possible solution)?

thanks all

---

### Post by cimi on 2006-11-18
I have your same problem pls help ;)

---

