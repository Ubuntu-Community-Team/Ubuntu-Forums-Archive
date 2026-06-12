---
title: "large fat32 partitions"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2007-03-06
I have a machine with a 300gb drive on it that I need fully shared between the xp machine it sits in and my linux machine.

One thing I was thinking about was limiting the XP system to a 20gb partition and then using linux to format the rest of the drive as FAT32. I'll have no files on the machine over 4gb in size so that is nothing to worry about.

Alternatively, I could put my faith in NTFS writing over a network......

what do you think?

Will XP play nicely with a large fat32 partition? I am struggling to find info about this online

cheers
John

---

### Post by endtroducing on 2007-03-06
I have a 500gb formated in fat32. I have files larger than 4gb on it. Never had a problem.

---

### Post by stchman on 2007-03-06
> **pompeyjohn said:**
> I have a machine with a 300gb drive on it that I need fully shared between the xp machine it sits in and my linux machine.

One thing I was thinking about was limiting the XP system to a 20gb partition and then using linux to format the rest of the drive as FAT32. I'll have no files on the machine over 4gb in size so that is nothing to worry about.

Alternatively, I could put my faith in NTFS writing over a network......

what do you think?

Will XP play nicely with a large fat32 partition? I am struggling to find info about this online

cheers
John

XP plays very well with FAT32.  FAT32 has some security issues, but you can read/write to FAT32 with both linux and XP.

NTFS is a journalised file system so you can run into trouble with writing to it from another source.  NTFS writing is still beta in linux.

---

### Post by pompeyjohn on 2007-03-06
Thank you very very much!

I love this community :)

Although this machine will have to be XP and with the fat32 partition, my laptop will continues to give me lots of I love Ubuntu moments :)

---

### Post by dvarsam on 2007-03-06
[QUOTE=endtroducing]I have a 500gb formated in fat32. I have files larger than 4gb on it. Never had a problem.[/QUOTE]

How did you format the FAT32 Drive?
I.e. Windows max FAT32 Partition size is 32GB?

What program did you use to format such a big FAT32 Partition?
Thanks.

---

### Post by pompeyjohn on 2007-03-06
Not sure how endtroducing (is that a DJ shadow reference? sweet :) ) did it...

...I am in the process of formatting the drive now using gparted... it is going ok so far ...

---

### Post by Patrick K on 2007-03-06
I formatted partitions at 37GB using Seagate's disk tools. W98 has no problems with this. I don't know what the limit might be. Apparently, 500GB is doable. I'm not so sure about the over 4gb files size, though.

---

### Post by endtroducing on 2007-03-09
> **dvarsam said:**
> How did you format the FAT32 Drive?
I.e. Windows max FAT32 Partition size is 32GB?

What program did you use to format such a big FAT32 Partition?
Thanks.

Not anymore... FAT32 volume can theoretically be about 8 terabytes when using 32k clusters. I don't think it's recomended however. ;)

I use FAT32 so my sister can read my drive when connected to Mac OS.

FDISK was used...

---

### Post by endtroducing on 2007-03-09
> **pompeyjohn said:**
> Not sure how endtroducing (is that a DJ shadow reference? sweet :) ) did it...

...I am in the process of formatting the drive now using gparted... it is going ok so far ...

It is indeed. :)

---

