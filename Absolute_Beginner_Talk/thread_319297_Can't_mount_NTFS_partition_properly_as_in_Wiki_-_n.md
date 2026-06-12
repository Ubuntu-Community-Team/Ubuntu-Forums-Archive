---
title: "Can't mount NTFS partition properly as in Wiki - nothing there?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by intrepidus on 2006-12-15
I followed the Wiki on how to add read only access to an NTFS drive, but I've hit a bump.

When I mount the drive, a 250gb WD SATA with one partition (/dev/sdc1) to /media/music, and navigate there, it's empty of all real data. All that's listed is AUTOEXEC.BAT, IO.SYS, $RECYCLE.BIN, System Volume Information, CONFIG.SYS, MSDOS.SYS, RECYCLER.

This drive is NOT where Windows is located. There are no hidden partitions or anything of the like. The drive is used to store my music and video files, that's it. I do not have any problems mounting my 500gb WD SATA that I used for all my files. It mounts fine, with the same command, except /dev/sdd1 instead of /dev/sdc1. I can read just fine.

What's going on here?

---

### Post by taurus on 2006-12-15
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by meng on 2006-12-15
Can I just clarify what you've tried already?
I assume you typed a command like:
sudo mount -t ntfs /dev/sdc1 /media/music

is that correct?
And (I realize we are going back to basics here) what is the output of:
fdisk -l

---

### Post by intrepidus on 2006-12-15
> **taurus said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

As I said, I've already followed the Wiki. This is just the same information from another source. Same problem.

> **meng said:**
> Can I just clarify what you've tried already?
I assume you typed a command like:
sudo mount -t ntfs /dev/sdc1 /media/music

is that correct?
And (I realize we are going back to basics here) what is the output of:
fdisk -l

I'm using:
sudo mount /dev/sdc1 /media/music -t ntfs -o nls=utf8,umask=0222
to mount the drive.

fdisk -l output:
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23564   189277798+  83  Linux
/dev/sda2           23565       24321     6080602+   5  Extended
/dev/sda5           23565       24321     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sdb2            1021        1657     5116702+   7  HPFS/NTFS
/dev/sdb3            1658       24321   182048580    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001   42  SFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001   42  SFS

Disk /dev/sde: 60.0 GB, 60011642368 bytes
255 heads, 63 sectors/track, 7295 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          14      112423+   0  Empty
/dev/sde2              15        7296    58492665    b  W95 FAT32

```

---

### Post by bodhi.zazen on 2006-12-15
```
sudo mkdir /media/music
sudo mount -t ntfs /dev/sdc1 /media/music -o nls=utf8
```

Post any error messages.

---

### Post by intrepidus on 2006-12-15
> **bodhi.zazen said:**
> ```
sudo mkdir /media/music
sudo mount -t ntfs /dev/sdc1 /media/music -o nls=utf8
```

Post any error messages.

The only error with that, of course, is that a non-superuser can't read it. It -still- doesn't work. See above, for the same reason. Only shows those files.

---

### Post by bodhi.zazen on 2006-12-15
So the partition mounts, it is just a permissions problem :)

```
sudo umount /media/music
sudo mount -t ntfs /dev/sdc1 /media/music -o nls=utf8,umask=222
```

Post any error message :)

---

### Post by intrepidus on 2006-12-15
> **bodhi.zazen said:**
> So the partition mounts, it is just a permissions problem :)

```
sudo umount /media/music
sudo mount -t ntfs /dev/sdc1 /media/music -o nls=utf8,umask=222
```

Post any error message :)

No, you turned it into a permissions problem. I've already tried this - please read my first post. It is **not** a permissions problem, *your* fix to it made it a permissions issue because you forgot the umask.

---

### Post by bodhi.zazen on 2006-12-15
I read your title "Can't mount NTFS partition properly" so I mounted it properly ;)

So sorry if I mis read your problem. Perhaps "lost data" would be better description, no ?

If your data is "not there" it sounds as if it has been lost.

Can you read the data from windows? Did you format the drive somehow ?

---

### Post by intrepidus on 2006-12-18
I've solved this.

Linux can/can't see the Windows' pagefile, which I wasn't aware of. And by can/can't, I mean it doesn't list its existence via fdisk -l, but knows it's there nonetheless. Thus, it was mounting the pagefile as /dev/sdc1, even though it listed that as the larger of the two partitions (thus the one with data on it), and the desired partition as /dev/sdc2. Odd issue.

---

