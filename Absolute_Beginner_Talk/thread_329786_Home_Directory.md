---
title: "Home Directory"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by mohdridha on 2007-01-02
Is it wise to assign /home directory on FAT32 filesystem?

How to format a partition from Ext3 to Fat32 on Linux?
I tried using cfdisk to change the filesystem at /dev/hdb3/.
Is it enough just to change the type of filesystem to FAT32 in cfdisk mode?
Do I need to run  " mkdosfs -s 8 -F 32 /dev/hdb3" afterwards

Does it screw up my other partition (hdb5,hdb6,...) that holds this Ubuntu OS?

Thanks :-k

---

### Post by kidders on 2007-01-02
Hi there,

> **mohdridha said:**
> Is it wise to assign /home directory on FAT32 filesystem?No. Since FAT filesystems don't support ownership/permissions, there would be no way for you to keep users out of eachothers' files.

> **mohdridha said:**
> How to format a partition from Ext3 to Fat32 on Linux?Use mkfs.vfat. The original filesystem doesn't make much difference ... it's the one you want to switch to that counts.

> **mohdridha said:**
> I tried using cfdisk to change the filesystem at /dev/hdb3/.
Is it enough just to change the type of filesystem to FAT32 in cfdisk mode?
Do I need to run  " mkdosfs -s 8 -F 32 /dev/hdb3" afterwardscfdisk is a disk partitioner ... you don't need it.

> **mohdridha said:**
> Does it screw up my other partition (hdb5,hdb6,...) that holds this Ubuntu OS?Tinkering with your disk partitions can screw things up if you don't know what you're doing. Be careful!

---

### Post by Lord Illidan on 2007-01-02
why fat32?

If your purpose is to be able to read your files from Windows, there are some ext3 drivers for Windows out there.

---

### Post by mohdridha on 2007-01-02
oh..

At first thought, i want to be my /home to be in Fat32 so that its easier for me to read/write my files on Linux or Windows.. But after read all the replies, its not a wise thing to do.

Its all because of i'm not setting up my /home directory during the installation. That means my /home dir is on the same partition as / (/dev/hdb5)

```

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          89      714861   82  Linux swap / Solaris
/dev/hdb2              90        3276    25599577+  83  Linux
/dev/hdb3            3277        5826    20482875    c  W95 FAT32 (LBA)
/dev/hdb4            5827        7476    13253625    5  Extended
/dev/hdb5            5827        6081     2048256   83  Linux
/dev/hdb6            6082        6591     4096543+  83  Linux
/dev/hdb7            6592        7476     7108731   83  Linux
kapla@mrn:~$

```

See, my / which are on hdb5 is roughly 2GB. I'll run out of space soon.

[quote=kidders]

[quote=me]
I tried using cfdisk to change the filesystem at /dev/hdb3/.
Is it enough just to change the type of filesystem to FAT32 in cfdisk mode?
Do I need to run " mkdosfs -s 8 -F 32 /dev/hdb3" afterwards
[/quote]

cfdisk is a disk partitioner ... you don't need it.
[/quote]
Ok if you look above, my hdb3 is changing to Fat32 by using cfdisk only. And now i want to change it back to Ext3 back.. how?
Is it enough for to just used cfdisk again and choose the appropriate type for it (ext3)?
OR
skip the cfdisk thing and just put:
```

mkfs.ext3 /dev/hdb3

```

Sorry guys, just using Ubuntu for 3 weeks

---

### Post by kidders on 2007-01-02
Hey again,

Using cfdisk or fdisk to tweak partition flags doesn't actually change anything about a filesystem that may (or may not) be in it. You see, creating a filesystem is not the same thing as creating a partition to put a filesystem in. The tool for creating filesystems is called "mkfs".

Imo, if you have altered a partition's flags, you should probably reformat the filesystem it contains immediately, to avoid unpredictable behaviour. :-?

---

