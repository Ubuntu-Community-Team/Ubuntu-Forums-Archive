---
title: "Booting Two OS's from a USB Drive"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Drezard on 2007-06-03
Okay, I have my 1GB USB Drive, I want to put both Ubuntu and one other small linux on it at the small time. Is it possible to do this without having to partition the drive in someway? And how would I do it (I just want the Live CD's on my USB).

Regards, Daniel

---

### Post by jfinkels on 2007-06-03
> **Drezard said:**
> Okay, I have my 1GB USB Drive, I want to put both Ubuntu and one other small linux on it at the small time. Is it possible to do this without having to partition the drive in someway? And how would I do it (I just want the Live CD's on my USB).

Regards, Daniel

You will probably have to install GRUB on your USB disk drive, then make sure your computer boots from USB disk before hard disk. Ubuntu should automatically install GRUB on the disk to which you choose to install it.

---

### Post by HeavyMetalMessiah on 2007-06-03
If you use Syslinux as the bootloader on the drive, just put two kernel sections in the configuration file.

EDIT: This actually might require partitioning, i haven't used a live distro in a long time.

---

