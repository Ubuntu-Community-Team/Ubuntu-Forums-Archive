---
title: "Trying to mount/read an ntfs drive"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2006-12-29
I have an IDE drive formatted as ntfs which I need to recover some data from however I am having from problems.

here is my  **sudo fdisk -l** output:
```

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       36483   293049666    7  HPFS/NTFS

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1958    15727603+  fd  Linux raid autodetect
/dev/sda2            1959        8747    54532642+  fd  Linux raid autodetect
/dev/sda3            8748        9039     2345490   fd  Linux raid autodetect

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1958    15727603+  fd  Linux raid autodetect
/dev/sdb2            1959        8747    54532642+  fd  Linux raid autodetect
/dev/sdb3            8748        9039     2345490   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001   83  Linux

Disk /dev/md0: 16.1 GB, 16104947712 bytes
2 heads, 4 sectors/track, 3931872 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 55.8 GB, 55841325056 bytes
2 heads, 4 sectors/track, 13633136 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 2401 MB, 2401697792 bytes
2 heads, 4 sectors/track, 586352 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table
```

and here is my **/etc/fstab** output:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/md1        /home           ext3    defaults        0       2
# /dev/sdc1
UUID=12b5e3a2-0088-4646-b80e-1e7a446fa210 /mnt/storage    ext3    defaults        0       2
# /dev/md2
UUID=645c52d8-c538-4a44-b7be-3a5fb485dd3a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /media/windows  ntfs    defaults        0       0
```

however, whenever I try and do a **sudo mount -a** I get this
```
mount: special device /dev/hdc1 does not exist
```

same thing if I try a **sudo mount /dev/hdc1 /media/windows**

can someone please help? thanks in advance.

---

### Post by hyper_ch on 2006-12-29
Create Mount Points

Instead of /media/, you can also use /mnt/, both will work, but make sure to make the correct edits in all places.

mkdir /media/c_drive
mkdir /media/d_drive
mkdir /media/e_drive

You don't have to use these names, if you prefer to creat folders such as movies, documents, or winxp, any name will work (without spaces).

Mount Partitions

Run 'man mount' to fully explain what "-r -o umask=0222" does.

mount /dev/hda1 /media/c_drive/ -t ntfs -r -o umask=0222
mount /dev/hda2 /media/d_drive/ -t ntfs -r -o umask=0222
mount /dev/hda3 /media/e_drive/ -t ntfs -r -o umask=0222

Update /etc/fstab

Open '/etc/fstab' in an editor and add these lines to the END of the file:

/dev/hda1 /media/c_drive ntfs ro,defaults,umask=0222 0 0
/dev/hda2 /media/d_drive ntfs ro,defaults,umask=0222 0 0
/dev/hda3 /media/e_drive ntfs ro,defaults,umask=0222 0 0

FAT32

While wirting to ntfs partitions in linux is dangerous (although possible but I'm not going to cover this here) the writing to a fat32 filesystem is safe. In case you have a dual-boot system (linux & windows) you can use fat32 partitions as partitions onto which both systems can access with rw rights.

Add to fstab:

/dev/hda1 /media/fat32 vfat umask=000 0 0

---

### Post by Aberrix on 2006-12-29
> **sjau said:**
> Create Mount Points

I've already created the mount point **/media/windows** with the same results

---

### Post by hairmetal4ever on 2006-12-29
> **sjau said:**
> Create Mount Points

Instead of /media/, you can also use /mnt/, both will work, but make sure to make the correct edits in all places.

mkdir /media/c_drive
mkdir /media/d_drive
mkdir /media/e_drive

You don't have to use these names, if you prefer to creat folders such as movies, documents, or winxp, any name will work (without spaces).

Mount Partitions

Run 'man mount' to fully explain what "-r -o umask=0222" does.

mount /dev/hda1 /media/c_drive/ -t ntfs -r -o umask=0222
mount /dev/hda2 /media/d_drive/ -t ntfs -r -o umask=0222
mount /dev/hda3 /media/e_drive/ -t ntfs -r -o umask=0222

Update /etc/fstab

Open '/etc/fstab' in an editor and add these lines to the END of the file:

/dev/hda1 /media/c_drive ntfs ro,defaults,umask=0222 0 0
/dev/hda2 /media/d_drive ntfs ro,defaults,umask=0222 0 0
/dev/hda3 /media/e_drive ntfs ro,defaults,umask=0222 0 0

FAT32

While wirting to ntfs partitions in linux is dangerous (although possible but I'm not going to cover this here) the writing to a fat32 filesystem is safe. In case you have a dual-boot system (linux & windows) you can use fat32 partitions as partitions onto which both systems can access with rw rights.

Add to fstab:

/dev/hda1 /media/fat32 vfat umask=000 0 0


The only thing about Fat32 I have trouble wiht is making partitions larger than 32GB.

---

### Post by hyper_ch on 2006-12-29
> **Aberrix said:**
> I've already created the mount point **/media/windows** with the same results

and you have no umask in your fstab

---

### Post by Aberrix on 2007-01-09
> **sjau said:**
> and you have no umask in your fstab

what do you mean?

---

### Post by Aberrix on 2007-01-09
the only thing I wish to do is be able to read the drive, pull some data off and place it onto an existing ext3 drive, then format the ntfs drive to ext3. that's all...

---

### Post by Ben Sprinkle on 2007-01-09
[Click me to find out how to write and reate ntfs.](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Aberrix on 2007-01-10
> **Goat Spirit said:**
> [Click me to find out how to write and reate ntfs.](http://ubuntuforums.org/showthread.php?t=217009)

this did not help/work, any other guidance?

---

### Post by jvc26 on 2007-01-10
> **Aberrix said:**
> what do you mean?

He means your /etc/fstab:
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /media/windows  ntfs    defaults        0       0

No umask (see the one he put up):
mount /dev/hda1 /media/c_drive/ -t ntfs **-r -o umask=0222**

That isnt from your fstab by the way (the line) thats a command, but the umask should show up in the fstab if you put it in.

Did you check out terminal:
```

man mount

```

And also I'd take a peek at:
[http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab](http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab)
On mounting:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
and
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
And on automatically mounting:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Hope they help,
Il

---

### Post by Ben Sprinkle on 2007-01-10
> **Aberrix said:**
> this did not help/work, any other guidance?

Your doing some step wrong, I hae gotten it to work. :)

---

### Post by Aberrix on 2007-01-10
> **Goat Spirit said:**
> Your doing some step wrong, I hae gotten it to work. :)

care to help then please?

I just need to get some files off an ntfs drive... I followed the instructions...
installed ntfs-3g
edited fstab
rebooted

and when I do a sudo mount -a, I get the following:
```
Error opening partition device: No such file or directory
Failed to startup volume: No such file or directory
Failed to mount '/dev/hdc1': No such file or directory
```

here are the results of sudo fdisk -l | grep NTFS
```
Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/md1 doesn't contain a valid partition table
Disk /dev/md2 doesn't contain a valid partition table
/dev/hdc1               1       36483   293049666    7  HPFS/NTFS
```

and here is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/md1        /home           ext3    defaults        0       2
# /dev/sdc1
UUID=12b5e3a2-0088-4646-b80e-1e7a446fa210 /mnt/storage    ext3    defaults        0       2
# /dev/md2
UUID=645c52d8-c538-4a44-b7be-3a5fb485dd3a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /media/windows ntfs-3g  defaults,locale=en_US.utf8      0   0
```

please help! thanks in advance.

---

### Post by shadowsypher on 2007-01-10
I just finnished doing exactly what you are trying to do here are the lines that I added to my fstab
/dev/hdb1       /media/80gb     ntfs     ro,auto,user,fmask=0111,dmask=0000,uid=1000    0    0
/dev/hdd1	/media/250gb	ntfs	ro,auto,users,fmask=0111,dmask=0000,uid=1000	0	0
and I know that fmask and dmask are supposed to be for fat32 but it din't work untill I put those in. Once your done editing fstab reboot. hope this helps

---

### Post by Aberrix on 2007-01-11
> **shadowsypher said:**
> I just finnished doing exactly what you are trying to do here are the lines that I added to my fstab
/dev/hdb1       /media/80gb     ntfs     ro,auto,user,fmask=0111,dmask=0000,uid=1000    0    0
/dev/hdd1	/media/250gb	ntfs	ro,auto,users,fmask=0111,dmask=0000,uid=1000	0	0
and I know that fmask and dmask are supposed to be for fat32 but it din't work untill I put those in. Once your done editing fstab reboot. hope this helps

when I try that, reboot and try a 'sudo mount -a' I am told:
```
mount: special device /dev/hdc1 does not exist
```

---

### Post by Ben Sprinkle on 2007-01-11
Well what the hell is hdc1??
Souldn't it be hda1 or sda1? Or hdb1??

---

### Post by Aberrix on 2007-01-11
> **Goat Spirit said:**
> Well what the hell is hdc1??
Souldn't it be hda1 or sda1? Or hdb1??

I have no idea??? when I do a 'sudo fdisk -l | grep NTFS' it lists the htfs drive as /dev/hdc1

???

---

### Post by Ben Sprinkle on 2007-01-11
Usually if you have 1 hard drive and say 3 partitions it would be this:
hda1
hda2
hda3
USB or ipods etc are usually sda1 etc.
If you have 2 hard drives at 2 partitions each it would look like this:
hda1
hda2
hdb1
hdb2
And etc., understand?

---

### Post by Aberrix on 2007-01-11
> **Goat Spirit said:**
> ]
And etc., understand?

yes, but how does that help me?

the drive shows up as hdc with 1 partition, ergo hdc1

its connected to my second IDE port, the first IDE port has my CD-ROM on it. my other HD's which are in RAID-1 are connected to my SATA ports.

---

### Post by Ben Sprinkle on 2007-01-11
How many hard drives do you have total?
If your hard drive is in the 3rd IDE port then it's hdc.

---

### Post by Aberrix on 2007-01-11
> **Goat Spirit said:**
> How many hard drives do you have total?
If your hard drive is in the 3rd IDE port then it's hdc.

#)=port

Sata
1) WD Raptor 74GB - RAID 1
2) WD Raptor 74GB - RAID 1
3) SG 250GB Barracuda

IDE
1) CD-ROM
2) NTFS DRIVE

my RAID has three partitions, /, /home and swap
my 250GB Drive has one ext3 partion (/media/storage)

the NTFS drive has one partition w/ some video files I want to get off it, then reformat it and plug it into my server.

---

### Post by Ben Sprinkle on 2007-01-11
Why do you have 3 partitions? I combine mine into one, oh well.
If it is NTFS, does it automatically get mounted or try to get mounted?
Try this, it has worked for me but you must be in root.
```

#poke around in /dev for /dev/hda1 /dev/hdc or what not
mkdir /media/ntfs
sudo mount /dev/hdc1 /media/ntfs

```
I am also sorta confused on what your doing mate. :)

---

### Post by Aberrix on 2007-01-11
> **Goat Spirit said:**
> Why do you have 3 partitions?

I am also sorta confused on what your doing mate. :)

/ - 15Gb
/home - 52GB
swap - 2GB

incase I have to format or re-install, '/home' will *crosses fingers* hopefully be safe.

---

### Post by Ben Sprinkle on 2007-01-11
If you need to reinstall, you copy /home to a USB before you do it. Meh. :P

---

### Post by CroEragon on 2007-01-11
I dont know why people are so paranoid about ntfs-3g. Ok it is beta, but it is fairly stable (i use it for long now, never any problem). It is much better than pathetic FAT32 and 32GB limit. But if you can, format ext3, it is best.

---

### Post by Ben Sprinkle on 2007-01-11
> **CroEragon said:**
> I dont know why people are so paranoid about ntfs-3g. Ok it is beta, but it is fairly stable (i use it for long now, never any problem). It is much better than pathetic FAT32 and 32GB limit. But if you can, format ext3, it is best.

Aye to that. +1

---

### Post by Aberrix on 2007-01-11
well... any ideas on how I can get this drive mounted so I can get some data off it?

---

### Post by Aberrix on 2007-01-12
bump?

---

### Post by Ben Sprinkle on 2007-01-12
> **Aberrix said:**
> bump?

Yeah I forgot to post it yesterday, back at school. If you can wait 4 hours, I can post it when I get home. :)

---

### Post by alley on 2007-02-12
I'm having exactly the same situation.

2x sata disk running ubuntu
1x ide disk with an ntfs partition and an fat32 partition on it

fdisk reports it to be there but there is no /dev/hdc1 entry in /dev/ :(

Did you manage to solve this already?

---

### Post by Aberrix on 2007-02-15
> **alley said:**
> 

Did you manage to solve this already?

nope :(

---

