---
title: "Complete Disk Image Backup"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by rtX on 2007-05-09
Hi,
Is there software available under Ubuntu (with a GUI) to backup completely (and restore) a disk "image".  I want to be able to backup an image (compressed) of my whole system and then subsequently restore it to a different disk in the event of catastrophic failure.  I am aware that Acronis have TrueImage for Windows which if you have a windows system from which to launch can back-up an image, but wondered if there was anything Linux native?
I can find no Ububtu supported GUI for PartImage either.
Thanks,
rtX

---

### Post by fakie_flip on 2007-05-09
dd can do it. search google for more information with doing it on dd. i saw a good guide at [www.linuxquestions.org](www.linuxquestions.org) about dd.

---

### Post by fakie_flip on 2007-05-09
i think this is what you are looking for

[http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage)

---

### Post by fakie_flip on 2007-05-09
There is sbackup, but it is not for copying partitions.

---

### Post by fakie_flip on 2007-05-11
Did either of those do what you want?

---

### Post by kvonb on 2007-05-11
Go here and download it:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

It has lots of great tools

---

### Post by ramjet_1953 on 2007-05-11
There is also a package called Ghost for Linux (G4L), which is an iso image that you can download and burn onto a CD.

It has a mini Linux included and you boot from the CD.

You then just do a 1:1 copy of you HDD onto your second HDD.

Follow this link and download it:

[ftp://fedoragcc.dyndns.org/g4l-v0.22.iso](ftp://fedoragcc.dyndns.org/g4l-v0.22.iso)

Don't forget to burn it as an iso, not a data disk and burn it SLOWLY, no faster than 4 X.

Regards,
Roger :cool:

---

