---
title: "Grub unable to read IDE-0, serial # shows strange markings during POST"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by MindRiot on 2007-08-12
Hi.

I'm having issues with Grub.

Well, actually, I appear to be having issues with my primary hard drive.

Sometimes when I cold boot, the serial number shown in the POST for my first (IDE-0) hard drive has vertical dashes in place of most of the numbers. The dashes look like thick quote marks.  

When these markings appear, grub returns a read error.

I have tried to address this problem, by moving grub to a floppy, and this helps, because I can remove the floppy and boot directly into Windows XP, since Grub is no longer present in the MBR of the primary drive.  I have Ubuntu Feisty installed on a second, slave drive.

To fix the problem, I can sometimes run a Window's disk check on a restart, or sometimes I need to clear the CMOS, by pulling the battery.

I don't know whether this is virus effecting the primary hard drive, or something is corrupt in the primary hard drive.  However, I have no problem booting Windows XP, so I don't know why those marking show up in place of most of the serial numbers and why that would cause issues with Grub.

Does anyone know what's going on here and how I might be able to address it?

Thanks.

---

### Post by MindRiot on 2007-08-12
Sorry to bump the thread, but I'm hoping to gain some insight into what might be going on here.

---

