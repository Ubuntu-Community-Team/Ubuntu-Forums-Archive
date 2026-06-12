---
title: "Formating to ext3 from ntfs ?already mounted?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by sYs^ on 2006-04-05
Hi!

I used to have a HDD with NTFS filesystem, but I decided yesterday to change it to ext3 so I saved my files to another hdd then I started the partitioner from my Dapper install disc, I simply removed the NTFS partition and created an ext3 filesystem with default settings, everything went fine but when I wanted to mount it after the restart on my Dapper system:

```
root@ubuntu:~# mount /dev/hdb1 /home/dani/storage1/
**mount: /dev/hdb1 already mounted or /home/dani/storage1/ busy**
root@ubuntu:~#

```

It isn't in fstab.

```
root@ubuntu:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/hdc1    /home/dani/windows/c    ntfs-fuse    auto,uid=1000,gid=1001,umask=0007    0    0
/dev/hdc4    /home/dani/windows/g    ntfs-fuse    auto,uid=1000,gid=1001,umask=0007    0    0
/dev/hda1    /home/dani/windows/d    ntfs-fuse    auto,uid=1000,gid=1001,umask=0007    0    0
/dev/fd0     /media/floppy0                       auto    rw,user,noauto  0       0

root@ubuntu:~#
```

fdisk -l:
```
root@ubuntu:~# fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14946   120053713+   7  HPFS/NTFS

[B]Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  83  Linux[/B]

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1399    11237436    7  HPFS/NTFS
/dev/hdc2            1400        3721    18651465   83  Linux
/dev/hdc3            3722       14945    90156780    f  W95 Ext'd (LBA)
/dev/hdc4            3825       14945    89329401    7  HPFS/NTFS
/dev/hdc5            3722        3824      827316   82  Linux swap / Solaris
root@ubuntu:~#
```

It's a *Maxtor 6Y120L0*.

Any ideas? Thanking you in anticipation.

---

### Post by taurus on 2006-04-05
You can boot your system with a LiveCD.  Then use fdisk to remove that partiton and create it again.  Then, format it as ext3 and see if you still have the same problem.

---

### Post by sYs^ on 2006-04-05
Thanks for the answer, I'll try that in 10 minutes.

Here's some more info for the investigation :p

If I try to change something on that disc with Gparted there's a lot of errormessages like this:

```
Error reading inode 36465.
Error reading inode 38131.
Error reading inode 38161.
Error reading inode 39653.
Error reading inode 45861.
Error reading inode 51631.
Error reading inode 51674.
Error reading inode 51685.
Error reading inode 52134.
Error reading inode 52187.
Error reading inode 53075.
Error reading inode 53390.
Error reading inode 55887.

```

---

### Post by taurus on 2006-04-05
Since you are talking about /dev/hdb and there is nothing on it, the best way is to use fdisk from the LiveCD.  Open a terminal and type
```

sudo fdisk /dev/hdb

```
Then use d to delete the old partition and use n to create a new one.  Then use t to change it to 83--Linux filesystem.  Save it and quite with w...  And once you are back to the prompt again, do
```

sudo mke2fs -j /dev/hdb1

```

---

### Post by sYs^ on 2006-04-05
I booted with kororaa-xgl livecd and everything went smootly, it easily created the partition and the filesystem but Ubuntu still doesn't want to mount it :\

---

### Post by sYs^ on 2006-04-05
Oh my god. I can mount it with Windows XP (with Ext2 IFS). I can't understand this.

Edit: Perhaps something is missing from my own kernel because if I load my system with the default ubuntu kernel then it's working. But what shall I add to my kernel?

---

### Post by sYs^ on 2006-04-05
Problem solved according to this thread: [http://ubuntuforums.org/showthread.php?t=103900](http://ubuntuforums.org/showthread.php?t=103900)

Thanks for your help!

> First, you need to install package kernel-patch-evms through Synaptic or apt-get or whatever you like to use. This installs the patch in /usr/src/kernel-patches/.

Then, before compiling your kernel, go to /usr/src/linux/, or wherever you keep your kernel source to be compiled, and run this in order to patch the kernel:
Code:

sudo gzip -d 2.6-bd-claim.patch.gz sudo cat /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch | patch -p1

Then compile your kernel as usually and everything will be fine 

---

