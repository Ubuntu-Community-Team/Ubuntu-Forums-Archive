---
title: "Gutsy installed on flash usb. Now T60 won't boot without flash drive"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by beech2000 on 2007-12-30
Hello,

Absolutely fell in love with Gutsy Gibbons ver. of Ubuntu while running from CD and decided to install on USB flash.

Now T60 will only give me the boot menu for XP pro with USB flash installed. 

Also when trying to boot to USB flash is says no operating system installed.

Everything works perfect while 8 meg usb flash is installed. I can boot to windows normally and Gutsy Gibbons runs normal. I can even access IBM restore OS on partition of HD.

I would like to be able to insert USB Flash drive to run Gutsy while retaining the T60's version of XP pro as normal.

Please help and thanks

Thanks

---

### Post by LaRoza on 2007-12-30
Get the Super Grub Disk, restore the Windows bootloader.

Boot from the Disk and go to Advanced->Windows (Advanced) I think it is the first option.

Apparently, you installed Grub to the MBR and it looks for Grub (which is on the flash drive).

Now, reinstall, but install Grub to the flash drive, not the hard drive.

---

### Post by beech2000 on 2007-12-30
Thanks for the quick reply.

Super Grub Disk?

Can you elaborate for me?

---

### Post by plucky on 2007-12-30
The **super grub disk** is used for repairing windows and linux bootloaders and can be downloaded from [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)


Download and burn to CD.This Cd is bootable.

Cheers

---

### Post by LaRoza on 2007-12-31
> **beech2000 said:**
> Thanks for the quick reply.

Super Grub Disk?

Can you elaborate for me?

Sorry, it is in the link in my sig.

---

