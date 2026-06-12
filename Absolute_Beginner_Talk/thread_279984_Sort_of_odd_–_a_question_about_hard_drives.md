---
title: "Sort of odd – a question about hard drives"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-10-18
I used <blush!> the Windows XP disk administration tool to delete some partitions for my Ubuntu install. Then I just let Ubuntu do its thing (it's much smarter than I am).

I was looking at the Disk Manager tool to see how much space I had used (System>Administration>Disk Manager)

hdb has 2 partitions. 1 is XP, the other is the restore partition. That is all straight forward.

hda on the other hand is sort of odd? The disk manager says:

Partition 1 is /media/windows98  (dev/hda1     file system: vfat size         7.87 gig )
Partition 2 is no mount point	      (dev/hda2     file system:  Extended3     7.87 gig)
Partition 3 is /root                         (dev/hda3     file system  Extended 3    20.67 gig)
Swap partition                               (dev/hda5  Memory swap                      933 meg)

My output from fdisk -l is:
```
 
dennisx@dennisx:~$ fdisk -l
dennisx@dennisx:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1028     8257378+   c  W95 FAT32 (LBA)
/dev/hda2            1029        2048     8193150    6  FAT16
/dev/hda3   *        2049        4746    21671685   83  Linux
/dev/hda4            4747        4865      955867+   5  Extended
/dev/hda5            4747        4865      955836   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
240 heads, 63 sectors/track, 5310 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         731     5526328+   b  W95 FAT32
/dev/hdb2   *         732        5310    34617240    7  HPFS/NTFS

```

So what is 
hda2
hda4
?

Are these empty partitions that I can give to Linux?

Thanks!

---

### Post by dbd on 2006-10-18
hda4 is the extended partition, and contians hda5, so you can't use that.

But hda2 looks just like a normal windows partition (strange that it is Fat 16 though), possibly put their by your PC's manufacturer? Mount it and have a look at whats there, if its not stuff you want to keep then you can change the filesystem and give it to linux :)

---

### Post by podunk on 2006-10-18
You wouldn't happen to know what the file mask for a fat 16 system would be do you?

---

### Post by gn2 on 2006-10-18
You say you deleted "some" partitions. Were there any left behind, or did you wipe the whole drive?

I see one of them is Fat16 ? Leftover from before perhaps?

I would advise wiping the drive totally clean using the gparted live CD then re-installing.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This may be of interest: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by podunk on 2006-10-18
Thank you both. :-)

I formated it to ext 3. Don't know what I'm going to do with it really - it's to small to be a dedicated /home. 

Maybe use it to store back ups? All I can think of anyway.

---

