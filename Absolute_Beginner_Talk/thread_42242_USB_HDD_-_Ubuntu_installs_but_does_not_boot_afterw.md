---
title: "USB HDD - Ubuntu installs but does not boot afterwards"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by Alan on 2005-06-16
Dear All,

I hope you are all well.

I have just installed a Linux OS for the first time in my life. It is Ubuntu 5.04. The HDD I used for the installation was WD 800JB (Western Digital 80GB with 8MB cache). The disk is in an external case and is conntected to the mainboard via USB. The Ubuntu installation script had no problems finding the externally connected HDD.

The installation went smoothly but after re-booting the Ubuntu does not start. The error message says:

[B]pivot_root : No such file or directory /sbin/init : 428 : cannot open dev/console : no such file
kernel panic - not syncing : Attemptedto kill init![/B]

I think that kernel must not recognize the usb hdd :( Am I assuming right?

USB HDD 2.0 support in BIOS is enabled
MoBo: Soltek SL75-FRN2-L
RAM: 512Geil + 512 Kingston

Booting Devices:

CD-ROM //empty
USB-HDD // the WD hdd with Ubuntu installed on it
HDD0 // (120GB Samsung SP1213N) with 3 NTFS patritions and Win2K PRO SP4

Has anyone got a solution that will make Ubuntu work? I CANNOT remove the HDD from the case because the hdd has an almost-broken power supply PIN (in the connector) and I fear it will broke off when I try unplugging the power supply cable form the HDD.

---

### Post by adrian440 on 2005-06-17
Here's my guess:

The means of accessing usb HDDs is provided by a module, when it should be compiled into the kernel. I'm not sure of this, but it sounds like a problem I had once. I had the main filesystem of linux set to reiser the reiser filesystem, but when I compiled a new kernel, I only had reiser support as a loadable module, not compiled in. And so the kernel would panic upon boot.

So if I were you I suppose I would hunt down the details of the default kernel. It might be a problem fixable with grub (the boot loader), or it might be more troublesome. I think grub can be configured to tell the kernel to load modules, but I'm not sure.

---

### Post by morficus on 2005-06-18
I am having the same prob. and I found this link:
[http://ubuntuforums.org/showpost.php?p=42546&postcount=14](http://ubuntuforums.org/showpost.php?p=42546&postcount=14) 

havne't tried it yet.. but it seems like it could work.

---

