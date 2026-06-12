---
title: "Partition Changing"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Chake99 on 2006-10-24
I thought that there was a tool under system, administration called partition manager/ment but it doesn't seem to exist. Funny.

I was wondering how I would shrink my windoze partition (to nearly nothing) and enlarge my linux partition (which is nearly out of space). Googling found a program called QTparted but the website said it did not support resizing ext3 partitions (odd).

How do I do this?

Yes, I'm aware this is an incredibly nub question.

---

### Post by TitusDalwards on 2006-10-24
do you want to clear windows partition and combine it with linux partition? i don't know how can you do this but i have another idea.

use qtparted and change the file system type of windows partition( for example change it from NTFS to ext3) from now on, you have 2 hard disk,an you can access two of them without any problem.

---

### Post by Chake99 on 2006-10-24
I want to make the windows partition smaller (around 1/4 to 1/3 of its current size, as it is nearly empty) and extend my current linux partition to take up the cleared space (which is nearly full).

I don't want to put two OS's on one partition.

I don't want to reformat my windows partition. Just shrink. (possible?)

---

### Post by ReaderRat on 2006-10-24
> **Chake99 said:**
> I thought that there was a tool under system, administration called partition manager/ment but it doesn't seem to exist. Funny.

I was wondering how I would shrink my windoze partition (to nearly nothing) and enlarge my linux partition (which is nearly out of space). Googling found a program called QTparted but the website said it did not support resizing ext3 partitions (odd).

How do I do this?
I would not advise doing as post # 2 states. Gparted is on the LiveCD, and you cannot change a partition that is being used. Boot the LiveCD and use gparted to resize Windoze.

EDIT: As in any case where you mess with the partitions, BACKUP IMPORTANT DATA first.

---

### Post by brentoboy on 2006-10-24
I second readerRat's idea.

I have used the ubuntu liveCD to successfully "mess" with my partition table.  It was better than the "official" gparted CD that I got from thier site.

Back stuff up first!!!

---

### Post by Chake99 on 2006-10-24
Back up what? I have a music collection, and I guess I could back up my school work but what is the chance of gparted really failing?

Not to mention I don't really have any good way of backing up my system :(

---

### Post by CatKiller on 2006-10-24
[The latest version of GParted]("http://gparted.sourceforge.net/livecd.php") is able to move ext3 partitions which, as far as I know, the version on the Ubuntu cd can't. As has already been mentioned, you can't fiddle with a partition that's mounted, so you'll need to use **some** kind of live cd.

---

### Post by brentoboy on 2006-10-24
> **Chake99 said:**
> Back up what? I have a music collection, and I guess I could back up my school work but what is the chance of gparted really failing?

Not to mention I don't really have any good way of backing up my system :(

Rule of thumb for smart computer administrators:  Ignore the odds, even when they are in your favor.  Assume that any and all possible outcomes each have 50% chance of occurring.   If you data is not worth a flip of a coin, then dont worry. 

If it would be an inconvenience to back it up, and recreating it from scratch isnt scary, fine, so long as you accept that before you go swapping partitions.

Honesly though, what chance do I give it?
I give you about 95% "perfect" run no issues
2% some minimal data loss
and 2% one of the paritions gets hosed and you loose everything on it
with the remaining 1% you loose everything on the PC as it is today, please reformat and start over.

But dont go in unless you are prepared to accept equal chance for any and all of those scenarios.  The 95% perfect success generally only happens for the guy who took all those precautions in the first place.

-b

---

