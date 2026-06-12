---
title: "Your experience restoring Win/Ubuntu from image?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-26
Using the Ubuntu Live CD + Partimage, I backed up both Windows XP Home and Dapper.

However, I always installed or reinstalled or
```
tar xvpzf backup.tgz -C /
```
and I'd like to find out if you've already restored it that way and how it went.
Thanks.

---

### Post by bluefrog on 2006-09-26
Well apparently you did the job so tell us how it went...

Personally I boot on systemrescuecd, launch partimage and restore from there. In 2 minutes the inital OS is back online.

James

---

### Post by xyz on 2006-09-26
> **bluefrog said:**
> Well apparently you did the job so tell us how it went...

Personally I boot on systemrescuecd, launch partimage and restore from there. In 2 minutes the inital OS is back online.

James

Thanks for the feedback! I probably didn't express myself clearly!
I aimed to find out IF people had restore their system(s) from a backup image, for instance with Partimage because I never did restore from the image...only install,reinstalled and tar...
So I can't speak of my own experience since I have yet to use that method.

Restoring the Win NTFS that way...no problem?

---

### Post by dsauter on 2006-09-26
I have a MythTV setup that I can't bear to lose (it takes so much time to get it just right).  My solution is to have a spare partition and to copy the entire root partition to it using the Ubuntu install CD.  On the alternate install CD (I don't know about the normal install CD) there is an option in the partitioning dialog that lets you copy the contents of an existing image.  Every so often when I like my setup, I pop in the Ubuntu install CD and copy the entire partition onto the spare partition and call this my backup.  (then I back out of the install)

I have had to restore from this image, and it was painless.  All I had to do was copy the spare partition image back to the root partition and reboot.  It's not elegant, and it's kind of a waste of a partition, but it paid for itself with my last screwup.

I guess I should add that all my data files (and my mythtv database) are on their own partitions (one for important data, one for TV shows etc.).  These partitions use a totally different backup method that can be done automatically much more frequently.

---

### Post by xyz on 2006-09-26
Thanks for letting me know dsauter! I appreciate your explanation of how you did it.

---

