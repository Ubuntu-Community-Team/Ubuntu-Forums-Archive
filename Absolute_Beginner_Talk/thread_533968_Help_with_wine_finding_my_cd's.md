---
title: "Help with wine finding my cd's"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-08-24
Whenever I try to run a game on wine, an error comes up saying my disc isn't in the drive, even though the folder with all of the cd's files pops up.

---

### Post by pcexpert2 on 2007-08-24
what you need is a cd image for wine. i cant tell you where to get one because that would be illigal ok search google:-\"

---

### Post by WebSiteGuru on 2007-08-24
> **dljesse said:**
> Whenever I try to run a game on wine, an error comes up saying my disc isn't in the drive, even though the folder with all of the cd's files pops up.

If I remember it right (correct me if I am wrong on this), you will need to mount the CD ROM in wine too have it work correctly.

---

### Post by dljesse on 2007-08-24
I don't know how to do that, I'll go check the wiki.

---

### Post by dljesse on 2007-08-24
I can't figure out how to mount the cd rom. Will I have to make .iso files of all my cds to play?

---

### Post by WebSiteGuru on 2007-08-24
Here is how.

> Configuring Wine

On the command line or in Run Application, type winecfg.
Adding CD and DVD drives to Wine

Go to the drives tab in winecfg. Hit the Autodetect button.

If you find that this does not work correctly for you, then follow these instructions:

   1.       Run winecfg
   2.      Navigate to the drives tab
   3.      Click on Add...
   4.      In the path bar, type /media/cdrom
   5.      Click Show Advanced button below the Browse... button and set the Type to CD-ROM
   6.      Click OK

If you have more than one CD/DVD device you will need to identify each one differently. Use /media/cdrom0 for the first CD/DVD device, /media/cdrom1 for the second one, and so on. If in doubt, type ls -la ~/.wine/dosdevices/ in a terminal to check your CD/DVD device details after Wine is installed.

---

