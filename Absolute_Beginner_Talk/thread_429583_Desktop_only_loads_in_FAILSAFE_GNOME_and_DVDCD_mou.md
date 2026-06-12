---
title: "Desktop only loads in FAILSAFE GNOME and DVD/CD mount issue"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by visible on 2007-05-01
OK.  Everything did work but now I am finding that if I boot into a default session whether it is gnome or the xclient script one I get the login sound, a moveable mouse point and a blank desktop (no wallpaper, no panel, etc.).  Now if I boot into failsafe gnome, everything loads and appears as normal (even beryl and gdesklets).  I am running fiesty with a nvidia MX 440 (older card).  I am guessing that something is preventing something else from loading in default settings because that failsafe prevents start up scripts and want not. I've looked through the sessions prefs and can seem to figure out the problem.  
The other issue that has cropped up since this happened is when I insert a dvd it doesn't show up on the desktop like it did before.  then if I exit a player, vlc, xsine, mplayer etc, I cannot eject the disk.  thanks in advance.  The only thing I did wierd was trying to install vlc from the repos and kept getting an error about not being able to get all the files.  Install failed.  then I ended up using automatix for fiesty and it installed fine and works.

when I list my optical drives in terminal i get this.  seems a little redundant:
[   28.140217] hdc: CDD4801 CD-R/RW, ATAPI CD/DVD-ROM drive
[   28.923589] hdd: COMPAQ DVD-ROM SD-612B, ATAPI CD/DVD-ROM drive
[   29.141238] hdd: ATAPI 32X DVD-ROM drive, 512kB Cache, DMA

---

### Post by visible on 2007-05-01
FIXED IT!!! at least the metacity problem.  I went into root and deleted all the saved sessions.  turns out that it was looking for a window shade option (assiociated with beryl I think) that metacity wasn't capable of.  back to straight GK/Metacity stuff for now.  

I am however still looking for a fix for the DVD problem.  something I did when I was trying to install VLC.  I know it.  I was following a how to on here that had you install all these weird pakages.  I can't find the post again.

---

