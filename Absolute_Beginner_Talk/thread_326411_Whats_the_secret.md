---
title: "Whats the secret?"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by darco on 2006-12-27
Whenever I try to transfer a large file (4gb or more) FROM Windows to Ubuntu it always fails around 90 percent complete. I have transferred larger files in the past. My Win drive is NTFS and I am transferring to a VFAT drive (hmm, did I just answer my own question?)
Any help would be appreciated...
thxs

dr

---

### Post by spockrock on 2006-12-27
> **darco said:**
> Whenever I try to transfer a large file (4gb or more) FROM Windows to Ubuntu it always fails around 90 percent complete. I have transferred larger files in the past. My Win drive is NTFS and I am transferring to a VFAT drive (hmm, did I just answer my own question?)
Any help would be appreciated...
thxs

dr

if the filesystem is fat32, the max file size is 4GB.  Its a limitation of the fat32 filesystem. if you can read an ntfs file system, then try copying the file to  the ext3/2 or what ever filesystem you maybe using.

---

### Post by darco on 2006-12-27
Ya I experimented and transferred it to my Ubuntu desktop w/o a prob...
thxs
dr

---

### Post by silvercliff on 2007-01-05
i am getting this problem, but my circumstances are a little diff.  I have a 5.5 gig file on my main comp (ubuntu 6.10) to my file sever (6.04 or 5, the one before 10) via a samba share which i have automounted on startup.  it get a 2.0gig file limit error.  is there a way to change it?  both file systems are using ext3.

---

