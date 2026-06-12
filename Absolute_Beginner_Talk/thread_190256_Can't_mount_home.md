---
title: "Can't mount /home"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by [S|G] on 2006-06-06
I'm clueless and desperate about this error. I booted my computer and I'm getting the following message:
```

fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda4
Could this be a zero-length partition?

```

The system then exits to a root command prompt. /dev/hda4 is my /home mount point, so I have a lot of important stuff in there. I've tried to mount /dev/hda4 manually, but got this:
```

mount: wrong fs type, bad option, bad superblock on /dev/hda4,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
I thought about running fsck, but I had the same error as on startup:
```

root@SnowGust:~# fsck /dev/hda4
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda4
Could this be a zero-length partition?

```

I then checked my partition list:
```

root@SnowGust:~# fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381    c  W95 FAT32 (LBA)
/dev/hda2            1306        1321      128520   83  Linux
/dev/hda3            1322       13510    97908142+  83  Linux
/dev/hda4           13511       14946    11534670    5  Extended
/dev/hda5           13511       14402     7164958+  83  Linux
/dev/hda6           14403       14810     3277228+  83  Linux
/dev/hda7           14811       14946     1092388+  82  Linux swap / Solaris

```
Shouldn't /dev/hda4 be reading as "Linux" since it is (or was, I'm not sure anymore) a EXT3 partition? Any idea about how can I recover my data on it?

Thanks a lot!

---

### Post by [S|G] on 2006-06-06
Just adding some information from dmesg:
```

[4294932.384000] EXT3-fs: unable to read superblock
[4296090.094000] attempt to access beyond end of device
[4296090.094000] hda4: rw=0, want=4, limit=2
[4296090.094000] EXT3-fs: unable to read superblock

```

---

### Post by anaconda on 2006-06-06
Well.
/dev/hda4 can't be your /home because it is not a partition!!

From the partition table it looks like you have 3 primary partitions hda1, hda2 and hda3
and an extended partition (hda4) which consists of logical drives hda5, hda6 and hda7.

SO hda4 isn't a real partition, it just says that the 4.th partition is divided to 3 parts. (hda5,6&7), which are used as partitions.

---

### Post by [S|G] on 2006-06-06
Yeah... that was exactly the problem... I installed windows and it seems it went a bit further than screwing my mbr... The partition order appearently changed as well. 

Thanks a lot... I didn't figure it in my desperation

---

### Post by anaconda on 2006-06-06
Have you made new partitions recently?

creating new partitions can change the numbering of the old partitions..  your home is propably one of the linux partitions. eg. hda2, hda3, hda5 or hda6..

---

### Post by CompShrink on 2006-06-06
It looks like Windows bumped down all the partition numbers, try opening /etc/fstab (a text file) in the command line, or in the recovery mode if you can get into it. Change the line that mentions /home to use /dev/hda5.

---

