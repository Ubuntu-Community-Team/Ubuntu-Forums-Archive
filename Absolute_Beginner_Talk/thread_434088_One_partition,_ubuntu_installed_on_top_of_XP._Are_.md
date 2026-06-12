---
title: "One partition, ubuntu installed on top of XP. Are all 'old' files lost?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by kja-bry on 2007-05-05
After having successfully installed ubuntu on two multiple HD PCs, I installed on my main computer where I keep all music/photo files. The installation failed to recognize users from XP, and recommended to use all 400GB on the disk, which I unfortunatley accepted; and (of course, I suppose...) no XP can be found in the grub menu.lst. 

XP is not so important, but is there any way I can recover my photo/music files, provided they are not actually overwritten? :confused:

---

### Post by useLinux, on 2007-05-05
They shouldent be, i think there is a way to get it back and im sure i seen it on the ubuntu support page or documentation. But depending on what option you clicked to install, you may have lost them, one of the options on install was like "delete all files/folders on this drive" or something like that. So if you clicked that you may have lost everything..

---

### Post by toddward on 2007-05-05
If you formatted everything on that one partition I would have to say no.  Sorry dude, that really sucks.  

The only other option would be to go to a data specialist...but they charge out the butt to get data back.

---

### Post by oilchangeguy on 2007-05-05
you can try this:
[http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml)
but i'd say it doesn't look good.

---

### Post by kja-bry on 2007-05-06
Thanks, a small hope still then? What about gnu/ddrescue?

---

### Post by hessiess on 2007-05-06
red this somewere, carnt remember where, dont know if this is corect...

wen you delete a file it dosant actualy delete the file, just sets that space as usable for rewiriting.

dont just beleve this as im not shore if its true.

---

### Post by junjan on 2007-05-06
Check this out

[TestDisk]("http://http://www.cgsecurity.org/wiki/TestDisk") or [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

> 
PhotoRec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.


Sounds promising... :)

---

### Post by oilchangeguy on 2007-05-06
> **hessiess said:**
> red this somewere, carnt remember where, dont know if this is corect...

wen you delete a file it dosant actualy delete the file, just sets that space as usable for rewiriting.

dont just beleve this as im not shore if its true.
you are correct. however windows and ubuntu use different file systems. so when the format is changed, the data may be lost (for most of us). there are data retriveal companies that can (for a hefty price) get the data from just about any hard drive, if the platters are still intact. it just depends on how much you want to spend.

---

### Post by dptxp on 2007-05-06
Never, ever, use a single partition for OS and Data.

You can reinstall OS, change OS, format the OS partition and play around without
the risk of loosing data.

I always use 3- 4 partitions. One for OS and programs,one/ two for data, one for playing around.


And it is always wise to backup your important Data, the cost and time is much less than one professional
data recovery in 20 years. And in data recovery you are exposing your data to others. 

 Hard Disks crash. Oh yes, they do.

---

### Post by darkrose on 2007-05-06
Sorry to be the bringer of bad news but, it's gone for good, Ubuntu formats the drive as ext3 which writes all blank space as binary zeros, So there's nothing there to recover, even with recovery tools or proffesional data recovery services, you can't get anything out of a pile of zeros.

> wen you delete a file it dosant actualy delete the file, just sets that space as usable for rewiriting.
Not an an ext3 filesystem.

---

### Post by cruxx on 2007-05-10
Hi.
I have a similar problem so though I'd tack it onto the end of here. Had XP installed with 3 other partitiond for data. Installed ubuntu for dual boot and that went fine and seemed no problems except obviouosly there was one as now all the xp stuff is gone, all 4 partitions and the rest of the drive now shows as a whole  without partitions. Are they all gone for good or is there any way to recover any of these XP partitions? 
Have no idea how this occured as I thought my data would be ok on seperate partitions....a lot of stuff will be lost if this cannot be fixed :(

thanks.

---

### Post by dstew on 2007-05-10
What do you mean "shows as a whole without partitions"? How are you looking at it? If the drive has a file system on it, it must have at least one partition. Maybe the others are still there. Post the output of **sudo fdisk -l**.

---

### Post by Nekiruhs on 2007-05-10
> **hessiess said:**
> red this somewere, carnt remember where, dont know if this is corect...

wen you delete a file it dosant actualy delete the file, just sets that space as usable for rewiriting.

dont just beleve this as im not shore if its true.
Its true but installing Ubuntu "Formatted" his HD. When you format a Disk it truely erases it (well, almost).

---

### Post by cruxx on 2007-05-10
Sorry, wasn't too clear about the partitions and am a total noob with ubuntu. The drive is 80 gig, I can see a small part for ubuntu and a section for the swap file, the rest of the drive about 73 gig shows as a whole with no xp partitions. I seems as if it has removed them all and now the drive if one blank sheet again. 
Not on that machine at the moment so cannot post actual data but that is how it appears. I have also booted to gparted live cd,  partition magic boot floppy and it shows the same thing, no sign of XP or data partitions.
When I installed it asked me how much of the available drive to use for ubuntu and I pulled the bar down to its minimum of 11 gig and went from there. Things seemed fine until I checked the disk partitions and saw they were gone from my point of view.

---

### Post by kja-bry on 2007-05-12
Update on the lost data; I have run recovery in raw data mode (EasyRecovery), and a lot of the files are still there, so obviously ubuntu has only performed a "soft" formatting; I have for example found ~1GB of .xls files. Problem now is that this dos utility does not recognise my flash drives, so cannot copy the files after the 4.5 hours recovery session.

Could be a solution for lost partitions as well?

Have tried to look for raw recovery options within Linux, but no luck yet. I'd hate to reinstall XP; are there recovery in raw data format in Linux? Knoppix seemed like the answer, but no raw recovery on the CD, at least. Perhaps the DVD?

---

### Post by brennydoogles on 2007-05-12
> **junjan said:**
> Check this out

[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") or [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")




Sounds promising... :)

So I could use these programs to recover data from a corrupted disk as well?? I have a dual boot computer with a corrupted windows drive.

---

### Post by cruxx on 2007-05-15
Update, almost forgot.
I used GetDataBack for NTFS which pretty much got back all my stuff once I'd added another hard drive and reinstalled windows on it to save the data onto.
Looking back, think I did something different on the partition part of the setup but can't be sure, and this may have caused the problem. 

thank for replies.

---

