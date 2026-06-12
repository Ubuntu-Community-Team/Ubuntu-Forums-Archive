---
title: "Partition table entries not in disk order?"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by Kid G on 2006-01-23
Hi,
I have just installed Ubuntu on a dual partition with Windows XP (NTFS). I have an 80 GB harddrive of which i have allocated 20 Gb to Ubuntu. I also set up a 10 GB FAT32 partition.
I was trying to mount this FAT32 partition in Ubuntu using steps outlined [here]("http://users.bigpond.net.au/hermanzone/p10.htm"). However, when I run the "sudo fdisk -l" command in terminal I get the following output:

[INDENT]Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        6083    48829567+   7  HPFS/NTFS
/dev/hda3            8413        9732    10602900    5  Extended
/dev/hda4            6084        8412    18707692+  83  Linux
/dev/hda5            8517        9732     9767520    b  W95 FAT32
/dev/hda6            8413        8515      827284+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 254 MB, 254803968 bytes
128 heads, 5 sectors/track, 777 cylinders
Units = cylinders of 640 * 512 = 327680 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         778      248829+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(776, 127, 5) logical=(777, 76, 4)
[/INDENT]

When i run "sudo mkdir /media/hda5" to mount the FAT32 partition I get this message:

[INDENT]mkdir: cannot create directory `/media/hda5': File exists[/INDENT]

I think I may have followed steps out of order but hda5 is listed as having 14.3 Gb of memory along with hda2 and hda6.

Is there anyway I can get my partitions back in the correct order and mount the FAT32 partition in Ubuntu?

Thanks

---

### Post by Sutekh on 2006-01-23
Nothing wrong with partition table entries not in disc order.  It's not an error, just information letting you know how that the partitions on your disc are not in the order physically as they are numerically.  It's still a correct partition setup so don't sweat it.

As for the sudo mkdir /media/hda5 error, that command is to create a folder/directory for you to mount the FAT32 partition in.   The error is probably there because you already have that folder/directory on your filesystem.  

Try
```
cd /media/hda5
```
and see if you can change to the folder, then you'll know for sure if it is already there

Then try the next step in the guide
```
sudo mount /dev/hda5 /media/hda5 -t vfat -o umask=000
```
to mount the partition.

---

### Post by Kid G on 2006-01-23
Thanks,
 
Got it working now, panic over!

---

