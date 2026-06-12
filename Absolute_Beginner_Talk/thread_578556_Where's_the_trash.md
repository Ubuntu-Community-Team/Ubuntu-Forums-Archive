---
title: "Where's the trash?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by nanogeek on 2007-10-17
I have two physical  hard disk drives on my machine. I deleted files from the non-booting slave drive, but they don't show up in the trash, and the disk space is not recovered. I know that when I delete files from my primary HDD, the space is not recovered until I empty the trash, so I suspect that the deleted files from the second HDD are going to an analogous trash. 

Where is the trash from the slave HDD? How do I empty it. I need to recover the space.

Nanogee

---

### Post by bodhi.zazen on 2007-10-17
Trash is usually hidden

It may be in /root/.Trash

Or on your drive /mount/point/.Trash

Show hidden files or use locate

---

### Post by nanogeek on 2007-10-17
Thanks.
I found  in /media/drivename/.Trash-username
From there I was able to delete it from trash and recover my space.
Just out of curiosity, why doesn't the nice trash icon at the lower right hand corner of the desktop have a link to the drive's trash folder? Is there a way to modify this?

---

### Post by Ek0nomik on 2007-10-17
> **nanogeek said:**
> Thanks.
I found  in /media/drivename/.Trash-username
From there I was able to delete it from trash and recover my space.
Just out of curiosity, why doesn't the nice trash icon at the lower right hand corner of the desktop have a link to the drive's trash folder? Is there a way to modify this?

That trash icon is only for your home profile's trash where you have your root directory mounted.

(Ex:  ~/username/.Trash)

The other trash folders are going to be found on each individual device (mount point).  You could add a shortcut to your panel to link to the trash folder of those other devices if you wish.

---

