---
title: "Uninstalling then reinstalling Ubuntu."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by 4.9 on 2006-10-15
Yesterday I went out to by some CDs so I could write the disk at around 2x - 6x and now I need some help on what to do exactly. I made a list of things I need to do to fix Ubuntu and I need someone to tell me if I'm doing this right. Also, will deleting GRUB put Window's auto-boot back for a short time until I reinstall Ubuntu and GRUB?

[LIST]
[*]Download Ubuntu
[*]Burn to disk at 2x - 6x
[*]Put in GParted and delete the Ubuntu Partition
[*]Put in Ubuntu LiveCD
[*]Boot LiveCD
[*]Install Ubuntu from LiveCD
[*]Let Ubuntu finish the rest.
[/LIST].

---

### Post by taurus on 2006-10-15
You don't have to use gparted to delete Ubuntu partitions first before you install it.  Just tell the installer to format the partitions you want to install Ubuntu on and that would be good enough.

---

### Post by 4.9 on 2006-10-15
Would deleting the old Ubuntu Partition and Linux-Swap with GParted still work?

---

### Post by taurus on 2006-10-15
Yeah but why?  Do you plan to re-arrange your partitions around?  If you want to keep your partitions the way it is, then just format then while you install it.  But if you want to take an extra time to delete them, then go ahead...

---

### Post by 4.9 on 2006-10-15
Will deleting the partition cause Windows' auto boot to come back?

---

### Post by Bigbluecat on 2006-10-15
No.

Grub is sitting in you rmaster boot record. To eliminate this you need your Windows recovery disk to re-write the MBR. Be aware that when you do this you will lose the ability to boot to Ubuntu without some other help like Super Grub Disk.

Put your windows CD into the drive and boot. Type R when it tells you to get recovery mode.

Type

fixboot

then

fixmbr

I think it is quit to get our although it may be exit.

This should re-write your master boot record so you will be back to a PC as if it did not hve Ubuntu and cannot dual boot (except for the missing disk space of course)

---

