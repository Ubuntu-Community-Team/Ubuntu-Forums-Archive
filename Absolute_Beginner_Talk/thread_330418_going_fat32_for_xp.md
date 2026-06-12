---
title: "going fat32 for xp?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by sm1thson on 2007-01-03
Im new to ubuntu, i recently reformatted my laptop (win xp) as it was running slow, and i then installed ubuntu in dual boot. i realise now that i cant share my files from the ntfs part of the drive. i see that if i convert this to fat32 would be able to. (1)-is fat32 the best thing to use in my situation?

so i plan to either back up to another PC (slow) reformat my XP again (not something i want to do as ive just got it running right), or i could partition the drive (in gparted) move my files over (fast), reformat, then reinstal etc.

(2)-can anyone think of a better way? -is there a tool to convert the drive to fat32?

(3)-does winxp give the option to format in fat32 (i dont remember) -or do i format it in gparted then just install xp on it?

---

### Post by xyz on 2007-01-03
This is how I did it and it works fine for my needs:
> /dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs-3g defaults,locale=en_US.utf8   0    0 


/dev/hda3       /media/hda3  vfat iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0    
hda2 ext3 Ubuntu
hda1 ntfs with read/write
hda3 Fat32 sharing partition
This is on an 80G HD
I like GParted and it will format things the way you want them to be.

---

### Post by aberry5555 on 2007-01-03
You can read/write ntfs using a 3rd party program called NTFS 3g. read here [http://www.ubuntuforums.org/showthread.php?t=330375](http://www.ubuntuforums.org/showthread.php?t=330375)

---

### Post by spietros on 2007-01-03
Make 3 partitions:

1 with ext3 and Ubuntu
1 with FAT32 for the files which can be accessed/written both in ubuntu and win
1 with NTFS with WINXP on it.


This is my actual situation.

Bye

---

### Post by viciouslime on 2007-01-03
Partition magic for windows will let you convert fat32 back to ntfs if you do want to do it that way.

---

### Post by sm1thson on 2007-01-03
yeah, another thing i only have a little un (40gb) so i really dont want another partition shrinking things down.

i have read about NTFS-3g but i dont like the idea of it been beta, running beta programs and having them crash doesnt normally bother me, but something screwing up my harddrive that i use for work would!

hmm so partition magic can convert? is there any linux tools that can convert? (i would expect to hit problems with windows converting itself unless partition magig can be run off some kind of live disk?).

---

### Post by xyz on 2007-01-03
There are other ways but...
[GParted]("http://gparted.sourceforge.net/")
Thx for reading the (previous) posts....

---

### Post by sm1thson on 2007-01-03
i have used gparted (when i did my xp install i partitioned the drive ready for ubuntu -not realising how linux filesystems worked!, i used gparted to put it right it was a nice easy to use tool!) but i cant see how to convert my xp ntfs drive to fat32 with gparted without it wiping/formating the data? or are you suggesting i use gparted rather than xp to format because now i know i can convert with partition magic i want to convert not reformat but i would rather do it linux stylee!

---

