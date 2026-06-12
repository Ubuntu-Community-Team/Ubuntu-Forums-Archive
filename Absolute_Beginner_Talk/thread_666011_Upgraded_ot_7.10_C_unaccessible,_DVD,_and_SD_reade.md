---
title: "Upgraded ot 7.10 C: unaccessible, DVD, and SD reader"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by USFMD82 on 2008-01-12
I have fixed many problems I have had however I just now noticed this thouhg.. I cant get my dvd drive ot work on my laptop. at first I ahd trouble even opening it then reading other trheads I typed in the terminal eject, that worked. inserted a dvd. and it recognized it in the file browser as ther being a drive, however I could not read anytihngon the cd "I even tried to "mount" it but nothing..

as well I can no longer access my C: drive since upgrading.. it gives the option ot mount but then nothing.. I usually woudl run ubuntu and listen to my music on my C: drive off there.. any thoughts..

My SD reader is apparently "found by goign to device manager
PCIxx21 Integrated FlashMedia Controller
PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

cant find anything pertaining to my DVD drive there.. if it helpes I have a Compaq PresarioV2000

---

### Post by ckuka on 2008-01-12
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Should help you out reading dvds and cds if you need a driver update. 
i hope this helps.

---

### Post by blueridgedog on 2008-01-12
See the link regarding mounting windows drives in my signature.  I found the ntfs-config tool very useful.

---

### Post by USFMD82 on 2008-01-13
Thanks for the help so far guys.. I tried and neither worked.. Im not trying to read a encrypted dvd, im jsut saying when I put anything in the dvd drive, Ubunut File browswer knows there is a DVD drive there, but its not reading anything. Same with the SD card, and the USB, these things show up like Ubuntu wants to open them but when I double click, right click open, right click mount.  Nothing happens.. its like it wont open it up. when I installed 7.04 it used to just mount the drives and read them all by tiself I never had to d/l anytihng.. did I miss some package somewhere?

also now my Rhythymbox isnot playing mp3's or anytihng anymor for that matter (pdcasts, straming radio)  Man this upgrade was a headache, but im patient, luckily, and its better then windows still.. 

still open to suggestions

---

### Post by USFMD82 on 2008-01-13
Update..

Just tried to do the Gstreamer thing at startup 
[PHP]sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse[/PHP]

but that didnt work it came up with the error
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins-ugly has no installation candidate

```

SO I am guessing that it is still already on the computer.. but it is just not working.. anyway ot get it reset up?

---

### Post by USFMD82 on 2008-01-14
Bump

---

