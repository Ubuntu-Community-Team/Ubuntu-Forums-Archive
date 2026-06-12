---
title: "formatting ext hard drive to ext3 and still read only"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by alexmoon on 2007-04-21
I just got a new 80gb external hard drive, and formatted it with gparted to ext3. When I tried to access it, it had a folder on it called 'lost + found' with nothing in it that I could see, and it was read only. I'm using FAT32 now, which works ok but won't copy some of my files (those with punctuation in the name and html files, as far as I can tell). Would ext3 be any better for this? And how could I get it working?

---

### Post by heimo on 2007-04-21
Try these:
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Rospo Zoppo on 2007-04-21
Maybe you don't have permission to write...

---

### Post by medad on 2007-04-21
I used gparted to split up my 300GB hard drive.  I also saw the lost and found on all of my ext3 partitions, but when I loaded up the Ubuntu, I had no problems getting into my home folder.  I just leave the lost and found file alone.  It doesn't seem to have any affect.

---

### Post by bodhi.zazen on 2007-04-21
LOL

good question. The "lost and found" directoy is a "system directory" if you will.  So you do not have permissions (acces) as a user. It is used to track and store potentially dammaged fiiles if your system is not shut down properly.

Do not move it.

FYI :

[http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/lostfound.html](http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/lostfound.html)

---

### Post by alexmoon on 2007-04-21
Ok...now I tried to format it to ext3 from FAT32, to try suggestions...and it's coming up in gparted as an "unknown" filesystem. It still seems to be working fine for copying files, though. Weird.

---

