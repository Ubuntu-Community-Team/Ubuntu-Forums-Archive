---
title: "fsck every boot and bad magic number"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by DMcA on 2007-12-05
I've just installed gutsy and managed to get everything sorted out and working I think, except that every single time I boot up fsck is run on all my partitions. 

I've tried running 

```
sudo tune2fs -c 30 /dev/sda3

```

but this rather worryingly returns:

```
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Bad magic number in super-block while trying to open /dev/sda3
Couldn't find valid filesystem superblock.

```

The same thing happens on other partitions. 

I know I can prevent fsck from running at all by setting the last column of my /etc/fstab to 0 but I would quite like to have fsck run automatically every once in a while. Assuming  I have to set the last column of fstab to 0, is there some other way I can achieve this? 

I'm guessing there might be a problem with my fstab but it looks fine. I've stuck it below anyway. 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f240c440-b4f2-446f-a615-f30d23669d73 /               reiserfs notail          0       0
# /dev/sda6
UUID=e9bf731d-a78f-42aa-9165-503f90488ca5 /home           reiserfs defaults        0       0
# /dev/sda1
UUID=3007-17F2  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda2
UUID=320D-180E  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=11d01fdb-90f1-41e3-a65f-22ad67fa14e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Any ideas?

---

### Post by philinux on 2007-12-05
Read through this.

[http://www.bellevuelinux.org/superblock](http://www.bellevuelinux.org/superblock)

---

### Post by schorsch on 2007-12-05
tune2fs works on ext2/3 filesystems but according to your /etc/fstab /dev/sda3 is an reiserfs ....

---

### Post by DMcA on 2007-12-05
ok so the tune2fs output is irrelevant then, cheers. 

I've still got the problem of fsck running on every boot. From what I've been able to find out it seems like this can be a bug of some sort but I never had any issue with it  on feisty. Having disabled it, is there any way to run fsck periodically? I've been reading about autofsck but I don't see how that'll work if my computer wants to run fsck every boot anyway.

---

