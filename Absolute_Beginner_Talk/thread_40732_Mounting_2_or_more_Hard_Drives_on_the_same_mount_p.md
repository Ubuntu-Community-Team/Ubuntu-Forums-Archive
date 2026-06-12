---
title: "Mounting 2 or more Hard Drives on the same mount point"
date: 2005-06-10
forum: Absolute Beginner Talk
---

### Post by dmalopsy on 2005-06-10
I was wondering how you would go about doing this without using Hardware RAID 0. Does ext3 support this, and how would I do it. I need to add extra space to my system, but I dont want to mount the extra Hard drive in a different mount point. All I want to do is have 2 hard drives that are mounted on /home

---

### Post by chileverde on 2005-06-10
[QUOTE=dmalopsy]I was wondering how you would go about doing this without using Hardware RAID 0. Does ext3 support this, and how would I do it. I need to add extra space to my system, but I dont want to mount the extra Hard drive in a different mount point. All I want to do is have 2 hard drives that are mounted on /home[/QUOTE]
 AFAIK you can't do that.

What you can do is mounting one inside the ohter, for example:

/dev/hda1 -> /home
/dev/hda2 -> /home/johndoe

hope it somehow helps you :D

---

### Post by tread on 2005-06-10
You might be able to use lvm, though I don't know how!

---

