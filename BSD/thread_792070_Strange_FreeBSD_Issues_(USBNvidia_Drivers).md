---
title: "Strange FreeBSD Issues (USB/Nvidia Drivers)"
date: 2008-05-12
forum: BSD
---

### Post by chachawpi on 2008-05-12
I have used FreeBSD in the past with no problems.  I tried it out around 4.2, and used it as a primary desktop OS after Nvidia released their first GLX drivers.  I tried revisiting it recently, and it is giving me nothing but trouble.  See below:

1) When booting, if there is a USB hard drive attached I get an instant kernel panic right after it is detected.  

2) I can unplug my USB drive and the system will boot.  However, during boot my other USB devices (mouse/keyboard) drop connection and I have to unplug them and plug them back in to have them reactivate.

3) NVidia driver does not work for me.  I was able to boot into X using "nv" driver, but when I compiled nvidia-driver from ports and ran nvidia-xconfig, I get an error about "/dev/nvidiactl" not being found and X will not boot.  

This was with 7.0-RELEASE.  The same problems persist with PC-BSD 1.5.1 which is based on 6.3-RELEASE.  In fact, when I select the "nvidia" driver during the initial boot, my system hard locks when testing the screen.  I have no problems with Linux on this computer, and even Solaris works perfectly with the NVidia drivers and all attached USB devices.  Also, I am able to run "special" versions of OS X Leopard with no problems on this machine.  Only FreeBSD gives me these problems.  OpenBSD boots up normally.

My system specs are:

Gigabyte GA-EX38-DS4 Motherboard
Intel E6850 Core2Duo
XFX NVidia 8800 320MB GTS (G80)
4GB GeiL PC6400 DDR2
150GB WD Raptor

AHCI/SATA Native mode are enabled in BIOS.

Anybody have any ideas?

---

### Post by theonlyrealperson on 2008-06-23
I was having the same USB issues, which I still haven't resolved. One fix was to change the USB bios setting from "legacy", but then I couldn't use the USB keyboard to do anything until the operating system was loaded. (for example, you can no longer use it to get into bios or use grub). That did seem to fix the kernel panic problem, but it created another problem of having to have a second keyboard around to get into bios or use the bootloader. 

I am having an issue that I can't fix, that may be related. I am getting random kernel panics, that seem to be attributed to my Nvidia-based chipset in my motherboard. Sometimes it gets a panic on boot, sometimes it is after a while of usage. Problem is that 7.0 is the only kernel to support the newer Nvidia chipsets, 6.3 doesn't seem to want to see the nic or anything else.

---

