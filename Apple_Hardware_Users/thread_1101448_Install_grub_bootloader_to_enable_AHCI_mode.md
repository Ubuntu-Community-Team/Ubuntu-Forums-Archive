---
title: "Install grub bootloader to enable AHCI mode"
date: 2009-03-20
forum: Apple Hardware Users
---

### Post by XMaster1 on 2009-03-20
HiHo,

I am having problems with the installation of the grub bootloader on a partition of my internal hard disk. I am not able to find the three required files which I have located here /boot/grub/... using 'find' in grub. Here is a screenshot showing the problem.

Thanks in advance for your help.

Best regards,
X.

---

### Post by cyberdork33 on 2009-03-20
> **XMaster1 said:**
> HiHo,

I am having problems with the installation of the grub bootloader on a partition of my internal hard disk. I am not able to find the three required files which I have located here /boot/grub/... using 'find' in grub. Here is a screenshot showing the problem.

Thanks in advance for your help.

Best regards,
X.
you have the msftres flag on that partition. that may be part of the problem, and I don't know that gparted has been fixed so that you can remove it.

---

### Post by XMaster1 on 2009-03-20
> **cyberdork33 said:**
> you have the msftres flag on that partition. that may be part of the problem, and I don't know that gparted has been fixed so that you can remove it.

Okay, I tried the 'boot' flag but same thing here… :(

---

### Post by cyberdork33 on 2009-03-20
> **XMaster1 said:**
> Okay, I tried the 'boot' flag but same thing here… :(
well that is not really any better. you really shouldn't mess with the flags as it can screw up other things... Make sure you can boot into OSX now after doing that.

---

### Post by XMaster1 on 2009-03-20
> **cyberdork33 said:**
> well that is not really any better. you really shouldn't mess with the flags as it can screw up other things... Make sure you can boot into OSX now after doing that.

I removed the Mac OS X hard disk before doing that.

---

### Post by cyberdork33 on 2009-03-20
> **XMaster1 said:**
> I removed the Mac OS X hard disk before doing that.
OH, that makes a big difference. You have multiple drives...

Are you on a Mac Pro or are you trying to use an external drive?

---

### Post by XMaster1 on 2009-03-20
> **cyberdork33 said:**
> OH, that makes a big difference. You have multiple drives...

Are you on a Mac Pro or are you trying to use an external drive?

When booting OS X I have four disks in my Mac Pro. During experiments I am using just one disk - the Windows Vista Boot Camp. So the 100 MB partition is on my internal disk.

---

### Post by cyberdork33 on 2009-03-20
> **XMaster1 said:**
> When booting OS X I have four disks in my Mac Pro. During experiments I am using just one disk - the Windows Vista Boot Camp. So the 100 MB partition is on my internal disk.
ok then, a couple of things.

a. You need to make sure to sync the partition tables on the drive that you are installing GRUB onto since it needs that information to properly identify partitions.

b. There is some "weirdness" when using multiple hard drives, as the Mac seems to think whatever drive that you use to move into "legacy OS" mode is the primary hard drive. The effects of this are not well documented.

[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

You might have better luck trying to boot directly with EFI...

[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

It's gonna be a few minutes (maybe an hour) before I can post back again.

---

