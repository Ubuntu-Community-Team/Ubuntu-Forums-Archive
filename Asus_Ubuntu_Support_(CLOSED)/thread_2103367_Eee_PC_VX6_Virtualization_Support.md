---
title: "Eee PC VX6 Virtualization Support???"
date: 2013-01-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by indigosunrise on 2013-01-10
Hey guys.

Despite the issues regarding video card support on this device I still continue to use a linux partition for majority of my work and windows for anything video heavy\windows network related for my studies. Ubuntu 12.04 Desktop 64bit host runs nice and quickly, 12.04 Server 32bit guest is slow.

However I'm trying to do a bunch of work using virtual machines and it's as slow as all hell... as in I'd have better speeds running an ubuntu virtual machine on my old dual-core laptop dedicating a bit under 2GB of memory as opposed to this one with 3.5GB of memory dedicated to the guest. 

Boot up into the bios and notice there is no VT-x or virtualization feature to enable. Can't install a guest 64bit Windows 7 despite using 64bit Ubuntu as host which leads me to think that this is CPU virtualization support related and my Ubuntu server 32 guest with LXDE as window manager is painfully slow as mentioned.

Anybody got advice to rectify this??? It's taking way longer to build my webstore prototype from scratch on guest machine then it should be taking, like maybe 10-15min to boot up and a 3min wait just to enable a drupal module on localhost.

Cheers guys.

Edit:
Output of : cat /proc/cpuinfo | grep flags


flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm

---

### Post by indigosunrise on 2013-01-10
.

---

