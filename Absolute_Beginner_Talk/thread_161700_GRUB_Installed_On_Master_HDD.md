---
title: "GRUB Installed On Master HDD"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by m0o0oeh on 2006-04-17
hi guys,

When I installed Linux on my dual-boot, Linux installed GRUB onto my primary drive. I now need to reclaim some space, so I'm relegating Ubuntu to my server. 

What I want to know is... how can I uninstall Grub from my primary drive?

J

---

### Post by uteck on 2006-04-17
You can leave grub there if you want and just change it so XP is the default.  That is the easy lazy way. :P

Otherwise you have to get the windows boot loader installed.  If you have the MS  install disk, boot from it and enter the recovery console and type "fixmbr"  That should install the ntloader.  I am not sure if you can run this from XP command prompt or not, but you could try that if you can't find the install disk.

---

### Post by m0o0oeh on 2006-04-17
Right. Unfortunately money and HDD space constraints say that I have to lose Ubuntu for now. I need to re-format my Ubuntu HDD into a Windows (boo hiss) secondary HDD. If I do this, GRUB will throw a wetty. So, any other suggestions?

J

---

### Post by echo $USER on 2006-04-17
Just throw in a windows cd, boot into recovery mode, run fixmbr or fixboot.  That will delete grub and enable to windows boot loader.  Reboot.  Then boot into windows, go to computer management, disk manager, format the partition ubuntu is on with whatever file system you want FAT or NTFS.

---

