---
title: "Someone help me please!"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by mphelp11 on 2008-02-26
I'm sure this is a common problem, but im new to Ubuntu, and not that skilled at computers in general:

The other day I downloaded Ubuntu so I didn't have to load up Vista everyday in school for taking notes. I downloaded it and proceeded to go through the set-up, when it asked how I wanted the drive partitioned, I just hit the "auto" button and completed the set-up.  So the next time I logged on my computer, It went straight to Ubuntu, so I restarted it, and tried to boot up Vista, but it wasn't on the list. I assumed it was deleted along with everything else on my computer.  But today I was looking at the plug ins I have for this computer by typing "about: plug ins" into my web browser, and I saw that DivX, Windows media player, and a few others that I had on my computer before I put on Ubuntu were present.  So maybe I have a small ray of hope that everything is still on my computer in this other partition somewhere. I just don't know how to find it.

Anyone's help is much appreciated.

---

### Post by JoshuaRL on 2008-02-26
No, unfortunately.  The plugins you're talking about let Ubuntu play those type of files.

But just to be sure, please post the output of:
```

fdisk

```

---

### Post by mphelp11 on 2008-02-26
I did and this is what it said

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by JoshuaRL on 2008-02-26
Sorry, try:
```

fdisk -l

```
And that would be a lowercase "L" after fdisk.

---

### Post by mphelp11 on 2008-02-26
it wouldnt recognize that, it just says command not found. im pretty computer-challenged

---

