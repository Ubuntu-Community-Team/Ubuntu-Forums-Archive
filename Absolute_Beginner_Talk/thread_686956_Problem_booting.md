---
title: "Problem booting"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by mcy782 on 2008-02-03
I'm new to Ubuntu. Just installed from the desktop CD with the first option to partition part of the drive with Windows still on it. I followed the defaults and everything seemed okay. However, when I boot up without the CD, I get a blank screen with "grub" in the upper right of the screen and a flashing curser nest to "grub." Nothing happens. I thought I was going to get a choice of which OS to boot. Any help would be appreciated. Thanks.

---

### Post by overdrank on 2008-02-03
> **mcy782 said:**
> I'm new to Ubuntu. Just installed from the desktop CD with the first option to partition part of the drive with Windows still on it. I followed the defaults and everything seemed okay. However, when I boot up without the CD, I get a blank screen with "grub" in the upper right of the screen and a flashing curser nest to "grub." Nothing happens. I thought I was going to get a choice of which OS to boot. Any help would be appreciated. Thanks.

HI and welcome, you may want to boot the live cd and in the terminal located under applications, accessories use the command ```
sudo fdisk -l

``` that is a small L.
Example
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3890    31246393+  83  Linux
/dev/sda2            3891       38889   281129467+   5  Extended
/dev/sda5            3891       16638   102398278+   b  W95 FAT32
/dev/sda6           16639       16893     2048256   82  Linux swap / Solaris

 This will let you make sure that the ubuntu and windows partition are still intact. Then you can use this link to maybe reinstall grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hopefully this will correct the issues.

---

### Post by mcy782 on 2008-02-03
Thanks. I'll give it a try.

---

