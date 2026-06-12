---
title: "Root Volume - File System?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by jabzwnein on 2006-11-23
OKay, so after my fiasco with Compiz/Beryl, I decided my computer was screwed up enough to warrant a reinstallation of ubuntu (I'd only switched over two weeks ago anyway).  During installation, I set it to completely erase the old harddrive and start fresh.  However, this installation seems to have done something different.  Namely, under Places > Computer, I get what appear to be two hard drives listed, called "DellUtility:Root Volume" and "Filesystem".  I wouldn't have noticed this if I hadn't installed ubuntu before, but it's my recollection that originally there was just "Filesystem" on the first installation.  What's going on here?  They seem to contain the same files.  Some things are screwy, tho, well, one thing.  The "samples" folder included with ubuntu won't let me do anything to it, it seems to link to the dellutility root.  It even says I'm not the owner, the root is.  Can I fix this somehow?

---

### Post by afbase on 2006-11-23
can you "df" in command prompt for us so we can see what is listed where

---

### Post by jabzwnein on 2006-11-23
elliott@elliott-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             75418912  25964352  45623464  37% /
varrun                  257400        80    257320   1% /var/run
varlock                 257400         4    257396   1% /var/lock
udev                    257400       148    257252   1% /dev
devshm                  257400         0    257400   0% /dev/shm
lrm                     257400     18856    238544   8% /lib/modules/2.6.15-23-386/volatile
elliott@elliott-desktop:~$

---

### Post by afbase on 2006-11-23
it looks like you only have one device listed.  /dev/hda1

is your "DellUtility:Root Volume" listed in /etc/fstab? or listed in cfdisk.  
NOTE: do be careful when you type in cfdisk, it loads a crazy CLI gui that can delete partitions.

---

### Post by jabzwnein on 2006-11-23
running cfdisk gives me a fatal error.  Here are pics of the directory to show you what I get when I check properties:



[IMG]https://mywebspace.wisc.edu/gougeon/pic1[/IMG]
[IMG]https://mywebspace.wisc.edu/gougeon/pic2[/IMG]

---

### Post by jabzwnein on 2006-11-23
No one have any clues on this at all?  :(

---

### Post by afbase on 2006-11-23
it looks like its just a utility partition dell installs on the hard drive. it may or may have not been deleted in the ubuntu installation.  It is only between 30-60 mb large, sooooo i suggest the soviet-russia rule:"if it ain't broke don't fix it".

P.S. cfdisk sounds like its broken or maybe you weren't root or something when you ran the proggy.  my next suggestion if you really want the dell partition off, is trying ```
 sudo cfdisk
```

---

