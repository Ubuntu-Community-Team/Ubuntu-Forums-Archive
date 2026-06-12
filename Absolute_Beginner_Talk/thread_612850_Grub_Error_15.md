---
title: "Grub: Error 15"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Eicca on 2007-11-14
Okay, so I tried today to get the pendrivelinux work. I followed the windows installation guide at [http://pendrivelinux.com](http://pendrivelinux.com) and everything went smoothly (except I don't know if I did the ext2 partition creating right) until I had to reboot. I pressed reboot and a few moments later, bang:

> Verifying DMI Pool Data .............
GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 15

I really hope that I can get this fixed, since I have a lot of stuff in my hard disks, that I need.

Also, is there an alternate booting software? I really don't like this, since I'm experiencing alot of errors and if something goes wrong, there is no way to easily edit the booting list.

---

### Post by Nano Geek on 2007-11-14
> **Eicca said:**
> Okay, so I tried today to get the pendrivelinux work. I followed the windows installation guide at [http://pendrivelinux.com](http://pendrivelinux.com) and everything went smoothly (except I don't know if I did the ext2 partition creating right) until I had to reboot. I pressed reboot and a few moments later, bang:



I really hope that I can get this fixed, since I have a lot of stuff in my hard disks, that I need.

Also, is there an alternate booting software? I really don't like this, since I'm experiencing alot of errors and if something goes wrong, there is no way to easily edit the booting list.[See if this works.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")

---

### Post by Eicca on 2007-11-14
Okay, so I followed a how to restore grub guide and the find /boot/grub/stage1 didnt give any results, so I tried hd 0,1 and hd 0,0 since I have 2 partitions and it is in one of those, and this is the result:

[I][COLOR="Sienna"]Error 17: Cannot mount selected partition
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found[/COLOR][/I]

Please help me! :S

---

### Post by Duck2006 on 2007-11-14
From the live cd in the terminal type

sudo fdisk -l

and post the output.

---

### Post by Nano Geek on 2007-11-14
Try the forth post in this thread.
[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

---

### Post by tech9 on 2007-11-14
> **Eicca said:**
> Okay, so I tried today to get the pendrivelinux work. I followed the windows installation guide at [http://pendrivelinux.com](http://pendrivelinux.com) and everything went smoothly (except I don't know if I did the ext2 partition creating right) until I had to reboot. I pressed reboot and a few moments later, bang:



I really hope that I can get this fixed, since I have a lot of stuff in my hard disks, that I need.

Also, is there an alternate booting software? I really don't like this, since I'm experiencing alot of errors and if something goes wrong, there is no way to easily edit the booting list.

Download SuperGrub Disk as an iso, burn it to disk and repair your grub loader...

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by Inxsible on 2007-11-14
you could also use the [super grub disk]("http://supergrub.forjamari.linex.org/") and rectify your grub.

---

### Post by Eicca on 2007-11-14
> **Inxsible said:**
> you could also use the [super grub disk]("http://supergrub.forjamari.linex.org/") and rectify your grub.

Okay, I'll try this. Thanks alot!

---

### Post by tech9 on 2007-11-14
no problem - good luck :)

---

