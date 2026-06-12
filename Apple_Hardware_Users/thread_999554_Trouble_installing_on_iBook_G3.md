---
title: "Trouble installing on iBook G3"
date: 2008-12-02
forum: Apple Hardware Users
---

### Post by doctorbighands on 2008-12-02
I just picked up an old "clamshell" style iBook G3. I'm trying to install Ubuntu, but I keep running into the same issue.

I've tried using 7.10 alternate and 6.10 alternate.

After a VERY brief period of trying to load the install CD, I get the following errors:

```

RAMDISK: incomplete write (-28 != 32768) 8388608
RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

```

The discs md5sum just fine. Why is this happening, and how do I stop it so I can install correctly?

Thank you!

---

### Post by cyberdork33 on 2008-12-02
How much ram do you have?

---

### Post by doctorbighands on 2008-12-02
It has 128MB, I believe. Could it be the RAM that's causing this problem?

---

### Post by Yeti can't ski on 2008-12-02
From the PowerPC FAQ: 

> "Which Macs are compatible with Ubuntu?

All NewWorld Macs should work. This means iMacs, iBooks, blue & white G3s, Lombard G3 PowerBooks and newer. The minimum system requirements are 256 MB of RAM and 3 GB of hard disk space. Users with less RAM or disk space may try Xubuntu.

Currently as of Feisty for iBooks/Powerbooks sleep, wireless, and external display are all supported with models having ATI graphics. Owners of the 12" Powerbook G4 models with the Nvidia graphics chip: sleep is not possible, because of insufficient hardware information from Nvidia." 

If you want to check it out the full FAQ: 

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Why don't you try Xubuntu? 

Good luck!

---

### Post by stream303 on 2008-12-02
Each of those releases had problems of their own, similar to what Intrepid has out of the gate.  If you still want to run an older release, I'd suggest Feisty 7.04 "alternate", however that has EOL'ed so see my Debian suggestion further down.

There are quite a few good clamshell threads in the read-only ppc archives - here is just one:

[http://ubuntuforums.org/showthread.php?t=720547&highlight=clamshell](http://ubuntuforums.org/showthread.php?t=720547&highlight=clamshell)

While Xubuntu is a good idea for low-memory machines, it is not a panacea.  Since it has less resources available for it, especially in the ppc realm, I always advise using Ubuntu as a reference for a first-time install.  Once that is up and running, you can go back and add the xubuntu-desktop, or just reinstall with xubuntu proper.  At least this way you'll know if you are encountering general installation issues, or possible desktop-environment problems, as witnessed with Intrepid Xubuntu.

Quite frankly, instead of Feisty, I'd suggest Debian 4.0r5 - the "stable" version for that machine as a first-time install:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

Be sure to pick the stable powerpc release. You only need the first cd - not all of them.   This is still getting support and updates, and has a more classical X server layout that might be much easier to deal with when it comes time for video configuration etc.  Most of the info applicable to Ubuntu PPC can be applied to Debian naturally.

In fact, if you want a lower-resource desktop, choose the XFCE based version if you scroll down to see all the images.

Make sure you burn the cd at a very low speed, ie 1X or 2X max for that old clamshell.

---

### Post by rjcalifornia on 2008-12-06
Try Xubuntu, it is perfect for those kind of macs :D 

cheers*

---

