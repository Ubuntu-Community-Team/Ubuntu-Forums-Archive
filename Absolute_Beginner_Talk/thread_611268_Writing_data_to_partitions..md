---
title: "Writing data to partitions."
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-11-12
hi , i am using ubuntu 7.04 and i can see my window drives in ubuntu , i can only read data from these drives , can write data to these drives . how to do so????

---

### Post by taurus on 2007-11-12
Is it ntfs filesystem?  Then, you need to install and use ntfs-3g driver if you want to write to ntfs filesystem.

Post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by damansandhu on 2007-11-12
how to get ntfs-3g drivers

---

### Post by taurus on 2007-11-12
Try

```
sudo apt-get update
sudo apt-get install ntfs-3g ntfs-config
gksudo ntfs-config
```

---

### Post by damansandhu on 2007-11-12
daman@daman-desktop:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fuse-utils libfuse2 libntfs-3g0
The following NEW packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 ntfs-3g
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 265kB of archives.
After unpacking 717kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main fuse-utils 2.6.3-1ubuntu2 [77.4kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main libfuse2 2.6.3-1ubuntu2 [72.0kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe libntfs-3g0 1:1.328-1 [90.0kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe ntfs-3g 1:1.328-1 [25.9kB]  
Fetched 265kB in 7s (33.7kB/s)                                                 
Selecting previously deselected package fuse-utils.
(Reading database ... 111639 files and directories currently installed.)
Unpacking fuse-utils (from .../fuse-utils_2.6.3-1ubuntu2_i386.deb) ...
Selecting previously deselected package libfuse2.
Unpacking libfuse2 (from .../libfuse2_2.6.3-1ubuntu2_i386.deb) ...
Selecting previously deselected package libntfs-3g0.
Unpacking libntfs-3g0 (from .../libntfs-3g0_1%3a1.328-1_i386.deb) ...
Setting up fuse-utils (2.6.3-1ubuntu2) ...
creating fuse device node...
udev active, devices will be created in /dev/.static/dev/
creating fuse group...

Selecting previously deselected package ntfs-3g.
(Reading database ... 111675 files and directories currently installed.)
Unpacking ntfs-3g (from .../ntfs-3g_1%3a1.328-1_i386.deb) ...
Setting up libfuse2 (2.6.3-1ubuntu2) ...

Setting up libntfs-3g0 (1.328-1) ...

Setting up ntfs-3g (1.328-1) ...
Setting ntfs-3g suid root with group fuse...done
Users from 'fuse' group can now mount NTFS volume.

daman@daman-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       19457   136753312+   f  W95 Ext'd (LBA)
/dev/sda5            4865        7296    19535008+   7  HPFS/NTFS
/dev/sda6            2433        4864    19534977    b  W95 FAT32
/dev/sda7            9542        9728     1502046   82  Linux swap / Solaris
/dev/sda8            9729       14592    39070048+   7  HPFS/NTFS
/dev/sda9           14593       19457    39078081    7  HPFS/NTFS
/dev/sda10           7297        8269     7815591   83  Linux
/dev/sda11           8270        9541    10217308+  83  Linux

Partition table entries are not in disk order
daman@daman-desktop:~$ sudo badblocks -s -n /dev/sda1
/dev/sda1 is mounted; it's not safe to run badblocks!
daman@daman-desktop:~$

---

### Post by taurus on 2007-11-12
> **damansandhu said:**
> 
daman@daman-desktop:~$ **[COLOR="Blue"]sudo badblocks -s -n /dev/sda1[/COLOR]**
/dev/sda1 is mounted; it's not safe to run badblocks!
daman@daman-desktop:~$

:confused:

Try to umount your ntfs partitions first before you remount them with ntfs-3g.

---

### Post by damansandhu on 2007-11-12
it says cannot unmount the volume

---

### Post by taurus on 2007-11-12
What command did you run?

```
sudo umount /dev/sda1 /dev/sda5 /dev/sda8 /dev/sda9
df -h
```

---

### Post by damansandhu on 2007-11-12
ok , thanks , how to check for errors?

---

### Post by taurus on 2007-11-12
> **damansandhu said:**
> ok , thanks , how to check for errors?

Check for errors of the ntfs partitions?  Better do that in windows, not Ubuntu.

---

### Post by damansandhu on 2007-11-12
umm , my windows stopped working due to unknown hard error , i was watching "Braveheart" on windows then suddenly an error "Unknown Hard error" Appeared then everything stopped , even my partitions in my computer were gone . then i reset my pc , then windows were not booting in safe and normal mode . then i thought maybe i can fix that with the help of linux , atleast i finished movie with the hellp of linux :d

---

### Post by taurus on 2007-11-12
Maybe your harddrive is on the way out or this is a good reason to dump windows then!

---

### Post by damansandhu on 2007-11-12
i am not sure that my hardrive is out because its seagate barracuda , well i have  a doubt , everytime i insert dvd in my dvd drive , my pc including ubuntu and windows stops responding for a few seconds , i dont know why it happens. 

I will not be able to play games if i dump windows :((

---

### Post by damansandhu on 2007-11-12
how to write data in sda1?

---

### Post by taurus on 2007-11-12
Again, if you want to write to ntfs filesystem, /dev/sda1, you need to mount it with ntfs-3g driver.

```
sudo umount /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```

---

### Post by damansandhu on 2007-11-12
cool , let it check for bad sectors when i will mount with 3g drivers, 

in the mean time can you tell me what entertainment can i do in ubuntu ?

---

### Post by damansandhu on 2007-11-12
yea i have another questions , few months back my brother reset ubuntu many times then it stopped booting , it failed to check disk for errors and failed to start , why that happened?

---

