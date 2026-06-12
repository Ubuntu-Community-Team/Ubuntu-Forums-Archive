---
title: "Grub Error 17"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by dooglex on 2007-12-07
I was using vista on my dual boot system with gutsy and i lost all user input but could see hardisk activity going on, i waited half an hour but still no luck so hard to hard reset it and since the reboot when i turn the PC on i get grub error 17.

Vista is instaled on first sata disk, ubuntu on another sata disk and grub is in the MBR.

Can i recover my vista/ubuntu setup or do i have to format and start again. 

I can boot a live CD but cannot mount the drive (not that i really understand how to) and cannot see how to do a checkdesk or the like on an NTFS partition.

Thanks

---

### Post by HDave on 2007-12-08
OK -- I had this problem too at one point.

Sounds like you used the live CD to install Ubuntu on an external drive, yes?  If so, then here's the deal:

1) Even though you installed Ubuntu on the external drive, the install puts GRUB on the internal drive.
2) If the external drive is not plugged in GRUB throws and error.
3) if you want to fix your internal drive, you need to repair the Master Boot Record (MBR).  Find a windows CD and boot from that.  Use the recovery console to execute the fixmbr command.

Check out these threads for more help:

[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/")

Good luck.

---

### Post by dooglex on 2007-12-12
vista was installed on my first drive (sda1) and ubuntu on a second hardisk sdb, i managed to restore the vista boot loader and load vista, and can browse my ubuntu from the livecd by mounting it.

I tried to restore it using some instructions that said, like those,
sudo grub
find grub/boot/stage1
root (hd2,0) - my ubuntu partition
setup (hd0) - to my mbr

But when i restart it hasnt touched the mbr at all and it still boots straight back to vista!

---

### Post by bumanie on 2007-12-12
Could you please post the output of 
sudo fdisk -lu
Someone may be able to help if there is more information.
Also a copy of sudo gedit /boot/grub/menu.lst would be helpful

---

### Post by dooglex on 2007-12-13
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93af2a20

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1           16065   586099394   293041665    f  W95 Ext'd (LBA)
/dev/hdb5           16128   586099394   293041633+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7648ee81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488392703   244195328    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48a348a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    40467734    20233836   83  Linux
/dev/sdb2        40467735   135395819    47464042+   7  HPFS/NTFS
/dev/sdb3       149838255   156296384     3229065    5  Extended
/dev/sdb5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b88f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   781417664   390708801    7  HPFS/NTFS


Thanks for your help

---

