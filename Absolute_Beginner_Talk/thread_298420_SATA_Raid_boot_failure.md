---
title: "SATA Raid boot failure"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by AbyssNOLF on 2006-11-12
This might not necessarily be a topic concerning Ubuntu, but Ubuntu is the only linux distro I've used.  In any case, the problem is this:

I have two SATA drives I had in a RAID0 array on an old motherboard.  I ended up selling off that entire computer a while back, but I recently got a new motherboard that had SATA RAID support, except its by VIA instead of Sil.  In any case, whenever I boot from the LiveCD, I can install dmraid, mount, and access my old RAID array just fine.  However, whenever I try to boot into an Ubuntu installation on a separate hard drive, GRUB fails to load, usually hanging at "loading stage2.."  This is also the case when I attempt to boot into the Super Grub Disk cd in order to try and repair GRUB.  If I turn off my SATA hardware support in BIOS, however, everything works just fine., except I can't access the SATA drives anymore.

I have scoured the internet for many hours and I have attempted to follow various How-To's on setting up RAID and installing Ubuntu to RAID, or tutorials on fixing GRUB installations and so on, but I have not succeeded in anything.  It is my goal not to have to reformat my SATA drives, and I do not want to install Ubuntu to them (I have already done that on a separate drive), I just want to be able to mount the drives and access them.

Does anyone have any idea why the problem is occurring or how I could resolve the issue?  Why would booting the Ubuntu Live CD allow me access to the SATA RAID when I otherwise could not boot at all?  Any help would be appreciated.

BTW, I'm running on the amd64 architecture and therefore am using the amd64 software.  The hardware RAID support is by the vt8237 chip, and the raid firmware does not recognize that the two drives are already in a RAID array.

---

### Post by onlyconnect on 2007-07-31
Did you try the info here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Tim

---

