---
title: "How to avoid long EFI wait before GRUB without Mac OS X install disc?"
date: 2012-01-27
forum: Apple Hardware Users
---

### Post by yngens on 2012-01-27
I have successfully installed Ubuntu 10.04.3 Server LTS on my Apple MacPro. Everything seems to be working just fine, except one tiny problem - it boots too slowly. 

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) says: 

> Avoid long EFI wait before GRUB
If your Macbook spends 30 seconds with "white screen" before GRUB shows, try booting from your Mac OS X install disc, select language, then click Utilities->Terminal, and enter:

bless --device /dev/disk0s1 --setBoot --legacy

Assuming that the bootloader is on sda1, otherwise /dev/disk0s2 if it's on sda2, etc.

[https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB](https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB)

But the problem in my case is that I do not have Mac OS X install disc. I wonder is there any other way to avoid this long EFI wait before GRUB?

---

### Post by yngens on 2012-01-28
bump. please anybody.

---

### Post by johnmurrayvi on 2012-02-01
Do you still have OS X installed on a partition?

---

