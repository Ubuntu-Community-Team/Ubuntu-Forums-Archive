---
title: "IMAC G3 upgrade problems"
date: 2008-11-20
forum: Apple Hardware Users
---

### Post by ericd8027 on 2008-11-20
I have an old IMAC G3 that has had some hardware upgrade.  1GB ram, 30 gig hd.  I recently was able to get edgy eft installed on to the computer and then found out that it is no longer supported.  I have heard internet rumors that dapper still is until 2009.  

My ultimate goal is get a newer version of Linux on the cpu (as I run into a lot of errors with Edgy).  Please help.  I have been fighting this beast for 6 weeks now. 

Thanks in advance!

---

### Post by stream303 on 2008-11-22
What errors are you having?

If Edgy is still up and running somewhat, the first thing I'd do is copy / print your /etc/X11/xorg.conf and also your /etc/yaboot.conf before you do anything else.  These will serve as a valuable reference later if needed.

With all that ram, this will indeed be a worthy project for an older G3 indeed.  Determining which model you have will help:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

---

### Post by ericd8027 on 2008-11-30
Here is the computer we will be working with...

iMac G3/350 (Slot Loading - Blueberry)
	

350 MHz PowerPC 750 (G3)

---

### Post by ericd8027 on 2008-12-02
I have been able to fix most of the errors (just a couple occur in firefox) by reinstalling Edgy.  Now, because Edgy is not supported anymore and the architecture of the Powerpc's is such, I need to downgrade to 6.06 LTS.  I have tried an install from CD and have had errors.  How can I downgrade to 6.06 so I can then upgrade to some newer versions of Ubuntu.

Any help is greatly appreciated.

---

### Post by stream303 on 2008-12-02
Downgrading is a real drag, and isn't advised - it's a one way street for the most part.  HOWEVER, you do have the key to the kingdom concerning upgrades!

Copy or print out your existing /etc/X11/xorg.conf, as well as your /etc/yaboot.conf for future reference.

Instead of trying to upgrade, you might have better luck tying to install Hardy 8.04 directly.  I'd still go with the "alternate" installer even with all that ram, as you will probably have to edit your new xorg.conf with some of the values taken from your old one.

If you just want basic functionality, and don't mind using the latest Firefox in the 2.x series, (2.0.0.18 as of now I believe) may I suggest Debian stable 4.0r5?  Everything you've learned in Ubuntu is applicable there, even most of the material in the docs and wikis.  It is still getting support, and has the more classical X server configuration that could make it much easier to configure than the newer releases.  All you need is CD-1 for gnome, and down the page you'll see CD-1's for KDE and XFCE.  And, you can still hang with the Ubuntu crowd helping out since they are from the same stock basically.

You can grab the stable 4.0r5 Etch right here:
[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

---

### Post by ericd8027 on 2008-12-06
Thanks for the help...I will definitely try to go with Hardy 8.04 and if that doesn't work I will definitely try out Debian.  Appreciate it greatly!

---

