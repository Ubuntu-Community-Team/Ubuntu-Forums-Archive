---
title: "Booting Two Harddrives"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-04-14
There use to be a product called Trios that would let you select which harddrive to boot from before you turn on your computer.  Question is, is there anything like that out there now.  I have duel botted before but I like the idea of two harddrives.  Any help would be appreciated.

---

### Post by confused57 on 2007-04-14
> **Drifter said:**
> There use to be a product called Trios that would let you select which harddrive to boot from before you turn on your computer.  Question is, is there anything like that out there now.  I have duel botted before but I like the idea of two harddrives.  Any help would be appreciated.
You should be able to leave your bios set to boot first to the drive with grub installed to the mbr, then add entries to boot any OS on the same drive or a different drive.

---

### Post by nudnik on 2007-04-15
> **confused57 said:**
> You should be able to leave your bios set to boot first to the drive with grub installed to the mbr, then add entries to boot any OS on the same drive or a different drive.

Will this work with Vista?

---

### Post by confused57 on 2007-04-15
> **nudnik said:**
> Will this work with Vista?

Since I don't use Vista personally, I can't guarantee it'll work in every instance; however, I've read posts by other people who have successfully done so.

The biggest concern I've seen dualbooting with Vista is that new users attempt to resize their Vista partition using gparted with the live cd install...gparted doesn't currently support the new NTFS filesystem used by Vista.  The Vista partitioner should be used to resize the Vista partition, when freeing up space to install Ubuntu.

---

