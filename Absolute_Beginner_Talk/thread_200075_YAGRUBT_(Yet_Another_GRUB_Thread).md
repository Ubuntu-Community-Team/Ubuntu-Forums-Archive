---
title: "YAGRUBT (Yet Another GRUB Thread)"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by muxecoid on 2006-06-19
I have 2 HDDs. Windows is on the slave disk. It's NTFS. Master disk is disabled during boottime via BIOS but works after boot. MBR is on the slave disk. I want to install Ubuntu to the first disk, but I want WinXP on Slave HDD to remain bootable. What needs to be done?

---

### Post by rai4shu2 on 2006-06-19
Unless you boot from a BIOS menu or from a bootable floppy/CD grub will need to overwrite the MBR. If you overwrite the MBR, you can then use grub to boot into Windows or some other OS.

---

