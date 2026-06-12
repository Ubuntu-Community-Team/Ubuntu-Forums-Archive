---
title: "vista + ubuntu 7.04"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by preciousnightmare on 2007-09-05
So I've been surfing around the forums and google for thorough instructions on installing ubuntu in a new laptop with vista and even found this site [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first). But after searching through peoples problems most are related to vista not booting after installing ubuntu and the vista bootloader failing to function... Does anyone have any ideas on how to prevent this from happening? Or if there are other instructions out there for installing ubuntu with vista that came from a new laptop? also if it does happen to me, is the recovery disk good enough to remedy my Vista? I dont have a Vista cd. Just the 2 recovery disk that came with this HP laptop. Thanks.

---

### Post by wolfen69 on 2007-09-05
yes, the recovery disks will work perfectly.

---

### Post by por100pre1 on 2007-09-05
Do everything as shown in that guide but:

At step 7 (the last step before install) click Advanced.

Select to install GRUB in the Ubuntu partition, like this:
(hd0,1) if you have only the Vista partition,
(hd0,2) if you have the Vista partition and a Vista Recovery Partition or just two partitions.

(If you are unsure about how many partitions you have to count them with Gparted.)

Install and Reboot. You'll login into Vista (Ubuntu will appear missing)

Use Easy BCD to add Ubuntu to Vista's Bootloader.

Hope this helps. :)

This method won't replace Vista's Bootloader so it's safer in a Windows perspective.

---

