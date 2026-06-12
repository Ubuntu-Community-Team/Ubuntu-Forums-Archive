---
title: "Help with mount/accessing storage drive."
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by sgrif on 2007-12-21
K. Total linux newbie here. Please help me out?
Storage drive that I set up in XP, but last used in Vista.NSTF format. If I try to open it or right click > mount, I get "hal-storage-fixed-mount-all-options refused uid 1000"

I'm using kubuntu running gutsy. Thanks!

---

### Post by taurus on 2007-12-21
What partition is that drive?  Post the output of this command from a terminal.

```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by spiderbatdad on 2007-12-21
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by sgrif on 2007-12-21
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x130a7ebe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         128     1024000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         128        9730    77130256    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4489d063

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18701   150215751   83  Linux
/dev/sdb2           18702       19457     6072570    5  Extended
/dev/sdb5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4be8868d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9730    78155201    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0xbc5bbc5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      266306  2147483647+  ee  EFI GPT
```

The 500 GB one is the one I'm trying to access

---

### Post by taurus on 2007-12-21
Which one do you want to mount, /dev/sda2 or /dev/sdc1?

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda2 /media/sdc1
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
df -h
```

---

### Post by sgrif on 2007-12-21
> **spiderbatdad said:**
> [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Thanks, but I'd prefer to learn how to do it the hard way. :)

---

### Post by sgrif on 2007-12-21
> **taurus said:**
> Which one do you want to mount, /dev/sda2 or /dev/sdc1?

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda2 /media/sdc1
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
df -h
```

I'm pretty sure it's /dev/sdd1, actually. Whichever one is the 500 gb.

---

### Post by taurus on 2007-12-21
Do you see that WARNING above?  You need to use gparted to format it to ntfs if you want to use ntfs filesystem for /dev/sdd1.

---

### Post by sgrif on 2007-12-21
> **taurus said:**
> Do you see that WARNING above?  You need to use gparted to format it to ntfs if you want to use ntfs filesystem for /dev/sdd1.
What's gparted?

You're talking to an UTTER noob. :)

---

### Post by Ex-windows on 2007-12-21
> **sgrif said:**
> What's gparted?

You're talking to an UTTER noob. :)
gparted is a partition tool . You can download by going to
System>Administration.Synaptic Package Manager.
When synaptic comes up use the search button and type in gparted..
The search will find it and then you check the box and Mark  for installation and then click the apply button. This will download it for you. Gparted is also the partition tool used on the Live cd (installation disk).
You cannot partiton or do anything to a partiton that you are on or mounted. So if you need to you can insert the Live cd and use gparted from there. Hope that helps as far as the gparted issue goes.
Happy Holidays

---

### Post by taurus on 2007-12-21
```
sudo apt-get update
sudo apt-get install gparted
gksu gparted
```

---

### Post by sgrif on 2007-12-21
Wait, I don't want to reformat the drive I want to access the files there. Won't partitioning it delete all the files?

---

### Post by sgrif on 2007-12-21
K, according to gparted, it's dev/sdd2 I want. /dev/sdd1/ is an unknown file system but /dev/sdd2/ is already ntfs. So would this be the right code?

```
sudo mkdir /media/sdd2
sudo mount -t ntfs-3g /dev/sdd2 /media/sdd2
df -h
```

---

### Post by sgrif on 2007-12-21
Nvm, the code I just asked about worked. :) Thanks for your help!

---

