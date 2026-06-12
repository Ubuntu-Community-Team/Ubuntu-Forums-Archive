---
title: "Wot no partition?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by kneewax on 2008-04-07
Hi folks,  

OK here is the deal, I inadvertently and rather annoyingly managed to do something with gParted that completely removed all three partitions from my laptop's HDD.  (don't ask its all a bit vague and I am trying to shut it out)  However the OS stayed up long enough for me to backup everything to a USB harddisk.  OK no data loss, but I did need to re-install the entire system.

I installed Gusty from the CD I previously used and partitioned the 80GB drive 3 ways as before: 20GB ext3 for Gusty, 58Gb FAT32 for Data (lastime round his was ntfs because I was migrating) and about 800mb for a swap file.  All seemed to install fine, BUT Gusty now not only hasn't mounted my data partition, but it doesn't even appear in the 'Computer' window as an unmounted drive.

What have I done wrong?  Can anyone help me locate this partition and get it to permanently mount?

Thanks

Kneewax

---

### Post by Inxsible on 2008-04-07
could you post the output of ```
sudo fdisk -l
``` -l is a lowercase L

---

### Post by kneewax on 2008-04-07
Here you go!


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31313131

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2435    19559106   83  Linux
/dev/sda2            2436        9668    58099072+   b  W95 FAT32
/dev/sda3            9669        9729      489982+   5  Extended
/dev/sda5            9669        9729      489951   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd72ac8cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9964    80027797+   f  W95 Ext'd (LBA)
/dev/sdb5               2        9964    80027766    7  HPFS/NTFS

---

### Post by smurphy_it on 2008-04-07
I'm no expert here, but I believe you have to enter that partition into fstab

You need to create an empty folder under /media for mounting this into.
It's usually a good idea to use the UUID of the drive too... here is an example...


in a terminal do a sudo mkdir /media/windows

sudo vol_id sda2 (this command will give you the UUID of the selected partition)

Next edit the fstab file.

sudo gedit /etc/fstab

Then add a line similar to the following...

UUID=bb9a2d34-f007-201c-85fb-2a3d2faf32aa     /home           ext3 defaults 

save and on next reboot the drive should be there.

---

### Post by durand on 2008-04-07
Well your partition table looks fine...
To mount your FAT partition, try this:

```

mkdir test
sudo mount /dev/sda2 test

```
That will mount the partition into the test folder. Just check that everything works right from nautilus (the file manager) or whatever and if it does, then do this:
```

sudo mkdir /media/sda2
sudo gedit /etc/fstab

```

Then add this to the end of the file:
```

/dev/sda2 /media/sda2 vfat defaults,utf8,umask=007,gid=46 0 1

```
That should automount it for you. You might want if there is a similar line already in the file.

EDIT: Darn, took too long to reply...lol. By the way, smurphy_it, kneewax's trying to mount the FAT partition.

---

### Post by Duck2006 on 2008-04-07
Some reading on mounting win partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kneewax on 2008-04-07
Hi thanks fro all the replies.  

Making a test folder and trying a mount doesn't work - I get no errors messages but I also get not mounted partition...

Contents of my fstab file currently are:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b8b36a26-34cd-4c7b-9a90-d606eebb8924 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=FDB8-2B4E  /data           vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2 /media/sda2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=dd1ec119-bbd4-4c8e-a4cd-8a2d8d00e864 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Any ideas folks?

---

### Post by Duck2006 on 2008-04-07
> # /dev/sda2
UUID=FDB8-2B4E /data vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda2 /media/sda2 vfat defaults,utf8,umask=007,gid=46 0 1

You are trying to mount sda2 twice.

---

### Post by kneewax on 2008-04-07
Ooops!  Good  point.  I removed the original line and replaced it with the one durand suggested.  Now works great - thanks guys

---

