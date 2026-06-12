---
title: "Need Help Mounting"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by ES_EF_EX on 2007-10-29
I am trying to install Age Of Empires [to run via Wine], but I can't seem to get it to mount.  Whenever I insert it into the drive, the computer recognizes it as a music CD, and all I can do is open it with Sound Juicer, which doesnt help much.  Any ideas?

---

### Post by taurus on 2007-10-29
Try something like

```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```
Assuming /dev/hdc is where your CD drive is.

---

### Post by ES_EF_EX on 2007-10-29
> **taurus said:**
> Try something like

```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```
Assuming /dev/hdc is where your CD drive is.

Ok so I've done that, and I used Wine file and installed it and it seemed to run fine, but when I click "Play" an error message pops up and says "Could not initialize Grphics system.  Make sure your graphics card is compatible with DirectDraw."  Now what?

---

### Post by taurus on 2007-10-29
Now you have to ask that question in the Gaming & Leisure section because that's where most (if not all) gamers hang out.

---

### Post by Maestro23 on 2007-10-29
> **taurus said:**
> Now you have to ask that question in the Gaming & Leisure section because that's where most (if not all) gamers hang out.

Also can check the Wine App DB for issues with Age of Empires.

[http://appdb.winehq.org/appbrowse.php?iCatId=57](http://appdb.winehq.org/appbrowse.php?iCatId=57)

---

