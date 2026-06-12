---
title: "Cleaning Boot Loadere"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by RealMabu on 2007-09-09
Hello I need some guidance through the process of cleaning my (not only multi-os but) multi-bootloader configuration!
I had XP.
Then installed MacOSX.
Then installed Vista.
Then Ubuntu.
Then reformatted Vista. :-)
Now my 2 hard drives look like this:
```
/dev/sda1 --> WinXP
/dev/sda2 --> NTFS Data
/dev/sdb1 --> MacOSX
/dev/sdb2 --> ext3 Data
/dev/sdb3 --> Ubuntu Feisty
/dev/sdb5 --> NTFS Data
/dev/sdb6 --> linux swap
```
Now  I have two bootloaders:
-GRUB is the first to start, I have manually adjusted its configuration so that it allows me to choose among Ubuntu (default), WinXP and MacOSX.
-If I choose WinXP from the above, I am linked to the now-defunct Vista Bootloader that allows me to choose among WinXP, Vista (???) and MacOSX again.
I needed such a configuration because I was not able to configure GRUB to boot MacOSX. I have to admit that reading at the grub manual was enough...
But now I want to get rid of Vista bootloader because when I choose XP I just want to boot XP!
I am afraid at doing /fixboot and /fixmbr stuff, because I dont want to wipe out the main MBR that activates GRUB.
Any help?

Thank you.

---

### Post by InGunsWeTrust on 2007-09-09
I would do a fixboot and fixmbr then start with a live cd and do a grub-install. There is no way I know of to manually remove the Vista loader. I think it is written directly to the first sector to the first partition.

---

### Post by RealMabu on 2007-09-11
Thanks for answering.
FIXBOOT was enough.
Just to be informative, here is how I solved.

1.boot from WinXP cdrom
2.choose R-Repair. There will be a scan of the windows installations present on your HDs.
3.choose the specific installation you want to repair. If you have multiple installations in different partitions, this step also identifies the partition.
4.log in as administrator. If you don't know the admin password, you will not be able to go through this step...
5.at the console prompt, type: FIXBOOT
6.after FIXBOOT has finished, type EXIT and reboot

The key is step 5.
It rebuilds the boot sector of the partition identified in step 3, without modifying the MBR.
So, rebooting, I still see GRUB's menu.
If I choose "Windows XP" i boot directly into windows: Vista loader has been wiped out.

If you wanted to wipe GRUB as well you should have issued a FIXMBR in addition to FIXBOOT as suggested by most forums here.

Regards.

---

