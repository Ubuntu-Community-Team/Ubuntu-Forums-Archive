---
title: "Defrag in Ubuntu?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by mmcl on 2008-04-07
Are there any recommendations for a defrag program for Ubuntu?  I used to manually defrag when I had XP installed; I've forgotten the program that I used.

---

### Post by Wyrmboy on 2008-04-07
No you should not need to defrag in ubuntu unless the hard drive is almost out of space

---

### Post by tamoneya on 2008-04-07
ubuntu doesnt require degfragging since it has a ext3 filesystem.  Windows which uses things like FAT32 and NTFS has problems with fragmentation.  In the same way that you dont have to worry about viruses, you also dont have to worry about fragmentation.

---

### Post by SunnyRabbiera on 2008-04-07
You really dont need one, the file system in Ubuntu does not fragment or at least not nearly as bad as windows.
Now there is a tool for you pre installed that checks the system for faults called fsck, it will come up during boot every so often (normally once in 22 times, more or less)

---

### Post by tubasoldier on 2008-04-07
The ext3 filesystem is a JOURNALED system. In other words it keeps track of your files much better. The only time I have noticed any fragmentation that made me wonder was when I had very large files. The reason for that was because they were spread across multiple sectors of the disk.

Don't worry about fragmentation in Linux. It is pretty well managed. Also fsck is really more similar to scandisk.

---

### Post by SunnyRabbiera on 2008-04-07
> **tubasoldier said:**
> The ext3 filesystem is a JOURNALED system. In other words it keeps track of your files much better. The only time I have noticed any fragmentation that made me wonder was when I had very large files. The reason for that was because they were spread across multiple sectors of the disk.

Don't worry about fragmentation in Linux. It is pretty well managed. Also fsck is really more similar to scandisk.


true, though if it detects a bad file it can help rectify it.

---

### Post by mrsteveman1 on 2008-04-07
NTFS is also journaled, which really has little to do with fragmentation.

EXT3 doesn't fragment as badly because it attempts to write blocks to disk in such a way that fragmentation is not as common, however it does happen, and fsck.ext3 will show you how fragmented the disk is if you force check.

Until recently i had a 250gb ext3 partition that was over 2 years old, before i moved all the data the filesystem was both nearly full and fsck showed over 15% of the disk to be non-contiguous. Thats a pretty low number considering all the small files and the fact that it was mostly full, so it does say something about how well ext3 keeps track of individual files.

---

### Post by FragViper on 2008-04-08
I found ext3 to get extremely fragmented when using large files (50MB-8000MB) so I switched to the XFS filesystem instead, which works better for large files and you can defrag it manually.
Otherwise there is a thread here: [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)
I haven't tested it though...

---

### Post by articpenguin on 2008-04-08
> **FragViper said:**
> I found ext3 to get extremely fragmented when using large files (50MB-8000MB) so I switched to the XFS filesystem instead, which works better for large files and you can defrag it manually.
Otherwise there is a thread here: [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)
I haven't tested it though...

all files above 128MB will fragment in ext3 because ext3 divides the space into block groups.

---

### Post by Hendrixski on 2008-04-08
Real operating systems don't need to defrag.  There are no defrag utilities that come with Mac either.  Ubuntu is just easier to use than windows because you don't have to worry about a lot of that kind of crap.

---

### Post by Therion on 2008-04-08
This is the best explanation I've run across that explains [Why You Don't Need to Defrag](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting) Linux operating systems.  With visual aids!!

---

### Post by bred on 2008-04-08
> **Hendrixski said:**
> Real operating systems don't need to defrag.  There are no defrag utilities that come with Mac either.  Ubuntu is just easier to use than windows because you don't have to worry about a lot of that kind of crap.

[COLOR="Blue"]way to go dude :)
:lolflag:
[/COLOR]

---

