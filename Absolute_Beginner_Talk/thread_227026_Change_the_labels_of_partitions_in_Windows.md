---
title: "Change the labels of partitions in Windows?"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by l0l on 2006-08-01
Well, I tried to reinstall Ubuntu yesterday, but it failed both times. Now I see that the partition thingy has messed with the partitions. Before yesterday, my NTFS partition was assignes the label H: and the "games" partition was G:; however, after my unsuccessful attempt to install Ubuntu again, the labels have been swapped, so that the NTFS partition is now G:. Why did this happen and how can I change them back?

---

### Post by aysiu on 2006-08-01
I don't know why this happened, but I don't think you can swap them back unless you magically (and accidentally) do the reverse of what you did before or you physically remove the G: drive and then add it back again.

Windows, like Ubuntu, will assign drive names in the order they appear. If you have a drive called G: and then add another drive, that drive will be H:

Likewise, in Ubuntu, if you have a drive that's /dev/hda1 and add a second drive, it'll be /dev/hdb1.

---

