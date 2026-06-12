---
title: "Memory Swap File....necessary?"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-20
Ok, this is probably showing my newness to all of Linux: 

I recently cleaned off my 80GB drive and gave it a 70GB ext3 partition and a ~10GB FAT32 partition.  What I didn't do is give this drive a memory swap partition.  Is this necessary?  It's a completely seperate drive (/hdb) from the one Linux and XP are loaded onto (/hda). 

The reason I ask is b/c I'm not able to "Enable" it in Disks Manager.  I didn't mount it because I thought I would only need to mount an NTFS/XP partition, not an ext3 partition.  Am I wrong on this?  I was just thiniking it would recognize it as "useable" because its ext3.

---

### Post by jimrz on 2005-12-20
How much memory do you have installed? I have 512Mb, ubuntu built an 800 something swap on install, but it is rarely, if ever used.

---

### Post by Rackerz on 2005-12-20
Yeah, i have about 1.25GB RAM. Ubuntu hasn't even challenged that yet. If you have a high amount of memory (RAM) then a Swap might not really be necessary but its always good to have one.

---

### Post by Gandalf on 2005-12-20
If i understood you quite well, you have a swap partitio on /dev/hdb but it ain't mounted as swap right? if it's the case do the following:
Open /etc/fstab in your favorite editor
```

sudo gedit /etc/fstab

```

if there is not a swap entry (which is the case) you have to add it, it's easy, first we need to know on which partition lies the swap one
type
```

sudo fdisk -l /dev/hdb

```

you will get something like this
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         892     7164958+   b  W95 FAT32
/dev/hda2             893        8454    60741765    5  Extended
/dev/hda3   *        8455        9703    10032592+  a5  FreeBSD
/dev/hda5             893         905      104391   83  Linux
/dev/hda6             906        1889     7903948+  83  Linux
/dev/hda7            1890        2080     1534176   82  Linux swap / Solaris
/dev/hda8            2081        8454    51199123+  83  Linux

```
for my case it is /dev/hda7 (the one mentioned as Linux swap / Solaris

now back on the fstab file, add the line
```

/dev/hdbX       none            swap    sw              0       0

```
replace the X with what you have found out, now save and close the file, run in terminal

```

sudo swapon /dev/hdbX

```
again replace the X

---

