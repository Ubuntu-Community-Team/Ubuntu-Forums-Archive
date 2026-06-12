---
title: "Grub &amp; link loading with 2 HDD's"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by oygle on 2007-10-15
Two hard drives as follows ..

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002c46f

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9636    77401138+  83  Linux
/dev/sda2            9637        9729      747022+   5  Extended
/dev/sda5            9637        9729      746991   82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x239d4641

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         499     4008186    b  W95 FAT32
/dev/sdb2             500        2494    16024837+   f  W95 Ext'd (LBA)
/dev/sdb5             500        2494    16024806    b  W95 FAT32


Have Ubuntu 7.10 RC installed on the primary master, and Windows 95 installed on the primary slave.

Ubuntu works fine, it can even let me browse the 2 logical partitions on the W95 HDD.

But when I press ESC at GRUB during boot, it just hangs at the msg ..

> 
Starting up ...


I even modified the contents of /boot/grub/device.map , to add the W95 as 'hd1' as an extra line ..

> 
(hd0) /dev/sda
(hd1) /dev/sdb


but still can't boot to the W95 hard drive. I have seen some posts about doing the "map" command under GRUB, can that be done conditionally, like in the menu.lst file ?

Any clues please ?

---

### Post by oygle on 2007-10-16
The second post in the thread [How do I add Windows XP to Grub boot loader? - LinuxQuestions.org]("http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/") , shows the use of "map" in menu.lst , so I will give that a try.

It was from a post 2 years ago, so I hope it can still be done.  :)

---

### Post by oygle on 2007-10-16
Yes, adding the 2 "map" commands after the "title" command did it, was able to boot to W95 okay.

---

