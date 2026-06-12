---
title: "Grub error 2? Help"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Qazoo on 2008-04-06
Im unable to boot unbuntu (grub error 2)

I tried sudo grub
find /boot/grub/stage1
root (hd#,#)
setup (hd#)

and i still get the same error

-------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by twin_57103 on 2008-04-06
Have you tried [Super Grub]("http://supergrub.forjamari.linex.org/")?  It's got some good utilities for repairing GRUB errors.

---

### Post by Qazoo on 2008-04-06
Im trying but i dont understand how to do it. :\ im pretty newbie to this stuff

---

### Post by twin_57103 on 2008-04-06
Sorry I wasn't very specific.  What operating systems are you using?  I'm assuming Ubuntu (or another *buntu) and one version of Windows.   I assume you're gotten Super Grub downloaded and burned to a CD, then booted to it?

 I believe you'll want the option that is 
GRUB => MBR & !LINUX! (1)      AUTO
(or possibly Super Grub Disk (with help) )

I'm afraid that's as far as I can help - I haven't used Super Grub for this application before, just knew that it was capable of repairing GRUB errors.  I've used it in the past to restore a Windows MBR after I had to remove the drive that had GRUB (drive failed).  I hope that's enough to get you started, at least!

---

