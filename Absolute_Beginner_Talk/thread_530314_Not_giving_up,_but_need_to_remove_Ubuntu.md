---
title: "Not giving up, but need to remove Ubuntu"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-08-20
Hello,

I am currently dual-booting Windows XP and Ubuntu on a 30 GB hard drive.  15 GB to each.
I am not giving up on Ubuntu.  I just need to remove it from the hard drive for the time being.  I want to completely remove any trace of It ever being installed and use the entire 30GB for Windows.  Can someone please tell me the most efficient way of going about this?

---

### Post by LaRoza on 2007-08-20
> **ITdrummer said:**
> Hello,

I am currently dual-booting Windows XP and Ubuntu on a 30 GB hard drive.  15 GB to each.
I am not giving up on Ubuntu.  I just need to remove it from the hard drive for the time being.  I want to completely remove any trace of It ever being installed and use the entire 30GB for Windows.  Can someone please tell me the most efficient way of going about this?

0. Restore the MBR (use XP install disk, or Super Grub Disk)
1. Boot into Windows
2. Use Disk Management to delete the Linux partition(s) and resize the C: to fill the space.

---

### Post by kellemes on 2007-08-20
Reboot with Windows-disk, get into recovery console (forgot key, but you'll see) and type "fixmbr" (or type "help" for more options)

---

### Post by janga on 2007-08-20
I made a good experience with the gparted Live CD. You can wipe out your Ubuntu Partition and then resize your windows partition with that.

You can download it here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

However, if you have grub installed to MBR, you will need to restore the Windows XP Bootloader with your Windows CD in recovey mode.

edit: O.K, two people faster than me...
edit2 : @LaRoza, if he has XP Home Edition, he might not have the Disk Management Tools.

---

### Post by LaRoza on 2007-08-20
> **janga said:**
> 
However, if you have grub installed to MBR, you will need to restore the Windows XP Bootloader with your Windows CD in recovey mode.

The Super Grub Disk can also do this, and is easy to use.

---

