---
title: "250 gb hard drive only showing as 127 gb"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by ScarletPimpernell on 2007-07-24
Hi guys,

This isn't a specific Ubuntu problem, but if I can fix it with Ubuntu I'll be rather pleased.

Basically, I bought a Western Digital 250 gig sata drive to install in my main machine. I then installed XP onto it (SP1 I think) and was befuddled to discover that the drive was showing far short of its capacity at only 127 gigs.

I have heard that XP can't recognise drives larger than 127 gb in SP1, but I don't know how to fix it.

My question is, if I format the drive, getting rid of XP completely, and install Ubuntu - will I be able to unleash the rest of my gigabytes?

I'm hoping that Ubuntu will magically save my hard drive, please tell me I'm right. :)

---

### Post by Orochi on 2007-07-24
Easiest way to tell for sure is to pop in the Ubuntu LiveCD and see what it reports the drive's size as.

---

### Post by ScarletPimpernell on 2007-07-24
Good point, well made. I'll give it a try. :)

---

### Post by Nekiruhs on 2007-07-24
> **ScarletPimpernell said:**
> Hi guys,

This isn't a specific Ubuntu problem, but if I can fix it with Ubuntu I'll be rather pleased.

Basically, I bought a Western Digital 250 gig sata drive to install in my main machine. I then installed XP onto it (SP1 I think) and was befuddled to discover that the drive was showing far short of its capacity at only 127 gigs.

I have heard that XP can't recognise drives larger than 127 gb in SP1, but I don't know how to fix it.

My question is, if I format the drive, getting rid of XP completely, and install Ubuntu - will I be able to unleash the rest of my gigabytes?

I'm hoping that Ubuntu will magically save my hard drive, please tell me I'm right. :)
They must have fixed that (As if microsoft ever "Fixes" anything) in SP2. I happily have 2 250 GB Drives. IF you want XP to use all the space availible, just make some partitions on it that XP can read. But yes, Ubuntu will fix this.

---

### Post by ScarletPimpernell on 2007-07-24
Thanks for your help chaps, I'll give both recomendations a go and report back here with my findings.

---

### Post by Mornedhel on 2007-07-24
I heard XP cannot create FAT32 partitions over 32 GB, that you'd have to use NTFS. I heard this when someone asked me how I managed to get an external drive to be a single 120 GB FAT32 partition (formatted under Ubuntu), they were pretty surprised. Is it true ?

---

### Post by Patrick K on 2007-07-24
It's possible you have a BIOS limitation. Enter the BIOS and see what it reports. If it says 127GiB (or 139GB) then the BIOS will need to be updated.

---

### Post by LaRoza on 2007-07-24
> **Mornedhel said:**
> I heard XP cannot create FAT32 partitions over 32 GB, that you'd have to use NTFS. I heard this when someone asked me how I managed to get an external drive to be a single 120 GB FAT32 partition (formatted under Ubuntu), they were pretty surprised. Is it true ?

FAT32 can support rather large drives, but Windows limits it so force you to use NTFS. (I believe FAT32 can support up to four terabytes, but I am not sure)

-EDIT In theory, FAT32 can support 8 terabyts.

---

### Post by Orochi on 2007-07-24
Yeah I have a 150 gig drive formatted as FAT32 and Windows can read/write to it fine.

---

### Post by Mornedhel on 2007-07-24
> **LaRoza said:**
> Windows limits it so force you to use NTFS.

I did think so.

---

### Post by Patrick K on 2007-07-25
You might want to look at this. It explains the 137GB size limit

[http://www.48bitlba.com/](http://www.48bitlba.com/)

---

### Post by stchman on 2007-07-25
> **Mornedhel said:**
> I heard XP cannot create FAT32 partitions over 32 GB, that you'd have to use NTFS. I heard this when someone asked me how I managed to get an external drive to be a single 120 GB FAT32 partition (formatted under Ubuntu), they were pretty surprised. Is it true ?

FAT32 has a 4 TB partition limit.  FAT or FAT16 has a partition limit of 2GB.  FAT32 has a 4GB file size limit though.

---

### Post by Mornedhel on 2007-07-26
I know about this, I was asking for the confirmation of a software limitation in XP.

---

### Post by G_force on 2007-07-26
windows XP SP2 was meant to resolve the 127gb limit, 
this limit was also present in windows 2000

---

