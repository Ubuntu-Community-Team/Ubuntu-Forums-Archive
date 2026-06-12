---
title: "New Hard Drive"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by sarsippius on 2007-05-16
I have a Hard Drive I have set up as a slave IDE drive.  It is a FAT32 drive, formally connected to my Windows XP box.  There are some things on there I would like to have access to in Linux.

I used FAT32 because I know Linux can read that type of partition.  However, I don't know how to get Linux to see the drive since I've added.

Any help would be greatly appreciated!

Thanks!

---

### Post by JerMe on 2007-05-16
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

should get you started in the right direction.

---

### Post by confused57 on 2007-05-16
> **sarsippius said:**
> I have a Hard Drive I have set up as a slave IDE drive.  It is a FAT32 drive, formally connected to my Windows XP box.  There are some things on there I would like to have access to in Linux.

I used FAT32 because I know Linux can read that type of partition.  However, I don't know how to get Linux to see the drive since I've added.

Any help would be greatly appreciated!

Thanks!

Maybe this will help:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

or if you want to mount it permanently:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by Kirurgs on 2007-05-16
Linux can read/write ntfs as well, so I suggest converting that drive to ntfs...

---

