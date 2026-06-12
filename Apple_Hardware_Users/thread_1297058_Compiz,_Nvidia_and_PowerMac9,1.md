---
title: "Compiz, Nvidia and PowerMac9,1"
date: 2009-10-21
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-10-21
I have been trying to activate visual effects under the "visual effects" pane in "appearances". However, I get the following error:

"Desktop effects could not be enabled"

I have an Apple G5 PPC:

```
$ grep machine /proc/cpuinfo
machine      : PowerMac9,1
```

I am not sure what graphics card it uses, but I am pretty sure that it is an Nvidia graphics card.

I have checked and Compiz was installed by default when I installed Ubuntu.

/etc/X11/xorg.conf does not have any driver listed under the "Device" section.

Any ideas?

---

### Post by frog_pilot on 2009-10-21
there are no 3d drivers for nvidia for ppc-machines. only for ati cards there is one.

try this command to find out vendor and model of your graphics card

lspci | grep VGA

---

### Post by casbahdk on 2009-10-21
```
$ lspci | grep VGA
0000:f0:10.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200 Ultra] (rev a1)
```

---

### Post by frog_pilot on 2009-10-26
This means you own a nvidia 5200 card and thats why you will not get 3d desktop effects.

---

