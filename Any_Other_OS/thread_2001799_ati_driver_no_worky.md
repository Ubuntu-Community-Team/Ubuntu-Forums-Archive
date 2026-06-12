---
title: "ati driver no worky"
date: 2012-06-11
forum: Any Other OS
---

### Post by NERDMAN! on 2012-06-11
i'm trying to enable the ati FGLRX graphics driver with post release updates,
and i get an error telling me to check the log, now unfortunately i dont speak jockey so can i get someone to translate this log file code for me?

```
2012-06-12 05:25:32,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:17755L> 100.000000
2012-06-12 05:25:37,642 DEBUG: install progress dpkg-exec 0.000000
2012-06-12 05:25:40,457 DEBUG: install progress libc6-i386 0.000000
2012-06-12 05:25:40,457 DEBUG: install progress libc6-i386 5.000000
2012-06-12 05:25:41,209 DEBUG: install progress libc6-i386 10.000000
2012-06-12 05:25:41,283 DEBUG: install progress libc6-i386 15.000000
2012-06-12 05:25:41,732 DEBUG: install progress lib32gcc1 15.000000
2012-06-12 05:25:41,833 DEBUG: install progress lib32gcc1 20.000000
2012-06-12 05:25:41,997 DEBUG: install progress lib32gcc1 25.000000
2012-06-12 05:25:42,081 DEBUG: install progress lib32gcc1 30.000000
2012-06-12 05:25:42,522 DEBUG: install progress fglrx-updates 30.000000
2012-06-12 05:25:42,623 DEBUG: install progress fglrx-updates 35.000000
2012-06-12 05:25:47,978 DEBUG: install progress fglrx-updates 40.000000
2012-06-12 05:25:48,077 DEBUG: install progress fglrx-updates 45.000000
2012-06-12 05:25:48,333 DEBUG: install progress fglrx-amdcccle-updates 45.000000
2012-06-12 05:25:48,434 DEBUG: install progress fglrx-amdcccle-updates 50.000000
2012-06-12 05:25:48,899 DEBUG: install progress fglrx-amdcccle-updates 55.000000
2012-06-12 05:25:48,984 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-06-12 05:25:49,091 DEBUG: install progress ureadahead 60.000000
2012-06-12 05:25:49,545 DEBUG: install progress dpkg-exec 60.000000
2012-06-12 05:25:49,616 DEBUG: install progress libc6-i386 60.000000
2012-06-12 05:25:49,825 DEBUG: install progress libc6-i386 65.000000
2012-06-12 05:25:49,996 DEBUG: install progress libc6-i386 70.000000
2012-06-12 05:25:50,231 DEBUG: install progress lib32gcc1 70.000000
2012-06-12 05:25:50,332 DEBUG: install progress lib32gcc1 75.000000
2012-06-12 05:25:50,512 DEBUG: install progress lib32gcc1 80.000000
2012-06-12 05:25:50,612 DEBUG: install progress fglrx-updates 80.000000
2012-06-12 05:25:50,963 DEBUG: install progress fglrx-updates 85.000000
2012-06-12 05:26:21,983 DEBUG: install progress fglrx-updates 90.000000
2012-06-12 05:26:22,453 DEBUG: install progress bamfdaemon 90.000000
2012-06-12 05:26:22,844 DEBUG: install progress fglrx-amdcccle-updates 90.000000
2012-06-12 05:26:22,979 DEBUG: install progress fglrx-amdcccle-updates 95.000000
2012-06-12 05:26:23,092 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-06-12 05:26:23,205 DEBUG: install progress libc-bin 100.000000
2012-06-12 05:26:23,542 DEBUG: install progress initramfs-tools 100.000000
2012-06-12 05:26:39,784 DEBUG: Selecting previously unselected package libc6-i386.
(Reading database ... 148014 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up libc6-i386 (2.15-0ubuntu10) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic
Building for architecture amd64
Building initial module for 3.2.0-23-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic/kernel/drivers/char/drm/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
Warning: No support for locale: en_AU.utf8

2012-06-12 05:26:40,066 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-06-12 05:27:05,114 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:05,115 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:05,148 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:05,149 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:50,753 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:50,754 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:50,787 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:50,788 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:50,811 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-06-12 05:27:50,866 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:50,866 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-12 05:27:50,926 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:50,927 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:50,960 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:50,960 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:51,039 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:51,040 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:51,073 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:51,073 DEBUG: fglrx_updates is not the alternative in use
2012-06-12 05:27:51,092 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-06-12 05:27:51,144 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-12 05:27:51,145 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
```

---

### Post by FishboyFive on 2012-06-11
from what i was told is that ubuntu does not support the drivers from AMD.com anymore and the ONLY focus is on the Opensource driver made by VMware or who ever.

the last two Ubuntu distros had said they have drivers for AMD but Both version made to the end user Have FAILED BIGTIME

the only way you are going to get AMD drivers to work is going back to winodws = its true

even if you do install the drivers and get them to load ubuntu uses 
Plymouth to boot the Distro and Plymouth does not support AMD at all not even a tad so your system will have one UGLY bootscreen and shut down with errors all over the place 

the driver may work but your os will looks like its Borked every time you boot it or shut it down 

its really sad linux still can not get real drivers to work 

one day i hopr before i get to old to use a pc i can install drivers and get real 3d support one day

---

### Post by bodhi.zazen on 2012-06-11
> **NERDMAN! said:**
> i'm trying to enable the ati FGLRX graphics driver with post release updates,
and i get an error telling me to check the log, now unfortunately i dont speak jockey so can i get someone to translate this log file code for me?

There are no errors in the code you posted.

Can you please post the exact error message you got ?

---

### Post by NERDMAN! on 2012-06-12
tis alright lads, managed to get it to work.
and for the record i probably should have mentioned this but i'm not using ubuntu, using mint 13, an ubuntu derivative. which works quite epicly now the drivers are working.

oh and bodhi it didnt give me an error, just said install failed check log.

---

### Post by bodhi.zazen on 2012-06-12
> **NERDMAN! said:**
> tis alright lads, managed to get it to work.
and for the record i probably should have mentioned this but i'm not using ubuntu, using mint 13, an ubuntu derivative. which works quite epicly now the drivers are working.

oh and bodhi it didnt give me an error, just said install failed check log.

Glad you got it resolved.

In the future, Mint is forked from Ubuntu, and you should use their forums, they are a very nice community there.

---

### Post by champdog on 2012-06-25
> **NERDMAN! said:**
> tis alright lads, managed to get it to work.
and for the record i probably should have mentioned this but i'm not using ubuntu, using mint 13, an ubuntu derivative. which works quite epicly now the drivers are working.

oh and bodhi it didnt give me an error, just said install failed check log.

Any chance you can post your solution for others like myself that are struggling with this?

---

