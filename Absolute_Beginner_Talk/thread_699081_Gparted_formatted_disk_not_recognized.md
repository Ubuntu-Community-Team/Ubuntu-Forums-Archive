---
title: "Gparted formatted disk not recognized"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jimpan on 2008-02-17
I have a external USB drive and I use Gparted to format it as FAT32.  I want to use this drive to transfer PDF and other documents in between Linux and Windows XP.  Ubuntu can mount the disk without any problems.  WHen I connect the USB disk to the XP, is just said it is a unrecognized devices and it is not usable.  I just delete the partition (ext3) and make it FAT32.  Does any one has this issues before? I burned the data to CD as temporary fix.  Please help,  Thanks.

---

### Post by yabbadabbadont on 2008-02-17
Try formatting the drive as FAT32 using XP.  Then it should work fine for both.

---

### Post by hardyn on 2008-02-17
you have to format after creating the Partition.

all the partition too does is make a partition... i personally use cfdisk (but gparted should be fine) to make the partition then format using mkfs -vfat /dev/____
you need sudo for all operations.

works really well.

---

### Post by asmoore82 on 2008-02-17
> **hardyn said:**
> you have to format after creating the Partition.

all the partition too does is make a partition... i personally use cfdisk (but gparted should be fine) to make the partition then format using mkfs -vfat /dev/____
you need sudo for all operations.

works really well.

Actually GParted does everything, partitions AND creates filesystems("formats").

I've seen M$ Windoze fail to recognize perfectly fine formats from GNU/Linux before,
I would take **yabbadabbadont**'s advice

---

### Post by hardyn on 2008-02-17
i have had no trouble with a few disks i have initialized as above.

---

### Post by jimpan on 2008-02-17
I did the following and it is not working.

sudo cfdisk /dev/sda
type = 0B
write
quit

mksf.vfat -I -n /dev/sda1

Ubuntu has no problems what so ever, but I tried Vista 64, XP and windows 2003 without luck.  Is there any low level format on some of the live cd out there.  I would like to give it one more try.  

Thanks for all the posts.

---

### Post by yabbadabbadont on 2008-02-17
If it is a large drive, try using partition type "0C", Win95 FAT32 (LBA), instead.

And if all else fails, format the stupid thing with Windows as previously suggested.  :lol:

---

### Post by hardyn on 2008-02-17
Unless your external is greater than 32gb... then you will need a 3rd party application again.  Windows will not let you create a fat32 partition larger than 32gb,  This is for no good reason however, as there is no size limitation in the spec. for fat32.

---

### Post by yabbadabbadont on 2008-02-18
@hardyn: Good call on that.  I forgot about the 32GB limit in Windows for FAT32.

---

