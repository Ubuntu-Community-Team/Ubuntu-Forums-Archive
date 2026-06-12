---
title: "partition suggestions"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-15
Below is an overview of my partition setup at the moment.

if vmware is on hda1 is that included in the size
does it mean there is free space of 13.8 gigs

I am thinking of putting on another os in free space

please advise.

lex1


The number of cylinders for this disk is set to 4864.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4662    37447483+  83  Linux
/dev/hda2            4663        4864     1622565    5  Extended
/dev/hda5            4663        4864     1622533+  82  Linux swap / Solaris


hda1
filesystem ext3
size 36570 mb
used 22687 (62%)
unused 13883 (38%)
flags boot

hda2
filesystem extended
size 1585 mb


hda5
filesystem: linux swap
size 1585 mb

---

### Post by adam.tropics on 2006-07-15
I believe it depends if when creating the vmware device, you told it to allocate all the space then or have it dynamically adjust as required. Either way, you seem to have a rapidly filling disk (so maybe you did allocate vmware?), and with disk usage like that I would question the practical benefit of straining it any more, as it looks like you need the space. What , you have a lot of movies and such?

---

### Post by lex1 on 2006-07-15
no moviesthe size of the vmware disk is about 17/18 gigs

lex1

---

### Post by adam.tropics on 2006-07-15
Then I would think that you allocated it all and it is probably included. Gotta say though, on a 40gb drive, a vmware drive that size seems awfully excessive. Does it really need to be that big. Exactly what are you trying to do? If you are thinking of installing another OS, and you are going to repartition, then why not scrap the vmware altogether?

---

### Post by lex1 on 2006-07-15
yep you probably correct but i could scrap whats on vmware now and make two os's on the vmware.

lex1

---

### Post by adam.tropics on 2006-07-15
Yes you could, I guess it's a matter of weighing up the conveniance and I suppose safety of vmware against a noticable and inevitable performance hit. And that is really personal preference.

---

