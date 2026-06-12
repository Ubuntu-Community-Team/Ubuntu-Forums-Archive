---
title: "LVM troubles"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by cobaltcopy on 2007-07-04
Hi all,

Thank you in advance.

I have a mythtv system setup and I'm trying to setup an lvm over two disks:
```
fdisk /dev/hda -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        1925    15358140   83  Linux
/dev/hda3            1926        2447     4192965   82  Linux swap / Solaris
/dev/hda4            2448       14593    97562745   8e  Linux LVM

fdisk /dev/hdb -l

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161   8e  Linux LVM


```

I have created a logical group 'lg'. The problem is that I can't find the logical group in "/dev/vg" to mkfs.xfs or to simply expand it. I'm trying to mount it eventually as /video.

My vgdisplay output:
```
--- Volume group ---
  VG Name               vg
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               167.57 GB
  PE Size               4.00 MB
  Total PE              42897
  Alloc PE / Size       25600 / 100.00 GB
  Free  PE / Size       17297 / 67.57 GB
  VG UUID               M03TE2-1fLw-3yuw-BoEA-ewKB-rD3C-c5FXAA

```

---

### Post by supertdog on 2007-07-05
This won't help you but you're not alone.  I'm having the same problem.  I'm very new to ubuntu, this is my first ubuntu system but I thought I partitioned correctly to allow for a logical volume group to be mounted at /mediaFiles

but here is the fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=9d2af505-26d1-4d97-abc0-c47f64a25322 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=c8cbc9e6-9061-42ca-acd2-1ab5fdb5eb2c /boot           ext3    defaults        0       2
# /dev/hda2
UUID=c8929950-1664-4191-9229-980bb263f04b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

however  fdisk /dev/hda -l shows...

```

Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32         153      979965   82  Linux swap / Solaris
/dev/hda3             154        2585    19535040   83  Linux
/dev/hda4            2586       36483   272285685    5  Extended
/dev/hda5            2586       36483   272285653+  8e  Linux LVM
```

what do I do to get back into the partitioner and make the volume show up?

---

### Post by supertdog on 2007-07-05
I feel like I'm getting closer.

this should show you the logical volumes availible... (mine is mediabox_vg1)

```
$  sudo vgscan
```

then activate the volume...

```
$  sudo vgchange -a y mediabox_vg1 
```

then find the logical volume...

```
$ sudo lvs
```

the you should be able to mount it...

```
$ sudo mkdir /mnt/mediaFiles
$ sudo mount -t ext3 /dev/mediabox_vg1/mediaFiles /mnt/mediaFiles
```

but I just get this error...

```
mount: wrong fs type, bad option, bad superblock on /dev/mediabox_vg1/mediaVolume,
       missing codepage or other error
```

---

### Post by supertdog on 2007-07-21
In searching I've noticed that there are a few threads where people seem to be having this sort of problem, all of which end without a response.  Does anyone have an idea of even where to begin to track this down.  I currently have a few hundred gig of space not being used because I can't get my logical volume to mount.

---

### Post by mpeters on 2007-07-21
> **supertdog said:**
> In searching I've noticed that there are a few threads where people seem to be having this sort of problem, all of which end without a response.  Does anyone have an idea of even where to begin to track this down.  I currently have a few hundred gig of space not being used because I can't get my logical volume to mount.

Quick and Dirty LVM Howto:

1. Initialize your partition, eg /dev/hdb1
```
sudo pvcreate /dev/hdb1
```

2. Create a volume group from the partition:
```
sudo vgcreate my_volume_group /dev/hdb1 
```

3. Activate the volume group:
```
sudo vgchange -a y my_volume_group
```

4 Create a logical volume, eg a volume called myvolume of 50Gb:
```
sudo lvcreate -L50G -nmyvolume my_volume_group
```

5. Format the new volume group as ext3:
```
sudo mkfs.ext3 /dev/my_volume_group/myvolume
```

6. Now mount the new volume:
```

sudo mkdir /home/volume
sudo mount /dev/my_volume_group/myvolume /home/volume
```

7. To add this volume to your /etc/fstab add the line:
```
/dev/my_volume_group/myvolume /home/volume   ext3    defaults        0   0
```

**supertdog**, I suspect your problem is from not formatting the volume, step 5.

Some further useful stuff :

To show volume groups:
```
vgdisplay
```

To show logical volumes:
```
lvdisplay
```

To remove a logical volume, after first umounting:
```
lvremove /dev/my_volume_group/myvolume
```

For more details check [http://tldp.org/HOWTO/LVM-HOWTO/commontask.html](http://tldp.org/HOWTO/LVM-HOWTO/commontask.html)

---

### Post by supertdog on 2007-07-21
Okay this seems to have solved it for me...


I needed to run mkfs

I really wanted to mount the filesystem xfs but that isn't available to me for some reason so I just did this...

```

sudo mkfs -t ext3 /dev/mediabox_vg1/mediaVolume

```

then I was able to mount...
```

sudo mount -t ext3 /dev/mediabox_vg1/mediaVolume /mnt/mediaFiles

```

hope this helps

---

### Post by cobaltcopy on 2007-07-21
Sorry for not replying sooner...

I'm currently in the process of deleting the partition and starting from scratch.

Will update later.

---

### Post by cobaltcopy on 2007-07-21
Success!

I simply removed all of the volumes to make a clean lvm formatted with xfs.

Thanks for all of the help.

---

