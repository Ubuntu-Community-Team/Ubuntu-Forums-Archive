---
title: "GParted confused about my HFS+ partition"
date: 2013-04-25
forum: Apple Hardware Users
---

### Post by SwedishWings on 2013-04-25
Maybe some one can help me out?

I have an internal drive in my MBP5,2 with a few partitions. One is a HFS+ partition with journaling disabled used for sharing data between Linux and OSX. After a lot of trying, i cant make GParted recognize the partition (see attached image). However, the partition mounts properly (R/W) and it shows up when i use parted CLI:
```
mike@MacBookPro:~/Desktop$ sudo parted -l
Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      20.5kB  210MB  210MB   fat32           EFI                   boot
 2      210MB   304GB  304GB   hfs+            Macintosh
 3      305GB   329GB  23.6GB  ext3
 4      329GB   372GB  43.0GB  ext4
 5      372GB   414GB  41.8GB  ext4
 6      414GB   493GB  79.6GB  hfsx            Share     **<--------- THIS PARTITION**
 7      493GB   500GB  6698MB  linux-swap(v1)  Apple_HFS_Untitled_2

```

I have tried to format the partition in both OSX and GParted, but GParted can't see it after i disable journaling from OSX.

Any ideas?

---

### Post by SwedishWings on 2013-04-25
I filed a bug report, if anyone else is interested, look at [https://bugzilla.gnome.org/show_bug.cgi?id=698876](https://bugzilla.gnome.org/show_bug.cgi?id=698876) 

The guys handling GParted are very responsive, Kudos!

---

