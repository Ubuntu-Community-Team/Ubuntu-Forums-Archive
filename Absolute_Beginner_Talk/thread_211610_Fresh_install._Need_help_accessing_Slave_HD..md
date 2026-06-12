---
title: "Fresh install. Need help accessing Slave HD."
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by sintryx on 2006-07-08
Hello, my first post on here!
So far very happy with the way ubuntu works, fast, easy, a good package for a complete noob like myself. Having a small problem with accessing a secondary back-up HD I have in this pc. 

Here is the '**sudo fdisk -l**' output:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4249    34130061    7  HPFS/NTFS
/dev/hda2   *        4250        9502    42194722+  83  Linux
/dev/hda3            9503        9729     1823377+   5  Extended
/dev/hda5            9503        9729     1823346   82  Linux swap / Solaris

Disk /dev/hdb: 28.5 GB, 28520497152 bytes
255 heads, 63 sectors/track, 3467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3467    27848646    c  W95 FAT32 (LBA)

And here is the contents of my '**fstab**':

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I've tried looking around on forums before asking, came across a few solutions like this one: **[http://www.ubuntuforums.org/archive/index.php/t-22046.html](http://www.ubuntuforums.org/archive/index.php/t-22046.html)** However I was unlucky with the results.

Thanks in advance for any advice.

---

### Post by confused57 on 2006-07-08
> **sintryx said:**
> Hello, my first post on here!
So far very happy with the way ubuntu works, fast, easy, a good package for a complete noob like myself. Having a small problem with accessing a secondary back-up HD I have in this pc. 

Here is the '**sudo fdisk -l**' output:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4249    34130061    7  HPFS/NTFS
/dev/hda2   *        4250        9502    42194722+  83  Linux
/dev/hda3            9503        9729     1823377+   5  Extended
/dev/hda5            9503        9729     1823346   82  Linux swap / Solaris

Disk /dev/hdb: 28.5 GB, 28520497152 bytes
255 heads, 63 sectors/track, 3467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3467    27848646    c  W95 FAT32 (LBA)

And here is the contents of my '**fstab**':

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I've tried looking around on forums before asking, came across a few solutions like this one: **[http://www.ubuntuforums.org/archive/index.php/t-22046.html](http://www.ubuntuforums.org/archive/index.php/t-22046.html)** However I was unlucky with the results.

Thanks in advance for any advice.

I believe it's a matter of mounting the HD partition, see this link:
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

Mounting a FAT partition is toward the bottom of the page.

---

### Post by PriceChild on 2006-07-08
Use this code at the end of your fstab:
```
/dev/hdb1	/mnt/data	vfat defaults,auto,**umask=000**,uid=1000,gid=1000 0 0
```
((Where /mnt/data is the place you want to mount the data - make sure this folder is already created!))
then in terminal:
```
sudo mount -a
```

---

### Post by sintryx on 2006-07-08
TY! Editing fstab and mouting it after did the trick.
Thanks again.

---

### Post by Blur-king on 2006-07-08
Hi I have a similar problem but I did not see this post. I complicated my problem by accessing my 2nd HD which is a FAT32 via Disk manager and formatted it to ext3. as a result I was not able to use the methods suggested here, I was promted that there was "superblock" when I applied the methods in this post. Any ideas what to do. Thanking all in advance. BK :oops:

---

### Post by confused57 on 2006-07-08
> **Blur-king said:**
> Hi I have a similar problem but I did not see this post. I complicated my problem by accessing my 2nd HD which is a FAT32 via Disk manager and formatted it to ext3. as a result I was not able to use the methods suggested here, I was promted that there was "superblock" when I applied the methods in this post. Any ideas what to do. Thanking all in advance. BK :oops:

Here's a link to mount a Linux partition:

[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

---

### Post by Blur-king on 2006-07-09
Thanks, it did the trick. Thank you, Thankyou, Thank you. I think may be time to dapper my daughter's box soon. Two down one more to go...

---

