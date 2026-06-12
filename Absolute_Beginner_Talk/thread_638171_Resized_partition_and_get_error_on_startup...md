---
title: "Resized partition and get error on startup.."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-11
Hi,

in the old days when t-rex was around i resized my 300gb HDD from Ntfs to ext3 by shrinking the ntfs and moving data to the new ext3...

well all is fine now my disk is named sdc2 instead of the sdc1 which is understandable..when i reboot it checks for errors and fails...dunno the error code will write it down next time...

has anyone had similar experences with this?

should i move 200+gb data across to another HDD then format it? or is there a fix?

many thanks..

---

### Post by ijason on 2007-12-11
yeah, definitely need to see the error code it spits back. 

are any files accessible on the drive? it may be that your old hard drive is getting near the end of its days.

---

### Post by hopelessone on 2007-12-11
OK i'll leave this alone till i write down the error code...then report back... it's a new HDD this year..

---

### Post by hopelessone on 2007-12-11
it must have logged the error somewhere.. in kern.log i found this:

Dec 11 09:10:37 box-desktop kernel: [  133.423159] sdc2: rw=0, want=4, limit=2
Dec 11 09:10:37 box-desktop kernel: [  133.423165] EXT3-fs: unable to read superblock

i remember something about the superblock on the error..

does this help in any way?

---

