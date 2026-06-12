---
title: "Old world PPC macs (with the mac rom)"
date: 2005-03-06
forum: Apple PPC Users
---

### Post by ShadowRage on 2005-03-06
any chance oldworld macs like the 8500/120 will be supported?

---

### Post by ShadowRage on 2005-03-07
if not, will the current ppc base work with an old powermac?

---

### Post by DJ_Max on 2005-03-07
The main thing you have to worry about is the boot loader, you can't use the standard Yaboot, you have to use BootX or quik.
[http://ubuntuforums.org/showthread.php?t=15529](http://ubuntuforums.org/showthread.php?t=15529)

---

### Post by val1984 on 2005-03-07
[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

---

### Post by tjm on 2005-11-26
[Breezy Badger Supported Systems]("https://wiki.ubuntu.com//SupportedArchitectures")

BootX works with my beige G3 in order to boot into Linux. There is another way using miBoot, so you don't need an OS 9 on the machine but to set it up is a bit tricky.

I will try to setup my UMAX Pulsar S900 those days as a Ubuntu server and give the install a try. This machine is similar to Apple PowerMac 8500/9500 series. And hopefully the kernel will detect the drives connected to the UW-SCSI PCI controller. With Yellowdoglinx 3 it did not and needed another kernel by BenH.

I will give report about the results.

---

