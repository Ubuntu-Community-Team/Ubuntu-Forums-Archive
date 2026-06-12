---
title: "A little concerned but mostly puzzled"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Jim D v2.0 on 2007-04-30
I am just a little puzzled.


In my 6.10 install my fstab was :


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdc1
UUID=926d61dd-6d63-4b1d-b80f-c8280c8b1814 / ext3 defaults,erro$
# /dev/hdc5
UUID=43315ab0-f2eb-45c1-ba01-c6c624de2e36 none swap sw $
/dev/hdd	/media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ 		/media/floppy0 auto rw,user,noauto 0 0
/dev/hdb5	/media/drive0 ext3 defaults 0 2
/dev/hdb6	/media/drive1 ext3 defaults 0 2
/dev/hda1	/media/win2k ntfs nls=utf8,fmask=0333,dmask=0222 0 $
/dev/hdb5	/home ext3 nodev,nosuid 0 2

now in 7.04 it is :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=c8ef69e8-74bb-48ce-ba30-657e75a76d3d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=7fc75349-bd80-4801-9bee-1f4e70f6f6bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/media/windows 	ntfs 	nls=utf8,umask=0222 0 	0
/dev/sdb5	/home 		ext3 	nodev,nosuid 	0 	2
/dev/sdb6	/media/drive2	ext3	nodev,nosuid	0	2

Everything seems to be working fine, but, should I be concerned about the change from /dev/hd to /dev/sd? My hardware has not changed at all. Both times this was from a fresh install.

---

### Post by Cypher on 2007-04-30
HDX indicates an IDE device and SDX indicates a SCSI/SATA device, I find it curious that change very curious. However, the change from HDX->SDX seems to be consistent..

It's strange that it's working at all..

---

### Post by yabbadabbadont on 2007-04-30
IDE drives are handled through the SCSI layer in the newer kernel versions.  I think this may be one of the reasons they decided to start using UUID's in the fstab file.

Edit: I should have said that IDE is handled through the SCSI layer for *some* chipsets in the newer kernels.  My IDE drives are still /dev/hd*  However, when I tried out Debian Etch, all my drives showed up as /dev/sd*  It just depends upon which kernel and which options were used when it was built.

---

### Post by NotMeAnyMore on 2007-04-30
Pata or Sata hard drives?

7.10 Is seeing sata drives for what they are and displaying a Sd is what I'm betting.

---

### Post by Jim D v2.0 on 2007-04-30
> **Wiebelhaus said:**
> Pata or Sata hard drives?

7.10 Is seeing sata drives for what they are and displaying a Sd is what I'm betting.

These are IDE drives (ie PATA).

Would the recommendation be to leave things as they are or make changes?

---

### Post by ubnewbie2 on 2007-04-30
> **Wiebelhaus said:**
> Pata or Sata hard drives?

7.10 Is seeing sata drives for what they are and displaying a Sd is what I'm betting.

Yes on my machine with both Sata and IDE Pata drives, it uses sd for the sata and hd for the IDE.

---

### Post by GrueTamer on 2007-04-30
I bet this has to do with that new libata thing in the kernel.  Basically...

hdX -> sdX  sdX -> srX  (the first options are the old ones, in case you're wondering why hdX changes twice ;) )

I'm not really sure, but since Zenwalk on my older computer has a kernel with Libata, I have a little bit of experience with it.

---

### Post by Cypher on 2007-04-30
This is very interesting change in the Kernel. At least, now we know the reason behind things still working though the names have all changed. I must look up more about this when I have some time..

---

