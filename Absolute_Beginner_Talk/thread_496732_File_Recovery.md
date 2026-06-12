---
title: "File Recovery"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by xerox on 2007-07-09
Alright, so here's the situation. I deleted my (windows) hal.dll file (by accident, I thought there actually was a problem with it, but windows has no words for improper partition setup, so it wrote that message instead when I tried to boot it up.. but thats another story..) without backing it up. 

Does anyone know of a file recovery program that works on linux? I made a general google search and it looks like most recovery programs are for windows (dont want to get into complications with wine), so I'd like to get a pointer in the right direction.

---

### Post by brennydoogles on 2007-07-09
> **xerox said:**
> Alright, so here's the situation. I deleted my (windows) hal.dll file (by accident, I thought there actually was a problem with it, but windows has no words for improper partition setup, so it wrote that message instead when I tried to boot it up.. but thats another story..) without backing it up. 

Does anyone know of a file recovery program that works on linux? I made a general google search and it looks like most recovery programs are for windows (dont want to get into complications with wine), so I'd like to get a pointer in the right direction.

Photorec/testdisk can be found in the repos
```
sudo aptitude install testdisk
```
Testdisk can possibly repair your partition, and Photorec can recover files from a corrupted disk.

---

### Post by goatflyer on 2007-07-09
Does this help your immediate problem?

[http://www.dll-files.com/dllindex/dll-files.shtml?hal](http://www.dll-files.com/dllindex/dll-files.shtml?hal)

---

### Post by xerox on 2007-07-09
Probably, i'll extract it and see if it works to boot windows. The problem is more the hal.dll file that got deleted, not the partition thing (I got that fixed right after I deleted the file, when it was too late.. the problem was I left the first partition empty, the one right before the windows partition.. I just had to make it a FAT one .. well, for now.) Anyway, I'll check if that fixes it.

---

### Post by xerox on 2007-07-09
Ok, the problem seems to have expanded to the following files:

hal.dll
ntoskrnl.exe
KDCOM.DLL
BOOTVID.dll

Maybe windows just doesn't have the words to say it's precious hal.dll file is corrupt.

No, what I don't need is a replacement. I need a recovery program to recover the original hal.dll file I had....

Guess I'd better whip out wine.

---

### Post by steve.horsley on 2007-07-09
This may help:
[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

