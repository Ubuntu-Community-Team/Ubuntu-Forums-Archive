---
title: "Unknown Partition ?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-29
Here is a screenshot of my drive 1,Ubuntu is on drive 2 and working fine,and
I can access this "unknown" partition with Ubuntu. Also in Windows it does not see this partition,and I can't even access it with windows. Any ideas of how to fix? Thanks :-(

---

### Post by grizzly on 2006-07-29
what is the output of "fdisk -l /dev/hda"

and what exactly do you mean that you access this partiontion? and can you write / paste files into the partition? what is the mount point of the partition, as in  /media/xxx .

---

### Post by Drakkor on 2006-07-29
Here it is:

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1431    11494476    7  HPFS/NTFS
/dev/hda2            1432        9732    66677782+   f  W95 Ext'd (LBA)
/dev/hda5            1432        5861    35583943+   7  HPFS/NTFS
/dev/hda6            5862        9732    31093776    7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2631    21133476   83  Linux
/dev/hdb2            7113        7299     1502077+   f  W95 Ext'd (LBA)
/dev/hdb3            2632        7112    35993632+  83  Linux
/dev/hdb5            7113        7299     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order
drakkor@drakkor:~$

---

### Post by catlett on 2006-07-29
Ubuntu sees it as a NTFS partititon. Gparted recognises that filesystem type. If gparted labels it unknown there is an issue somewhere.
Do you have important data on it?
Reformatting the drive should take care of the issue.
If you have no data or you have copied it out to cd and now want to reformat, this is how to do it.
It is going to take a couple of steps because gparted won't format to ntfs. Open up gparted and right-click on the partition. When the option menu drops down, scroll to "format to". Another option menu slides out with filesystem types. Select fat32. Make sure to hit apply after you make your selection. Gparted doesn't do any of the actions until apply is selected.
Boot into windows. Go to "My Computer". The partition will have an icon next to your C drive, Right-click on the icon and an option menu drops down. Select "Format..." and a window opens. There will be a "file system" line, choose ntfs. That is it.
If you want it to be an ext3 or fat32, you do not have to boot into windows and format anything, but if you want ntfs windows will have to do the conversion after gparted makes the unknown fat32.

---

### Post by Drakkor on 2006-07-29
Yes,catlett,there are files I want to save on there. What about copying the files to Ubuntu,formatting the partition to fat32 and then could I put the files back on that and access them?  Thanks :o

---

### Post by catlett on 2006-07-29
That should work. If you can acces it from ubuntu now then you can copy them out, format and re-copy them back.
You might want to keep it fat32 afterwards so Ubuntu can write to it as well. The only downside to fat32 is it has a file size limit of 4gb. So you couldn't copy a dvd or other large file/iso to the partition.
But as you can see from this example if you keep it ntfs ubuntu can read and copy off of the partition without any problems.

---

### Post by Drakkor on 2006-07-29
Got it ! :p  Thanks, catlett

---

### Post by catlett on 2006-07-29
WOW! I guess you did have some data on that! Glad it worked. That would be alot of data to loose. Take care.

---

