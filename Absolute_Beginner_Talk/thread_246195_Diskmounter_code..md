---
title: "Diskmounter code."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by DrMilo on 2006-08-28
I have 2 lines of code in /etc/fstab:

/dev/hda1 /media/hda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
And:
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

I want to enable read/write in hdb1. I noticed in the one line it's ro verses in the other rw. Can I just alter the line to read rw and get read/write or will that cause some terrible problem?

---

