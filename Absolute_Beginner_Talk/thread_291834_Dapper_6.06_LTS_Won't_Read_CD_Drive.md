---
title: "Dapper 6.06 LTS Won't Read CD Drive?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by dothedorky on 2006-11-03
I just upgraded about two days ago to the 6.06 LTS version, and let me just say that its DEFINATELY going to take some getting used to. I understood the breezy version a LOT better than i do this version for some reason- mainly because after installation breezy was immediately functionable and user friendly, and the linux kernel read everything on my system immediately and effectively... not so much on this version... though at least my internet connection was an immediate success.

Anyways, my question is this- I'm trying to upload some music files to AmaroK from a double layer DVD+R disk that i copied all my music files on to (yay for backup) however when i insert the disk, nothing happens. No icon on the desktop like the previous version, even when i go to Places--> Computer and search for my cd drive, it tells me 

:unable to mount the selected volume
:mount: no medium found. 

I miss Breezy when i start working with this version... but then again i am  always up for a challenge.:twisted:

---

### Post by houstonbofh on 2006-11-03
Just to be clear, you upgraded a Breezy system you have been using for quite some time, correct?  This can be a problem.  Especially if you are like most of us, and set up your system just the way you want it.  The upgrade can make some assumptions about what is where, and that my not be the case for you.  If it is an option (You did make a backup before upgrade, right?) a clean install of Dapper may be the quickest way to fix it.  Dapper has installed clean on almost every system I threw at it.

---

### Post by K.Mandla on 2006-11-03
See if you can mount a CD manually. Put the CD in, and use the mount command in a terminal.

```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```
Your /dev/hdX number might be different, depending on your system. Anyways, it's an idea. :rolleyes:

---

### Post by dothedorky on 2006-11-08
> **K.Mandla said:**
> See if you can mount a CD manually. Put the CD in, and use the mount command in a terminal.

```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```
Your /dev/hdX number might be different, depending on your system. Anyways, it's an idea. :rolleyes:

I get this:

mount: No medium found

---

