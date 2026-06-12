---
title: "[SOLVED] merge fat partitions?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by kaiju on 2008-01-29
i have two fat partitions i would like to merge without having to erase one of them first.
i did some searching around but found nothing, so i would be curious if one-step merging is possible at all.

thanks in advance for any ideas.

---

### Post by tchoklat on 2008-01-29
all I can suggest is copying the contents of one to the other, deleting that and expanding the second using gparted!

tchoklat

---

### Post by emarkd on 2008-01-29
I've seen Windows software that claimed to be able to do this, but I think what it really did was lots of really small copies/resizes to the disk and partition table.  I've never tried it myself so I can't offer any real guidance except to say that it sounds quite risky and you better have a backup.

The lower risk option is to empty one partition, delete it and then resize the other to take up the newly emptied space.  This involves only one partition table change instead of many, so the risk is a lot less.  Not zero risk, mind you, but a lot less.

Backups are always a good idea.

---

### Post by dgray_from_dc on 2008-01-29
I don't think you're going to find a "one-step" solution.  

Generally, if disks are separated into partitions, it's for a reason.  

As such, I don't think anyone has come up with a tool to merge them.  

It's a good idea though!  

Like tchoklat stated, you're probably stuck with GParted.  

If you can't perform the copy all at once, you may have to do it incrementally.

---

### Post by kaiju on 2008-01-29
ok,
thanks for the feedback, people.

while searching, i saw that this feature had been requested for gparted before, but then i guess it was not worth implementing, or something.

regarding the windows part, i know i used to be able to simply merge with partition magic, that's why i was surprised at not being able to do it under linux.

(hehe, btw one of the partitions had an old winxp install lying on it which i deleted to get some space, but kept the other stuff on it :P )

so the end of the story then, i guess, is that i'll just have to get me some dvd's. ;)

---

