---
title: "mounting a drive with gui"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Blond37 on 2007-06-03
how do  i do this?
i'm ready to throw the damn pc in the river!

---

### Post by Bohlio on 2007-06-03
hold on there mate, before you waterlog your computer you might want to try looking in in your menu bar at Places>Computer and then finding whatever drive you want to mount. right click on it and select "Mount Volume"
I hope this helps :-)

---

### Post by Blond37 on 2007-06-03
> **Bohlio said:**
> hold on there mate, before you waterlog your computer you might want to try looking in in your menu bar at Places>Computer and then finding whatever drive you want to mount. right click on it and select "Mount Volume"
I hope this helps :-)

thanks but it does not show up there

---

### Post by Bohlio on 2007-06-03
Ouch, Then i think it has problems detecting the drive. Im sorry but i cant really help you with that, Im still learning Ubuntu :-)

Just to help others help you, What type of drive are you trying to mount, a CD drive, Harddrive, floppy drive, flash drive?

Just be patient and this community always pulls through, Its great :-)

---

### Post by mrazster on 2007-06-03
Try installing *gparted* and check if it finds your hdd there, just do in terminal:
```
sudo apt-get install gparted
```
If not already installd, that is. If so then just fire it up and look for your hdd.

If you can find your hdd with gparted...we can work from there, if not then you have a hardware problem of some kind.

---

### Post by Blond37 on 2007-06-03
> **Bohlio said:**
> Ouch, Then i think it has problems detecting the drive. Im sorry but i cant really help you with that, Im still learning Ubuntu :-)

Just to help others help you, What type of drive are you trying to mount, a CD drive, Harddrive, floppy drive, flash drive?

Just be patient and this community always pulls through, Its great :-)

a 300 gig hard drive, and i am ready to go back to windows.

"resistence is futile"

---

### Post by Blond37 on 2007-06-03
> **mrazster said:**
> Try installing *gparted* and check if it finds your hdd there, just do in terminal:
```
sudo apt-get install gparted
```
If not already installd, that is. If so then just fire it up and look for your hdd.

If you can find your hdd with gparted...we can work from there, if not then you have a hardware problem of some kind.

gparted sees it.

---

### Post by icechen1 on 2007-06-03
> **Blond37 said:**
> gparted sees it.

right click on the drive you want to mount and choose ''mount drive''.

---

### Post by southernman on 2007-06-03
If your using Ubuntu when you go to: Places > Computer - do you see the drive here?

---

### Post by HotShotDJ on 2007-06-03
Have you partitioned and formated the drive?  IIRC, unformatted space won't show up on your desktop, even in Windows.  You can install either gparted (gnome) or qtparted (KDE) to partition and format it.

---

### Post by mrazster on 2007-06-04
> **Blond37 said:**
> gparted sees it.

Whery well....then the hdd is working properly.

Now..is it formated?...if not then do it with gparted...if it is then what filesystem does it have and wich driveletter is it assigned to (i.e hda, hdb...had2, hdb4 e.t.c)....???

---

