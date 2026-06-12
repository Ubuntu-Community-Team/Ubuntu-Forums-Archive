---
title: "Mounting an old hard drive"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by hallikpapa on 2005-12-09
Hello all! 

I am new to Ubuntu and was trying to copy over some files from a second hard drive located on my computer. Here is some info and the error I am receiving at the end. The second hard drive was an install of Fedora Core 4, and I just need to grab some files off of it. Everything is done as root. Trying to get stuff off of the 80GB hard drive. 

df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              19G  2.4G   16G  14% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile

```

fdisk -l
```

Disk /dev/hda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2427    19494846   83  Linux
/dev/hda2            2428        2534      859477+   5  Extended
/dev/hda5            2428        2534      859446   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        9729    78043770   8e  Linux LVM
```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

so I run:
mkdir /recovery

and then I try
sudo mount -t ext3 /dev/hdb2 /recovery

And this is the error I get:
mount: /dev/hdb2 already mounted or /recovery busy

Ideas?

---

### Post by amohanty on 2005-12-09
I think you will need to mount 
/dev/hdb1
and 
/dev/hdb2 
separately. Try that and post the results.

HTH

---

### Post by hallikpapa on 2005-12-09
I created a 2nd dir 

mkdir /backup

mount -t ext3 /dev/hdb1 /recovery

Worked fine.

mount -t ext3 /dev/hdb2 /backup
mount: /dev/hdb2 already mounted or /backup busy

---

### Post by hallikpapa on 2005-12-09
I tried fsck and got this. Looks like this is why it won't mount, but how would I repair it?

```

# fsck /dev/hdb2

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/hdb2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

It was a Fedora Core 4 install, can't remember the type. But it was probably whatever the default is.  I would run the e2fsck but I don't know what it is or those options are. :confused:

Did a man page on e2fsck and all the alt. superblocks fail. Starting to sound like no access to this drive?

<edit.> I just unplugged the Ubuntu drive, booted into Fedora, backing up all my stuff. ;)

---

### Post by amohanty on 2005-12-09
your /dev/hdb2 seems to be a LVM volume. Docs @ 
[http://www.die.net/doc/linux/HOWTO/LVM-HOWTO.html](http://www.die.net/doc/linux/HOWTO/LVM-HOWTO.html)

Post the output of:

```
sudo vgdisplay -v
```

and 

```
lvdisplay
```

AM

---

### Post by hallikpapa on 2005-12-09
vgdisplay -v
```

  Finding all volume groups
    Finding volume group "VolGroup00"
  --- Volume group ---
  VG Name               VolGroup00
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               74.41 GB
  PE Size               32.00 MB
  Total PE              2381
  Alloc PE / Size       2380 / 74.38 GB
  Free  PE / Size       1 / 32.00 MB
  VG UUID               fH6dTa-zFVd-ipxL-CWjo-ckHn-BDuE-iS9IS2
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol00
  VG Name                VolGroup00
  LV UUID                eEE7ay-7nMA-xW2b-21hS-aoyg-0Vo2-9q03yZ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                72.44 GB
  Current LE             2318
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol01
  VG Name                VolGroup00
  LV UUID                HxodRD-vmWw-xm4Y-pzSD-s53x-gBAG-3WY00I
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                1.94 GB
  Current LE             62
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1
   
  --- Physical volumes ---
  PV Name               /dev/hdb2     
  PV UUID               VMoqlQ-QsVB-oxsf-czgA-vRWD-30AN-xvB6Df
  PV Status             allocatable
  Total PE / Free PE    2381 / 1
   
```

lvdisplay
```

  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol00
  VG Name                VolGroup00
  LV UUID                eEE7ay-7nMA-xW2b-21hS-aoyg-0Vo2-9q03yZ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                72.44 GB
  Current LE             2318
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol01
  VG Name                VolGroup00
  LV UUID                HxodRD-vmWw-xm4Y-pzSD-s53x-gBAG-3WY00I
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                1.94 GB
  Current LE             62
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1
```

Thanks for all your help!

---

### Post by amohanty on 2005-12-10
Ok you seem to be using logical volumes on the hdd (damn FC4) in question so just do this:

> cd /
sudo mkdir mnt
cd mnt
sudo mkdir vol0 vol1
sudo mount -t ext3 /dev/VolGroup00/LogVol00 /mnt/vol0
sudo mount -t ext3 /dev/VolGroup00/LogVol01 /mnt/vol1

Per the lvdisplay output above, you have two logical volumes vol0 is 73G and vol1 is 2G. This will mount the drives on /mnt/vol1. Also if you would like to access them as a regular user dont forget to change the permissions on them.

HTH

---

### Post by hallikpapa on 2005-12-10
This did the trick. Thank you so much! Saved me much heartache. :)

---

