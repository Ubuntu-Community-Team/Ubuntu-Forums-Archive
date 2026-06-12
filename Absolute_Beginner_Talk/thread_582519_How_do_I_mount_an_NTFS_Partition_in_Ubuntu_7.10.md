---
title: "How do I mount an NTFS Partition in Ubuntu 7.10?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-10-19
Hi!

I am trying to mount an NTFS Partition in Ubuntu 7.10.

Steps done:

1. Created Mount Directory: ```
mkdir /mnt/ntfs_files
```

2. Typed: ```
fdisk -l
```
(Found that I need to mount to -> /dev/sdc1)

2. Typed: ```
nano fstab
```

3. Added line:

```
/dev/sdc1      /mnt/ntfs_files     ntfs   nls=utf8,umask=0222 0 0
```

4. Tried: ```
mount -a
```

```
ERROR: line 15 in /etc/fstab is bad
```

I then tried to use the following line instead:

```
/dev/sdc1    /mnt/ntfs_files    ntfs   defaults,umask=007 0
```

I got again the _same_ error!

Any ideas?

Thanks

P.S.> The above used to work in previous Ubuntu versions...

---

### Post by ravenus on 2007-10-19
Isn't that on by default in 7.10, mounting of NTFS partitions with R/W capability?

---

### Post by bodhi.zazen on 2007-10-19
could you post the output of :

```
cat -n /etc/fstab | grep 15
```

---

### Post by dvarsam on 2007-10-19
> **ravenus said:**
> Isn't that on by default in 7.10, mounting of NTFS partitions with R/W capability?

Hello & thanks for your reply!

I have 2 Hard Drives:

HD1:

Partition 1 = Windows XP Pro OS
Partition 2 = Ubuntu v7.10

I then decided to add a 2nd HD:

I got some errors & _lost_ the icon of the HD1\Partition1.

I thought that it auto-mounts only the Windows Partitions on the same HD...
... not Windows Partitions that exist in other HDs...

Am I wrong?
What should I do?

Thanks.

---

### Post by dvarsam on 2007-10-19
> **bodhi.zazen said:**
> could you post the output of :

```
cat -n /etc/fstab | grep 15
```

Here you go, man:
```
root@tony-desktop:/etc# cat -n /etc/fstab |grep 15

    15  /dev/sdc1       /mnt/ntfs_files      ntfs defaults, umask=007 0

root@tony-desktop:/etc#
```

Thanks.

---

### Post by bodhi.zazen on 2007-10-19
If you have 2 hard drives /dev/sdc1 is off (c = third hard drive)

so, can you post the output of :

```
sudo fdisk -l
```

---

### Post by dvarsam on 2007-10-20
> **bodhi.zazen said:**
> If you have 2 hard drives /dev/sdc1 is off (c = third hard drive)

so, can you post the output of :

```
sudo fdisk -l
```

I _do_ have 2 Hard Drives!

```
root@tony-desktop:/etc# sudo fdisk -l

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9f7f

Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1        3243    26049366    7  HPFS/NTFS
/dev/sdb2            3244        3437     1558305    f  W95 Ext'd (LBA)
/dev/sdb3            3438        4865    11470410   83  Linux
/dev/sdb5            3244        3437     1551467+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55271620

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS

root@tony-desktop:/etc# 
root@tony-desktop:/etc#
```

There is also a Zip connected in the PC & a Network Drive connecting through Ethernet Cable...
Maybe one of the above is taking that > If you have 2 hard drives /dev/sdc1 is off (c = third hard drive) "b" position...

Thanks.

---

### Post by bodhi.zazen on 2007-10-20
oic now ...

You need an additional "0" at the end of the line in fstab :

```
/dev/sdc1       /mnt/ntfs_files      ntfs defaults, umask=007 0 0
```

And what is up with your sig ? ~ :lolflag:

---

