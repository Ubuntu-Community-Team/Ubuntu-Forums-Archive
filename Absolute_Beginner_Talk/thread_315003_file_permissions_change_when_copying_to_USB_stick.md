---
title: "file permissions change when copying to USB stick"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by shizen on 2006-12-08
Hello, 

I am a user of Ubuntu LTS and I am looking for advise regarding the following problem:

When I back up files to a USB stick via drag'n'drop, the permissions of all files and folders change to

owner: READ+WRITE+EXECUTABLE
no permissions for others

All files on the stick have these permissions. The permissions remain corrupted when I copy the files back to the harddisc.

Right now, the most annoying thing is that all files become executable one. However, I would not mind if there was also a way to preserve all permissions exactly. By the way, the same problem occurs with an external harddisk connected through USB.

I would be glad of someone could help with this issue. Thanks in advance.

Andy

---

### Post by CatKiller on 2006-12-08
The USB stick is probably formatted as FAT. FAT has no support for permissions whatsoever, so happily forgets any permissions that files you put on it may have.

---

### Post by nixclusive on 2006-12-08
compress the files as 'tar' archives to preserve permissions anyway.

---

### Post by shizen on 2006-12-08
Thank you for your help.

Indeed, it was formatted for FAT16. I formatted the stick for FAT32 (to be readable under Windows). This  seems to preserve at least the executable attribute.

TAR is also useful, but in some cases I prefer the file not packed.

Thanks again and have a good day.

---

