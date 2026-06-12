---
title: "How Do I Burn A DVD?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by transkinetic on 2007-11-24
How do I burn files onto a DVD? I am trying to backup some data. I tried following the command line instructions on the [CdDvdBurning]("https://help.ubuntu.com/community/CdDvdBurning") Community Wiki. I installed growisofs and tried to burn a folder on my Desktop titled sandwiches...
```
spacepopeye@spacepopeye-laptop:/dev$ growisofs -Z /dev/scd0 -R -J /home/spacepopeye/Desktop/sandwiches
```
```
:-( /dev/scd0: media is not recognized as recordable DVD: 0
```
I have burned to this same brand of media using windows. What is wrong?
Thanks!
-Travis

---

### Post by CatKiller on 2007-11-24
I just go Places -> CD/DVD Creator and drag-and-drop the files that I want to burn onto the window.

---

### Post by transkinetic on 2007-11-24
I am running XCFE and don't have a places button. Is there some other way to bring up the burning folder?

I tried to burn using Brasero but it claims that my memorex disks are not writable media. I know that they are! Is this a limitation of Drivers or is there still hope? It worked in windows.

---

### Post by CatKiller on 2007-11-24
Ah. Sorry, I don't use XFCE or do much from the command line. Are you sure that /dev/scd0 is the path to your DVD burner? Mine is /dev/dvdrw, which is a link to /dev/hdc.

---

