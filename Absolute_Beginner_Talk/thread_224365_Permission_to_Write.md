---
title: "Permission to Write?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-07-27
Ok...so iv had some trouble getting access to my other drives...but finally figured out how to unmount them, and remount them properly so that i had access...but while i can access the drive...i still cant write to it...so...someone helpo me out please...i need to be able to write to my other drives...

---

### Post by Clay85 on 2006-07-27
I'm not sure about multipled hard drives, but when I need to read, write, execute for owner group and others I type

sudo chmod -R 777 <foldername>

-R makes it recurrent, so it will make the folder you named and all files and folders in it 777 (read, write, & execute for owner, group, & others)

Hope this is what you're looking for.

---

### Post by ovimunt on 2006-07-27
If your other drives are NTFS then it's not advisable to access them for writing! NTFS writing support is still only experimental in Ubuntu and is not recommended.

However, if you're up for it, you could convert your NTFS drives to FAT32 and then you could access them fully. Yet, converting NTFS to FAT32 is **NOT** recommended by any means!

---

### Post by Clay85 on 2006-07-27
Oh yeah I forgot to mention that too. I was so excited I actually knew something.

---

### Post by bladefallcon on 2006-07-27
> **ovimunt said:**
> If your other drives are NTFS then it's not advisable to access them for writing! NTFS writing support is still only experimental in Ubuntu and is not recommended.

However, if you're up for it, you could convert your NTFS drives to FAT32 and then you could access them fully. Yet, converting NTFS to FAT32 is **NOT** recommended by any means!

ok...then my question is this...if i need to save a file to one of those drives...How do i do it? If i dont have write capabilities, and it isnt recommended to aloow those capabilities...then how do i save to those drives?

---

### Post by OU812 on 2006-07-28
I don't know how you have your drives partitioned and I don't know what file systems you have on those partitions. Please do

sudo /sbin/fdisk -l

(in a terminal) and post the results. (This command will display all partitions on all detected hard drives with file system.) Then we can help you more. Thanks.

john

---

### Post by bladefallcon on 2006-07-28
```
blade@Blade2:~$ sudo /sbin/fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         522     4192933+   7  HPFS/NTFS
/dev/hda2             523        4864    34877115    f  W95 Ext'd (LBA)
/dev/hda5             523        4864    34877083+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1824    14651248+  83  Linux
/dev/hdb2            4263        4870     4883760   82  Linux swap / Solaris
/dev/hdb3            1825        4262    19583235   83  Linux

Partition table entries are not in disk order

```

---

### Post by bladefallcon on 2006-07-28
another question that I have...Is what if I wanted to move the installation of Linux from the drive it is on, to another...How would I go about doing that?

---

### Post by muep on 2006-07-28
At the moment, writing to those NTFS drives is very experimental and not recommended, it might cause data loss.

You could install an ext2/3 driver for Windows so that you could copy the files in Windows.

To the other question:
If you format the other drive into Ext3 or some other Linux filesystem, it is possible to just copy the installation to the other disk. This is also a bit hard, it is easiest to do from a livecd. After copying the boot loader and stuff needs to be reconfigured, too. And remember, the target partition loses its data when formatting.

---

### Post by bladefallcon on 2006-07-28
> **muep said:**
> At the moment, writing to those NTFS drives is very experimental and not recommended, it might cause data loss.

You could install an ext2/3 driver for Windows so that you could copy the files in Windows.


Could someone explain that for me then? I would like to do this..

---

