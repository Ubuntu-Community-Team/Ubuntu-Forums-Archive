---
title: "Re: Unable to Use Games with More than One Disk"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-08
Also, and I know this is totaly unrelated, but I can't get Wine to install games with more than one disk.  When I go to pop in the second disk, it gives me an error saying it can't find the new disk.  I would really like to install some of my games, but this makes it really difficult.

---

### Post by MasterOfDisaster on 2006-11-08
This is known problem with wine.  One solution is to copy all the files on all the disks to a directory, and run the .exe from there.  Note: I'm not sure if this works for all games, but does for World of Warcraft (the only game I've bothered with under Wine).

---

### Post by CatKiller on 2006-11-08
If that doesn't work, it's not too hard to make ISO images of the disks and then mount them in turn to the mount point you've told Wine contains a cd drive. When it asks you to change disks, you open a terminal, unmount one image, mount another, and then go back to your install.

---

### Post by YokoZar on 2006-11-08
Are you using the newest Wine?  There was a bit of a problem with HAL in versions of the packages I made until pretty recently.

---

