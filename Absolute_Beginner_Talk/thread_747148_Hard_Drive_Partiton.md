---
title: "Hard Drive Partiton"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by sherwoodwf on 2008-04-06
Hi

I'm new to Linux and Ubuntu. and i would like to be able to partition my hard drive so i can install windows on it as well so i still use some of the windows programs that i  may still like to use which don't run on Linux. 

i would like to know how to partition my hard drive and what i would have to use to do so and how to install that..

I'm sorry if this sounds like such a stupid question.

but thanks anyway

---

### Post by vanadium on 2008-04-06
The easiest procedure will be to first install Windows, using only a part of the drive. Then you can install Ubuntu and tell the installation program to use the free space on the drive. From that point, the Ubuntu installation program will automatically partition the free space. This way, it is all rather straightforward, although it is a good idea to take a look at the Ubuntu documentation first.

---

### Post by Hobo Joe on 2008-04-06
Either get the Gparted LiveCD, or boot into your Ubuntu LiveCD and open Gparted. Then, taking your biggest partition with the most free space, resize it to the desired size, then with the new empty space you've just created, make a new partition, and format it as NTFS.

Then, when you open the Windows install disk, just select the NTFS partition.

However, when you install Windows, it will wipe your boot sector and replace it with the Windows bootloader, meaning in order to get back into Ubuntu you will have to re-install grub. The easiest way to do this would be with the Super Grub Disk.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Duck2006 on 2008-04-06
For xp

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

For vista

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by sherwoodwf on 2008-04-06
ok thanks for the help... i will start to do it now

---

