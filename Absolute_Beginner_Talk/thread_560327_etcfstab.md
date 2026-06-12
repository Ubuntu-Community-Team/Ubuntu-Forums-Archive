---
title: "/etc/fstab"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by gramsyn on 2007-09-26
I have edited the /etc/fstab and managed to mount my discs permanently and name them as I like. However, when entering the system, there is a lot of lines stating some problems in  mounting the discs. When it enters everything seems to work fine. I post the output of the "blkid" prompt and the /etc/fstab. Can you tell me what to change in the fstab to correct any possible mistakes?


**~$ blkid**
/dev/hda1: TYPE="ntfs" 
/dev/hda2: UUID="ab13e529-3173-4b72-8605-2286b26f1f5f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="9214-FFE0" TYPE="vfat" 
/dev/hda4: UUID="4b5b248c-0641-4357-925f-7a5ca422b64b" TYPE="swap" 
/dev/hdb2: UUID="46C8-6087" TYPE="vfat" 
/dev/sda: SEC_TYPE="msdos" UUID="3131-0616" TYPE="vfat" 
/dev/hdb1: UUID="46C8-13EA" TYPE="vfat" 
/dev/hda5: TYPE="ntfs" 
/dev/sdb1: UUID="4650-5DD6" TYPE="vfat" 


#** /etc/fstab**: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ab13e529-3173-4b72-8605-2286b26f1f5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=9214-FFE0  /media/backup   vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=46C8-13EA  /media/files    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=46C8-6087  /media/music    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=D85016E75016CC5E /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=4b5b248c-0641-4357-925f-7a5ca422b64b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda5 /media/hda5 ntfs ro,user,fmask=0111,dmask=0000 0 0

---

### Post by mcduck on 2007-09-26
It might help if you changed the last number on your Windows partiton's entry lines from '1' to '0'. It should not be '1' anyway, only root partition should use '1'. All others should have either '2' to run fsck on them after root, or '0' to not run fsck on them at all.

It's a bit hard to tell what's the problem without knowing the error messages you get.. ;)

---

### Post by gramsyn on 2007-09-26
I fixed them the new /etc/fstab is:

----------------------------------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ab13e529-3173-4b72-8605-2286b26f1f5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=9214-FFE0  /media/backup   vfat    defaults,utf8,umask=007,gid=46 0       2
# /dev/hdb1
UUID=46C8-13EA  /media/files    vfat    defaults,utf8,umask=007,gid=46 0       2
# /dev/hdb2
UUID=46C8-6087  /media/music    vfat    defaults,utf8,umask=007,gid=46 0       2
# /dev/hda1
UUID=D85016E75016CC5E /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/hda2
UUID=4b5b248c-0641-4357-925f-7a5ca422b64b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda5 /media/hda5 ntfs ro,user,fmask=0111,dmask=0000 0 0
-----------------------------------------------------------------------------------------------------------------------------

However there is the same error, but I really can't describe what the messages say. They are something like Chinese and then something with problem in mounting.

The problem, I think, is that there are two NTFS partitions, both having Windows. One is working and one is not. The hda5 disc is shown on desctop, while the hda1 not. Can I delete the bottom two lines (the diskmounter line and the hda5 line) without causing any problem?

---

### Post by rsambuca on 2007-09-26
The problem is that a lot of UUID's have changed for some reason.  You must edit your /etc/fstab so that the UUID's are correct, as displayed in the blkid.  As an alternative, you can eliminate the UUID's from you fstab and replace them with the old /dev/hd... designations.

---

### Post by gramsyn on 2007-09-26
i have corrected the UUID, so that the fstab UUID match the blkid. If you can see any problem, please let me know. Can I delete the last two lines in the fstab without causing any problem?

---

### Post by stchman on 2007-09-26
> **gramsyn said:**
> I have edited the /etc/fstab and managed to mount my discs permanently and name them as I like. However, when entering the system, there is a lot of lines stating some problems in  mounting the discs. When it enters everything seems to work fine. I post the output of the "blkid" prompt and the /etc/fstab. Can you tell me what to change in the fstab to correct any possible mistakes?


**~$ blkid**
/dev/hda1: TYPE="ntfs" 
/dev/hda2: UUID="ab13e529-3173-4b72-8605-2286b26f1f5f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="9214-FFE0" TYPE="vfat" 
/dev/hda4: UUID="4b5b248c-0641-4357-925f-7a5ca422b64b" TYPE="swap" 
/dev/hdb2: UUID="46C8-6087" TYPE="vfat" 
/dev/sda: SEC_TYPE="msdos" UUID="3131-0616" TYPE="vfat" 
/dev/hdb1: UUID="46C8-13EA" TYPE="vfat" 
/dev/hda5: TYPE="ntfs" 
/dev/sdb1: UUID="4650-5DD6" TYPE="vfat" 


#** /etc/fstab**: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ab13e529-3173-4b72-8605-2286b26f1f5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=9214-FFE0  /media/backup   vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=46C8-13EA  /media/files    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=46C8-6087  /media/music    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=D85016E75016CC5E /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=4b5b248c-0641-4357-925f-7a5ca422b64b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda5 /media/hda5 ntfs ro,user,fmask=0111,dmask=0000 0 0

Follow my tutorial on mounting partitions.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

