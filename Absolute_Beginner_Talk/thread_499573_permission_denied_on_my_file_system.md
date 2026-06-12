---
title: "permission denied on my file system"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ve3rpm on 2007-07-12
Okay, I've been playing with 7.04 on and off for a few weeks now.  Finally decided to upgrade everything.  3.2 gig dual core, 320 gig hdd, and 100 gig secondary hdd.  Now that I've wiped the 320 gig, I want to transfer all of the files from my 100 gig so that I can wipe it as well and start fresh.  The problem here is that I don't have permission to write to my hda1 drive.  I've read lots of posts, and I initially formatted it with gparted as fat 32.  The install however reformatted it.  Any suggestions?

---

### Post by wormser on 2007-07-12
I think you need to have ntfs-3g installed to write to that drive.  I was a little confused by your description but give it a try.

```
sudo apt-get install ntfs-3g
```

Then go to Applications> System Tools> NTFS Configuration Tool

---

### Post by ve3rpm on 2007-07-13
Okay, it's not an ntfs drive.  there is no windoze on this at all.  Perhaps it's not that I want to write to the file system so much as my main hdd is invisible.  File system is there as well as my desktop, but it's like it's hidden.  I can't see 7.04 formatting to ntfs.

---

### Post by phr0ze on 2007-07-13
So it's not mounted?

---

### Post by ve3rpm on 2007-07-13
Okay, it seems that it's not mounted, cause I can't see it.  Now I've just booted up from the cd, and my hdd is there, but oddly enough even now it's still only read only

---

