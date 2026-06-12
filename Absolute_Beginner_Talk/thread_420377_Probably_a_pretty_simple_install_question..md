---
title: "Probably a pretty simple install question."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by ScornForSega on 2007-04-23
Well, Feisty likes my board as Edgy didn't seem to care for it too much, and Feisty will give me the live install with the option to install to disk.

My PC has three physical drives.

sda: NTFS Windows partition
sdb: Was openSUSE ext3 install, but removed the partitions after encountering access issues doing an overlay install with Feisty.  
hda: NTFS storage drive

Now, the way I've had this working is to use GRUB as my primary boot loader which I think was coming off of sdb.  I very well could have installed GRUB to sda and forgotten which might be the case.

Anyway, simple question.  I'm doing a full disk install of Feisty to sdb and when the loader asks on which drive to install GRUB, the default is hd0.  

Am I correct in assuming that:

hd0 = hda
hd1 = sda
hd2 = sdb?

I'd really just like to overwrite my old GRUB configuration without thrashing the NTFS partitions on sda and hda.

---

### Post by bwhite82 on 2007-04-23
You should be able to tell this by which filesystem is on those drives.

---

### Post by annda on 2007-04-23
> If someone wants GRUB on a partition, the 'setup (hd0)' step can be modified to 'setup (hdX,Y)'. Where X is the hard disk, and Y the partition using GRUB's nomenclature of starting from 0 (first partition=0, second=1,...).

i borrowed this quote from here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

