---
title: "Acronis True Image type program for Linux?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-06-28
Preface: I am a complete Ubuntu Newb.

I use Acronis True Image to backup all my windows computers, using it's full disk/partition image backup functionality.  I am wondering if there is a similar program or built-in function on Ubuntu that allows you to do a complete disk/partition backup?

TIA,
-BassKozz

---

### Post by starcraft.man on 2007-06-28
If you've already paid for Acronis True Image backup suite, then the simple answer is to use that for your back ups (especially if you've already got many backups in their format and don't have time to reimage and move media). I have been using it for a while and it works very well with all kinds of filesystems both from Windows and Linux (just burn the live CD and dump the program off of XP/Windows, then use it from the CD only).

If your looking for open source and free alternatives in an attempt to be more FLOSS, take a look at partimage and ghost4linux. Both are good implementations from what I heard.
[URL="http://www.psychocats.net/ubuntu/partimage"]
Partimage guide here.[/URL]
[List of Drive imaging suites here.]("http://linuxappfinder.com/backupandrecovery/driveimaging")

Thats it, I think that answers your question well.

---

### Post by Atomic Dog on 2007-06-28
I use TrueImage still but only the live cd that you burn with the program.  It does well backing up my system.   If you burned the live CD, you should be able to make good backups of your linux install.

---

### Post by lwh on 2007-06-28
try to have a look at the command called dd
I never tried to use it my self
But beside that, the acronis True image for linux works nicely aswell, and you are still able to create "online" backups of your system.

---

### Post by BassKozz on 2007-06-29
Thanks for all the feedback... I plan on trying a few different methods and see which works best.

Thanks again,
-BassKozz

---

### Post by hyper_ch on 2007-06-29
I don't do disk image backups anymore... I use the power of hardlinks to create a full backup every 6h and dating back for 90 days....

---

### Post by Delirious on 2007-06-29
I have acronis 10 and use the live cd, its incredibly useful for alot of things. But I found that proprietary images of anything but the OS install or intire disk weren't of much use to me and limited what i could do with the backup. So now i use the "drag and drop" method with an external drive, to backup everything but the OS.

> **hyper_ch said:**
> I don't do disk image backups anymore... I use the power of hardlinks to create a full backup every 6h and dating back for 90 days....

Hardlinks?

---

### Post by hyper_ch on 2007-06-29
well, I use rsync to sync the folders I want to backup

and then I make a hardlink copy... basically this will just double the file entry in the table of contents on the harddisk... so, if the file is the same, then multiple backup entries show to the same block of data and hence not eating up each invidiually diskspace....

---

### Post by jmfa59 on 2007-06-30
> **starcraft.man said:**
>  I have been using it for a while and it works very well with all kinds of filesystems both from Windows and Linux (just burn the live CD and dump the program off of XP/Windows, then use it from the CD only).

.

Please make my day tell me that Acronis true Image for windows works also for Linux I really missed that program after shifting to Linux specially the secure zone.

---

