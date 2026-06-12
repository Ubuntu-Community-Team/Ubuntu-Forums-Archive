---
title: "Installing drivers 4 USB-wireless w Atheros chip?"
date: 2011-11-12
forum: Any Other OS
---

### Post by taste of mint on 2011-11-12
I need help with installing drivers for my USB wireless adapter. I have spent the whole day trying to figure this out. I'm on Mint 9 which is based on 10.4 I think. Kernel 2.6.32-21-generic. And I have no internet connection (yet).

The chip is Atheros AR9271
```
idVendor                0x0cf3 Atheros Communications, Inc. 
idProduct             0xb002
```


I have read lots of threads about this and I have downloaded compat-wireless-2011-11-12.tar.bz2 
and the firmware ar9271.fw and htc_9271.fw and placed these in /lib/firmware
[B]
In the extracted compat-wireless-2011-11-12.tar.bz2folde[/B]r I have checked the following entries in the config file (config.mk) and they were already set up like this (as they apparantly should) but it doesn't look like this (4 in a row) it more one here and lots further down another one etc. am i looking in the right place?? Are there more kernel config files??

```
CONFIG_ATH_COMMON=m 
CONFIG_ATH9K_HW=m 
CONFIG_ATH9K_COMMON=m 
CONFIG_ATH9K_HTC=m 
```[FONT=monospace]



And thats where I'm at now.



I found another thread on another forum about this 
[http://www.ubnt.com/forum/showthread.php?t=22105](http://www.ubnt.com/forum/showthread.php?t=22105)

[/FONT]> WiFiStation Ext on Ubuntu 10.04

Information for drivers.
[http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc)

Downloads and some configuration information.
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Enable these options in your kernel config .config file.

     Code:
     CONFIG_ATH_COMMON=m CONFIG_ATH9K_HW=m CONFIG_ATH9K_COMMON=m CONFIG_ATH9K_HTC=m 
Recompile the kernel.

     Code:
     #lsusb -v   idVendor           0x0cf3 Atheros Communications, Inc. idProduct          0xb003 
download:
[http://wireless.kernel.org/download/...ss-2.6.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")
     Code:
     #locate hif_usb.c 
edit the hif_usb.c
add idVendor and idProduct

Run
     Code:
     #./scripts/driver-select ath9k_htc #make  #make install 
download the firmware and move ar9271.fw into /lib/firmware/         1 How do I recomplie the kernel?
2 Do I need to recompile the kernel?
3 I when I type locate hif_usb.c nothing happens. Where is this file located?

I have read [http://wireless.kernel.org/en/users/Download#Drivers](http://wireless.kernel.org/en/users/Download#Drivers)
[http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc)
[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

And I don't understand any of if.

Especially not
> **Requirements for bleeding edge**

 You need two things: 

[LIST]
[*]A Kernel >= 2.6.24
[*]Your kernel headers installed
[/LIST]
Please be *very sure* you have your kernel headers installed before reporting any sort of build issues with this package. This *usually* will mean having this symlink point to a valid directory with kernel headers in it: 

/lib/modules/`uname -r`/buildThe  exception to this is if you are building the package targeting a kernel  you are not running. Users doing this should read the [Building for external kernels]("http://wireless.kernel.org/en/users/Download#Building_for_external_kernels") section. 
Additionally,  the kernel you're building for needs a valid ".config" file, if it  isn't present compat will assume you have PCI, USB and PCMCIA built into  your kernel and if not, fail building. Whats a kernel header and how do I know if its installed?

Help

---

### Post by Cyclane on 2011-11-13
compiling a kernel is advanced stuff, I haven't done it myself yet but it's in my book.

It's important that your PWD is /usr/src/linux, so start with that. after that you can user make config or make menuconfig, the latter is supposed to be more user friendly.

```
sudo su
cd /usr/src/linux
make menuconfig

```

---

### Post by Perfect Storm on 2011-11-13
Moved to Other OS/Distro Talk.

---

### Post by taste of mint on 2011-11-14
Anyone? I'm trying the the Xubuntu 11.10 release on USB and still nothing, its 1,5 years newer than 10.4 so this should work from the start right?? 

How can I enable this USB wifi adapter on 11.10?

---

