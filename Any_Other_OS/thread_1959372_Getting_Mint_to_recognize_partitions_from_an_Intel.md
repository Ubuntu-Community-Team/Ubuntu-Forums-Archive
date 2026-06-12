---
title: "Getting Mint to recognize partitions from an Intel RAID"
date: 2012-04-15
forum: Any Other OS
---

### Post by Jguy on 2012-04-15
Hello,

I need to figure out how to get Ubuntu (actually Linux Mint 12, x64) to recognize my partitions setup through an Intel RAID BIOS utility. 

My setup:

2x 1.5TB Hard Drives in a RAID 0 (on an MSI P67A-GD53) I get a dialog after POST that says to press Ctrl+D to enter RAID setup utility.
On this RAID, I have two partitions. I really only need to see one of them.
There should be a 2TB partition at the beginning of the disk that I need to get to through Linux. It holds all of my documents, music, movies, etc. 
The disk was initialized with GPT on Windows.

fdisk reports the following:

```
jguy@vivi-mint ~ $ sudo fdisk -l
[sudo] password for jguy: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9276053e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   199229439    99511296    7  HPFS/NTFS/exFAT
/dev/sda3       199229440   201229439     1000000   82  Linux swap / Solaris
/dev/sda4       201230336   234440703    16605184   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdc12f009

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  2930268159  1465133056    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbc12dec2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_cefcbjhbii_3TB'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_cefcbjhbii_3TB: 3000.6 GB, 3000599052288 bytes
255 heads, 63 sectors/track, 364802 cylinders, total 5860545024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0xbc12dec2

                         Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cefcbjhbii_3TB1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

Screenshot from gparted:

[http://jemstuff.com/stuff/nixstuff/gparted1.png](http://jemstuff.com/stuff/nixstuff/gparted1.png)
(by the way, ntfsprogs was installed already)

```
jguy@vivi-mint ~ $ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 265 not upgraded.

```

I looked into fakeraid but I'm not sure that had what I'm looking for. I don't actually need to boot anything on my RAID, I just need to mount it in Linux. 

Any help is appreciated.

thanks!

---

### Post by oldfred on 2012-04-15
I do not know RAID, but it is my understanding that you do not use gparted on RAID partitions.

NTFS-3g merged with ntfsprogs. I think someone posted that now if you install ntfsprogs you get the older version and it uninstalls ntfs-3g. Check that you still have NTFS-3g.

---

### Post by Jguy on 2012-04-15
Sorry for the double post, I should add:

fstab looks like this:

```
# lets see if this works. Mounting DOCS (2TB) RAID partition on /mnt/docs.
/dev/mapper/isw_cefcbjhbii_3TB2 /mnt/docs       ntfs    none    0       0

```

when I try to mount:

```
jguy@vivi-mint /etc $ sudo mount -a
mount: special device /dev/mapper/isw_cefcbjhbii_3TB2 does not exist
```

---

### Post by Jguy on 2012-04-15
After I do:
```
jguy@vivi-mint ~ $ sudo apt-get install ntfs-3g
[sudo] password for jguy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ntfsprogs
The following NEW packages will be installed:
  ntfs-3g
0 upgraded, 1 newly installed, 1 to remove and 265 not upgraded.
Need to get 549 kB of archives.
After this operation, 815 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

```
I get:
```
jguy@vivi-mint ~ $ sudo mount -a
ntfs-3g: Failed to access volume '/dev/mapper/isw_cefcbjhbii_3TB2': No such file or directory

ntfs-3g 2011.4.12AR.4 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 7, XATTRS are on, POSIX ACLS are on

```

with the same as above in fstab.

---

### Post by oldfred on 2012-04-15
fdisk does not work with gpt. Not sure what works best with RAID, but for gpt use either of these, you may have to download gdisk. Use sda or sdb:

sudo parted /dev/sda unit s print
sudo sfdisk -l -uS
sudo gdisk -l /dev/sda

---

### Post by Jguy on 2012-04-15
gdisk just seems to show me what I already know. (that the 2TB Partition I need is /dev/mapper/isw_cefcbjhbii_3TB2.)

---

### Post by Perfect Storm on 2012-04-16
Moved to Other OS/Distro Talk.

---

