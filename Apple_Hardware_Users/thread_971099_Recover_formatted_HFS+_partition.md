---
title: "Recover formatted HFS+ partition?"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by Kopachris on 2008-11-04
I accidentally formatted the HFS+ partition where Mac OS X was installed while I was installing Ubuntu 8.04.  I thought I backed up all of my data on my external hard drive, but I just found out that the folders that were in "Documents" are gone.  The Ubuntu 8.04 installer formatted /dev/hda3 from HFS+ to HFS with the flag "boot".  That was 4 days ago.  Does anyone know of a program (preferrably free, but even a trial would be great) for Linux that can recover my data from the HFS partition, or am I totally screwed?  I know that recovery from formatted HFS+ drives is possible, I just need a free program that runs on Linux that'll do it.  I'm running an Aluminum 17" PowerBook G4 1.67GHz, in case that'll help.:oops:[-o<

---

### Post by DRM_free on 2008-11-05
If you really care about the data, boot from Mac OS X (ie. by re-installing it on an external firewire drive) and get one of the many shareware HFS+ recovery tools that run on OS X.

Since HFS+ isn't a native Linux filesystem, you won't find many recovery programs under Linux.

---

### Post by Kopachris on 2008-11-05
I found one that has a demo LiveCD for PPC (forgot what it's called).  The LiveCD is a Linux based ncurses program.  The demo only has a 64KB limit on the file size.  But it's sloooow.  It was "enumerating files" all night and only got to 14%.  After 15 minutes, it dropped to 12%!  I'm going to read the instructions and then let work while I'm at school.

---

