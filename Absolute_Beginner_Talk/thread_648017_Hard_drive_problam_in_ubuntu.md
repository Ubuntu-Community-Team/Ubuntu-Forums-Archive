---
title: "Hard drive problam in ubuntu"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Torque313 on 2007-12-23
I'm having a strange issue that just kind of happened when i re-booted.
I'm running it on a pc with 3 hard drives
1 with windows
1 for storage 
and 1 with ubuntu

Everything was fine and i was running perfectly and could acess all the data on all the drives. Now after the re-boot i can see the drives but when i double click them the window doesn't show what's on the drive, it automatically goes to the ubuntu drive. How do i get it back to normal?

---

### Post by blueridgedog on 2007-12-23
Well, after 15 hours, 30 views and no takers, I will give what advice I can.

Lets take a look at what your system sees.  Can you post the output of the following commands?
```

cat /etc/fstab

cat /proc/partitions

sudo fdisk -lu
```

Thanks.

---

### Post by The Cog on 2007-12-23
Can we also see the output from the command **mount**?

---

### Post by Torque313 on 2007-12-23
> **blueridgedog said:**
> Well, after 15 hours, 30 views and no takers, I will give what advice I can.

Lets take a look at what your system sees.  Can you post the output of the following commands?
```

cat /etc/fstab

cat /proc/partitions

sudo fdisk -lu
```

Thanks.

I would like to start out by thanking you for giving me this help. I'm very new to linux in general and i need all the help i can get :)

response to cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=4c0e65ef-3ebd-4d49-be5e-c9a8f8ae3317 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=054ad4f3-7a40-44e3-beb5-4f314d8a561b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

response to cat /proc/partitions
major minor  #blocks  name

   8     0   78150744 sda
   8     1   78140128 sda1
   8    16  244198584 sdb
   8    17  244196001 sdb1
   8    32  312571224 sdc
   8    33  309540388 sdc1
   8    34          1 sdc2
   8    37    3028221 sdc5

response to sudo fdisk -lu
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42f6c434

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5874c0f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb968b968

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   619080839   309540388+  83  Linux
/dev/sdc2       619080840   625137344     3028252+   5  Extended
/dev/sdc5       619080903   625137344     3028221   82  Linux swap / Solaris

---

### Post by Torque313 on 2007-12-23
> **The Cog said:**
> Can we also see the output from the command **mount**?



/dev/sdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by logos34 on 2007-12-23
If sda and sdb are internal hard disks, use [this guide]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971") to mount them.

If you're running gutsy, ntfs-3g is already installed--you just need **ntfs-config**.

The latter will create the appropriate fstab entries.

---

### Post by blueridgedog on 2007-12-23
OK, from the information you sent:

fstab tells of mounting:

/dev/sdc1 as you root ubuntu
/dev/sdc5 as ubuntu swap
/dev/scd0 as your CDROM

However, you have some other partitions not in fstab:

/dev/sda with one partition sda1
/dev/sdb with one partition sdb

and and a /dev/sdc2 which is probably an extended partition in which lives /dev/sdc5

We can get a hint about what is on these other two disks:

/dev/sda is an 80 gb NTFS drive (probably your windows boot disk
with one partition: /dev/sda1

/dev/sdb is a 250.0 GB NTFS drive (your storage/documents drive)
with one partition: /dev/sdb1

So, now to mount these we would do the following:

(see the how-to link already provided, but here are some steps).

1.  make a location to mount them and see that you own it

sudo mkdir /mnt/windows
chown USER:USER /mnt/windows (insert your user account)
sudo mkdir /mnt/storage
chown USER:USER /mnt/storage (insert your user account)

2.  Mount the drives
sudo mount -t ntfs-3g /dev/sda1 /mnt/windows
sudo mount -t ntfs-3g /dev/sdb1 /mnt/storage

Read the guide for how to edit /etc/fstab to do this for you.

---

### Post by blueridgedog on 2007-12-23
The following lines could be put in /etc/fstab to mount these (assuming you made the mount points as mentioned before)

/dev/sda1  /mnt/windows     ntfs-3g    defaults,umask=007,gid=46 0       1
/dev/sdb1  /mnt/storage     ntfs-3g    defaults,umask=007,gid=46 0       1

---

### Post by blueridgedog on 2007-12-23
I stand corrected, the [guide]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971") is pretty impressive, the ntfs-config tool (installed by sudo apt-get install ntfs-config) is so simple.  

I will simply point people there from now on.

---

### Post by Torque313 on 2007-12-23
Wow guys thanks :)
It worked like a charm.
Any idea as to why it worked at one point and then just went all retarted?
Is this thing common?

---

### Post by The Cog on 2007-12-24
No idea. I would say it's not common. If they were working before, then something must have overwritten your /etc/fstab file and removed the extra entries. Very odd and naughty.

---

### Post by blueridgedog on 2007-12-24
That is the REAL mystery here.  I am in the dark though.

---

### Post by Torque313 on 2008-01-02
It just did it again. This is really starting to piss me off.

---

### Post by Torque313 on 2008-01-02
the ntfs configuration tool doesn't seem to do the trick anymore

---

### Post by Torque313 on 2008-01-03
please could somebody help me?
remember i'm a noob so i'm going to need step by step instructions
the program in that users guide is not working anymore so i need a way to get around it

---

