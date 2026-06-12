---
title: "Can't See Drives"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by motion parallax on 2008-02-04
I booted my computer and suddenly my two partition icons have disappeared.  I rebooted and it's the same story.  I can't think of anything I've done recently to cause this.

Checked the Configuration Editor, and Drives Visible is checked.

Output of fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x311c2de8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020        7826    54677227+   6  FAT16
/dev/sda3            7827       14391    52733362+  83  Linux
/dev/sda4           14392       14593     1622565   82  Linux swap / Solaris

Contents of fstab

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=bbb589a3-2941-4170-aa00-69968f1438b4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=E8FCC1B416D9B5D2 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=76C02BD5C02B9A7F /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=10dcfd8d-7638-4681-8a81-5c9f3f6dee3d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

---

### Post by motion parallax on 2008-02-04
Is there some configuration file that controls this?  It seems like I can access the files on my linux drive, but now the Windows drive is totally invisible.

---

### Post by oedha on 2008-02-04
may i ?
i am just curious....did you shutdown your wiindows properly ( either shutdown or restart ) if it's not.....you can't see then since windows still locked that drives.
jump to windows....then restart.......are they still missing ?
~E~

---

### Post by motion parallax on 2008-02-04
That fixed it.  The last person to use my Windows partition had hibernated the OS.  

Thank you.  Very much appreciated.

I've got a lot more to learn about this dual booting :D

---

