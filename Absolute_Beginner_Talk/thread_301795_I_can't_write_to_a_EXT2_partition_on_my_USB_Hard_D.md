---
title: "I can't write to a EXT2 partition on my USB Hard Drive"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by accel on 2006-11-17
I've a 250GB Maxtor USB Hard Drive. I have formatted the drive
using Gparted into 2 partitions (1 EXT2 and 1 FAT32 partition)

Now the (auto)mounted EXT2 tells me that I can not copy/move files
to it because I'm not the owner ](*,) 
I'm logged in as a normal user and
only the root can copy/move files to the EXT2 part of the USB disk drive.

The FAT32 partition did get R/W access.

I've read somewhere that mounted USB devices (i.e. Flash drives, HDD) **always get** read/write access.
Can somebody tell me how to solve this.
BTW: I'm running Edgy

---

### Post by Average Joe on 2006-11-17
I think you should mount the partition with the right permissions for yourself. You could try to edit your /etc/fstab file. In this file, find the line where you mount your ext3 partition, and change "defaults" into "defaults,uid=1000,gid=1000,fmask=0133,dmask=0022".

Here I assumed that use have user id 1000, which is default for the first created user. This will give you read and write permission for yourself, and only read permission to others.

Then type: > sudo mount -a and it should work.

P.S. With FAT32 partitions everybody has read and write access, because FAT32 does not support file permissions at all.

---

### Post by taurus on 2006-11-17
I assume you mount your drives with /etc/fstab so let's have a look at it!

```
cat /etc/fstab
```

---

