---
title: "What´s The Difference???"
date: 2005-06-10
forum: Absolute Beginner Talk
---

### Post by LongTooth on 2005-06-10
I´m posting this question here thinking it might be usfull to newbies and also to find and answer. 

Results of df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              38G  3.2G   33G   9% /
df: `/media/floppy': No medium found
df: `/media/cdrecorder': No medium found
df: `/media/cdrom': No medium found


Results of df -H:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/hda2               41G   3.4G    35G   9% /
df: `/media/floppy': No medium found
df: `/media/cdrecorder': No medium found
df: `/media/cdrom': No medium found


I have a 40Gb HD. So I figure the df -H is closer to what I really have. Why the difference? What is the difference between --h and --H? Why a 3G difference?  

Thanks.

---

### Post by bored2k on 2005-06-10
> Show information about the filesystem on which each  FILE  resides,  or
       all filesystems by default.

>  -h, --human-readable
              print sizes in human readable format (e.g., 1K 234M 2G)


> -H, --si
              likewise, but use powers of 1000 not 1024


For more information, man df.

---

### Post by LongTooth on 2005-06-10
Thanks. I´ll check it out.

---

