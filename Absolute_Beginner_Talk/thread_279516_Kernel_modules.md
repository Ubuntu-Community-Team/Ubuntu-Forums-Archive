---
title: "Kernel modules"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by JaRoLLz on 2006-10-18
Dear all,

My real problems is with agpgart. I want to install i945gm drivers from an rpm package converted to deb with alien. But when i type:

sudo dpkg -i dri-i915_v1.1-20041218_i386.deb

it says that an error happens, and what caught my eye is that 

----
ERROR: AGPGART module did not compile


ERROR: AGPGART module did not compile - AGP module turned off in kernel ??


ERROR: Kernel modules did not compile
----

When finding through system documentation, i found modprobe, insmod, etc. But I'm totally blank. Anybody please help me. My laptop can't use opengl and 3d acceleration because of this. Even GLMatrix screensaver looks like slug.

Help needed :-|

---

### Post by elettronicha on 2006-10-18
Post the output of 'lsmod|grep agpgart'.

---

### Post by siliconeagle on 2006-11-02
i had a similar problem trying to install v1.8 of the Intel drivers which i just downloaded from the Intel site. i would say it a problem of not having the right source/header packages installed for the module to compile.

don't guess anyone has any ideas on what synaptic packages to install to compile this driver properly. 

the error was like this, except i am runnig the 2.6.15-27-686 kernel (as i need smp):-
```
(Reading database ... 113973 files and directories currently installed.)
Unpacking dri-intel (from intel.deb) ...
Setting up dri-intel (v1.8-20050729) ...


ERROR: AGPGART module did not compile
sed: can't read /lib/modules/2.6.15-26-386/build/.config: No such file or directory
sed: can't read /lib/modules/2.6.15-26-386/build/.config: No such file or directory


ERROR: AGPGART module did not compile
sed: can't read /lib/modules/2.6.15-26-386/build/.config: No such file or directory
sed: can't read /lib/modules/2.6.15-26-386/build/.config: No such file or directory


ERROR: Kernel modules did not compile
cp: cannot stat `drm/i915.ko': No such file or directory
Failed to install file /lib/modules/2.6.15-26-386/kernel/drivers/char/drm/i915.ko
cp: cannot stat `agpgart-2.0/intel-agp.ko': No such file or directory
Failed to install file /lib/modules/2.6.15-26-386/kernel/drivers/char/agp/intel-agp.ko
The installation of one or more files failed
```

---

