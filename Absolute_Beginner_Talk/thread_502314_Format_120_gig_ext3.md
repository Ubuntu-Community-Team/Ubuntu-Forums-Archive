---
title: "Format 120 gig ext3"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by tomstark on 2007-07-16
I'm trying to reformat a 120 gig drive from ntfs to ext3 but no luck.  However, I have no problem formatting a smaller drive (40 gig).  I've tried 3 different 120 gig drives with no luck but with two 40 gig drives, all goes as expected.
I'm using gparted.  Is there a problem with formatting 120 gig drives?  If I can reformat a 40 gig drive shouldn't I use the same method for a larger drive?

---

### Post by Famicommie on 2007-07-16
I've formatted a 250 GB drive no problem. Size shouldn't be an issue.
What happens when you try to format the drive? If you get errors, what do they say?

---

### Post by Jixxon on 2007-07-16
I have never had this issue either. I have done many formats at 250-300GBs without error. You might want to try and burn the gparted ISO again. Maybe it is an issue with the CD (?).

---

### Post by tomstark on 2007-07-16
It's a mystery to me.  Originally I tried to install Ubuntu of a spare 120 gig drive but no way to partition or format this drive.  I then tried a 40 gig drive and everything went fine and Ubuntu works fine from that drive.  This is not dual boot and is only running the latest Ubuntu.  I then again tried to format the 120 gig drive.  No go.  Tried another 40 gig, everything goes fine.  Tried yet another 120 gig, no luck.   Then tried a 250 sata and it worked fine.  Tried the 120 yet again and no luck.  All drives were originally used with XP and are (were) formatted to ntsf.

I don't remember the exact error message for the 120, but it mentioned something about the drive being mounted - I did unmount the drive when I attempted to format it and utilized the same process with the 40 and 250 which worked but the 120 didn't work.  All except the 250 are ATA.  (yes, I tried another cable)

---

### Post by wpshooter on 2007-07-16
Get [www.killdisk.com](www.killdisk.com) and WIPE the 120 drive completely clean and the just use the Live CD version of Ubuntu to install and format the drive as a part of the O/S installation.

Good luck.

---

### Post by bigken on 2007-07-16
are you using the gparted liveCD ?


if not try it

---

### Post by insane_alien on 2007-07-16
could always go with fdisk and mke2fs -j

thats never failed me yet. command line tools though, you might not want that.

a possible solution to you problem would be to use the Gparted liveCD and first, wipe the drive, then apply.
then add all the partitions and apply again. that has worked for me.

---

