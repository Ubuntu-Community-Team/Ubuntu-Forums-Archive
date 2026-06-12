---
title: "Access to a partition"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by modestgeek on 2006-02-18
I made a 42GB partition for all my media, its FAT32. I can access it in windows no problem, but when in Ubuntu, i cant see a thing. The only folders/drives/etc that I can see is the NTFS partition I installed windows on. How can I view this drive?

---

### Post by jjf on 2006-02-18
This should help you:

[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by modestgeek on 2006-02-18
Thanks, thats a big help!  :)

---

### Post by aysiu on 2006-02-18
See the fourth link of my signature. The first example is NTFS, but then there's an explanation of how to adapt it for FAT32.

---

### Post by orlox on 2006-02-18
I'd recommend the diskmounter script. That did the work for me...

[https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions)

---

