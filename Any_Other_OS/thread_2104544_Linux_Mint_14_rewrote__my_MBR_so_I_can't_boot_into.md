---
title: "Linux Mint 14 rewrote  my MBR so I can't boot into win8"
date: 2013-01-13
forum: Any Other OS
---

### Post by yaw hide on 2013-01-13
hello!

I am trying to dual boot onto my desktop. My main os is win8 and i wanted to install linux mint 14 on the side. 

I ran self-boot repair and it said it was successful. So i restarted and there was no win8 option.

here is my pastebin generated URL:

paste2.org/p/2743107

Before i installed linux I had three partitions:
500 mb boot partition i think? something along those lines
200gb for win8
200gb for linux mint
rest unpartitioned space

I selected the option to install linux mint ALONGSIDE win8 and selected the 200gb partition for linux mint. BUT linux mint decided to rewrite my mbr haha

Any help would be highly appreciated

thanks in advance!

---

### Post by howefield on 2013-01-13
Thread moved to the "*Other OS/Distro Talk*" forum.

Link to Mint forums : [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by yaw hide on 2013-01-13
do linux mint people even know about the self-boot repair tool?

---

### Post by oldfred on 2013-01-13
Boot-Repair added syslinux which is a Windows boot loader to the MBR of sda. Are you booting sda from BIOS?

You only show a swap, but no Linux install? You labeled a NTFS partition as mint but Linux does not install to NTFS (unless wubi).

You do not want to have Windows 8 hibernated if dual booting.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by yaw hide on 2013-01-13
ok so win8 isn't hibernating

i created a partition called linux mint using the linux mint live cd so you would think they would default it to the right partition type, not ntfs

yes i am booting sda from bios.

---

### Post by oldfred on 2013-01-13
If you create partitions in advance you really do not have to format, as you can format during the manual install. But I usually format when I partition. Any auto install options will not use existing partitions, but will install to unallocated space or let you resize existing partitions to make unallocated, or totally overwrite your entire hard drive deleting everything.

---

