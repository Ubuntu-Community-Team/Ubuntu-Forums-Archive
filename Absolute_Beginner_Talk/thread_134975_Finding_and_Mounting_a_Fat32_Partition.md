---
title: "Finding and Mounting a Fat32 Partition"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by OkydOky on 2006-02-22
I finally managed to install my Nvidia Drivers! Woo! 
My next bumb in the road is:

I have a Data/Media Partition on my Hard Drive. 
My Hard Drive (250GB Seagate S ATA) is Partitioned as Follows:
1: 30GB For Windows (NTFS)
2: ~160GB For Media (FAT32)
3: ~40GB For Linux, Auto setup (with installer) as swap and Linux Ext3. (So 2 Partitions really)

I want to be able to access my 2nd Partition. The one with all My Music, Movies, and Documents.

Help? :cry:  :confused:  haha...
My 1st Problem is Finding it.. where is it? :( Or where should it be.

---

### Post by gerbman on 2006-02-22
[QUOTE=OkydOky]I finally managed to install my Nvidia Drivers! Woo! 
My next bumb in the road is:

I have a Data/Media Partition on my Hard Drive. 
My Hard Drive (250GB Seagate S ATA) is Partitioned as Follows:
1: 30GB For Windows (NTFS)
2: ~160GB For Media (FAT32)
3: ~40GB For Linux, Auto setup (with installer) as swap and Linux Ext3. (So 2 Partitions really)

I want to be able to access my 2nd Partition. The one with all My Music, Movies, and Documents.

Help? :cry:  :confused:  haha...
My 1st Problem is Finding it.. where is it? :( Or where should it be.[/QUOTE]

Hi there. Check [this]("https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28fat32%29") out. I recommend following the section called "Mounting Partitions Manually".

---

### Post by codejunkie on 2006-02-22
[QUOTE=OkydOky]I finally managed to install my Nvidia Drivers! Woo! 
My next bumb in the road is:

I have a Data/Media Partition on my Hard Drive. 
My Hard Drive (250GB Seagate S ATA) is Partitioned as Follows:
1: 30GB For Windows (NTFS)
2: ~160GB For Media (FAT32)
3: ~40GB For Linux, Auto setup (with installer) as swap and Linux Ext3. (So 2 Partitions really)

I want to be able to access my 2nd Partition. The one with all My Music, Movies, and Documents.

Help? :cry:  :confused:  haha...
My 1st Problem is Finding it.. where is it? :( Or where should it be.[/QUOTE]
in a terminal run ```
sudo fdisk -l
```it will display the partitions something like this 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         182     1461883+  82  Linux swap / Solaris
/dev/hdb2   *         183        2589    19334227+  83  Linux
/dev/hdb3            2590        4998    19350292+  83  Linux

```
find the location of your fat32 partition there now run 
```
sudo mkdir /media/windows
```
for examples sake lets say your fat32 partition is /dev/hda2 you mount it like this 
```
sudo mount /dev/hda2 /media/windows
```
to have it mount automaticly and allow read write access run
```
sudo gedit /etc/fstab
```
add this line to that file but replace /dev/hda2 with your actual partition.
```

/dev/hda2       /media/windows  vfat    iocharset=utf8,umask=000   0       0

```save the file and exit hope this helps.

---

### Post by OkydOky on 2006-02-23
Worked wonderfully. Thank you.

---

