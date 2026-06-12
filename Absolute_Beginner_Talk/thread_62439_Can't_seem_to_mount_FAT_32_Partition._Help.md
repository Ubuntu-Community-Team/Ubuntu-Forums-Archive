---
title: "Can't seem to mount FAT 32 Partition. Help?"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by ronlondre on 2005-09-04
Hi,

I have tried to mount the FAT32 partition while in KUBUNTU that I created with partition magic 8 when in winXP.  However, the "how to's" do not seem to be of much assistance.  I have only been successful locating a "how to" for mounting a FAT partition, which is not working for me when trying to mount my FAT32 Partition.  Please some advice for a newbie.

My partitions are located here:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       16430   106374397+   f  W95 Ext'd (LBA)
/dev/sda3           16431       18437    16121227+  83  Linux
/dev/sda4           18438       19457     8193150    c  W95 FAT32 (LBA)
/dev/sda5            3188       16297   105306043+   7  HPFS/NTFS
/dev/sda6           16298       16430     1068291   82  Linux swap / Solaris

---

### Post by xequence on 2005-09-04
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

I just mounted a fat32 partition today and that worked for me.

---

### Post by ronlondre on 2005-09-04
Thanks, I was entering /dev/hda4 instead of /dev/sda4. Sorry about using up space.

---

### Post by xequence on 2005-09-04
Its ok. Someone who doesent know the answer will search and find this topic. You have made the world a better place :)

---

### Post by dalani on 2005-09-04
thanks guys!Solved mine too.. :-P

---

