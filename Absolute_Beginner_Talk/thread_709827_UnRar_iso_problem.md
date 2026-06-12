---
title: "UnRar iso problem"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by gelima on 2008-02-27
I am trying to unrar an iso file but I get the following message from Winrar:


    There is not enough space on the disk.
!   Write error: only NTFS file system supports files larger than 4 GB


Is this because the iso is in PAL format?

Thanks,

gelima

---

### Post by bazzawill on 2008-02-27
why are you using winrar for an iso file I would suggest mounting the iso and copy the files off there is a graphical way of mounting in nautillis on these forums but a quick and easy way in a shell is ```
sudo mkdir /media/iso
sudo mount -o loop -t iso9660 (path to iso) /media/iso
```
you can then use the shell or nautilus to copy the files to where you wish

---

### Post by gelima on 2008-02-28
Thanks for your help! 
orry I'm new in yhis topic..I have 87 rar files and when I try to Unrar them apparently they will become an iso file... The only software I know for Unrar is WinRar... is nautilus a better way to do this?

Thanks,

GELIMA

---

### Post by bazzawill on 2008-02-28
Ah I see what you want is unrar winrar is a windows version of rar so using the windows version of a linux problem would probably cause problems. So install unrar and in a terminal type
```
sudo  apt-get install unrar
```
you will need to have activated the restricted repositories from System > Administration > Software Sources, enable universe, multiverse and restricted.
Then you can open you're rar files by double clicking them in nautilus.

---

### Post by gelima on 2008-02-28
Thanks, I am using Windows Vista with Winrar... the problem is that I never get the iso file extarcted I, instead I get the message posted above... is this a Winrar problem or there is somenthing wrong with the rar files?

Regards,

---

### Post by kellemes on 2008-02-28
> **gelima said:**
> Thanks, I am using Windows Vista with Winrar... the problem is that I never get the iso file extarcted I, instead I get the message posted above... is this a Winrar problem or there is somenthing wrong with the rar files?

Regards,

You're trying to unrar an iso on a FAT32-disk maybe?
FAT32 won't except files larges than 4Gb.

Unrar the iso to an NTFS-disk and all will be fine..

---

### Post by gelima on 2008-02-28
Thanks! 
Excuse me for the ignorance... what is a NTFS Disk?

---

### Post by kellemes on 2008-02-28
> **gelima said:**
> Thanks! 
Excuse me for the ignorance... what is a NTFS Disk?

O well.. it's just the filesystem-format..
So when you look at the properties of your disk/partition from Windows Explorer you'll see in what format it's formatted.. these days NTFS is default for Windows, in the past it was FAT and Linux uses it's own filesystem-formats like ext2, ext3 or reiserfs.


Anyway, try to unrar (extract) the iso to a NTFS formatted disk (could very well be C:\ ) and see how it goes

---

### Post by gelima on 2008-02-28
Thanks again! I will try that

---

