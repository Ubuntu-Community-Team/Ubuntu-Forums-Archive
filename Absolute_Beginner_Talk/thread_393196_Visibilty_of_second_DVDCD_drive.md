---
title: "Visibilty of second DVD/CD drive"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Bias on 2007-03-25
Hi,

Wondering if anyone can help here.

I have two DVD drives in my machine, one is a read the other read and write.

The first one (read only) shows up in /media as cdrom0 at all times no matter if there is a disc in it or not, it also has a shortcut to it in /media.

The second drive only shows up if it has a non-blank disc in it.

Is it possible to get this second drive to show up in /media at all times just like the first one does?

The reason is to do with copying of discs within wine. Wine also shows the drive only if it has a non-blank disc in it, bit of a shame that as it's a writer and will often have a blank disc in it but of course as it don't exist I can't write to it. I have managed to use it by burning within the ubuntu environment but I would like to do this within the fake windows environment as well.

I have set this up in winecfg but it only shows in there if it contains a non-blank disc.

Any help or pointer would be appreciated.

Nick.

---

### Post by Bias on 2007-03-26
Please,

Anybody?

---

### Post by cowlip on 2007-03-26
that sounds tough.  Could you post your /etc/fstab file? (copy and paste it)

---

### Post by Bias on 2007-03-26
> **cowlip said:**
> that sounds tough.  Could you post your /etc/fstab file? (copy and paste it)

Thanks for the response, I'll post that as soon as I get in this evening about 5 hours time (unfortunately) :)

---

### Post by Bias on 2007-03-26
fstab file as requested:-



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/media/HDD/XP1	ntfs	umask=0222	0	0
/dev/hdb2	/media/HDD/ACRONIS	ntfs	umask=0222	0	0
/dev/hdb3	/media/HDD/FAT32	vfat	umask=0000	0	0


I tried adding:-

/dev/hdd        /media/dvdrom0   udf,iso9660 user,noauto     0       0

by way of an experiment but it didn't like it. Worth a try mind :)

Thanks,

Nick.

---

