---
title: "MOL - can it boot from other drives? Also, full screen not working."
date: 2006-12-16
forum: Apple PPC Users
---

### Post by magnolia fan on 2006-12-16
Hi MOL users,
I was wondering if MOL can be configured to boot from an OSX install on another Hard drive or if it will only use the OSX install on the same HD as Linux.  Can't seem to find where to make the adjustment in molrc.osx.

Also, I can't get full screen to work.  I'm trying Ctrl + Option + F8 but it only takes me to a black screen.  Ctrl + Cmd + F7 returns me to the small MOL window.  Ctrl + Option + F9 takes me to a video configuration screen. 

--any tips would be great, thanks

---

### Post by didg on 2006-12-16
> **magnolia fan said:**
> Hi MOL users,
I was wondering if MOL can be configured to boot from an OSX install on another Hard drive or if it will only use the OSX install on the same HD as Linux.  Can't seem to find where to make the adjustment in molrc.osx.


Yes it can in molrc.osx search for 'OS X Volumes'
and add
   blkdev:             /dev/hda9       -rw -boot

replace /dev/hda9 by your OSX partition.

No idea about full screen, I'm currently running feisty and mol is broken.

---

### Post by magnolia fan on 2006-12-16
Hey, that worked.  Thanks.

Does anyone know of a way to pass the Boot partition as an argument in the command line?

ie:  startmol --osx /deb/hda9  ???


The Full Screen issue can be resolved by upping the Screen Resolution in the System Preferences within the virtual OS itself once it boots.  I can live with that.

---

### Post by calum on 2006-12-23
> **magnolia fan said:**
> Hi MOL users,
I was wondering if MOL can be configured to boot from an OSX install on another Hard drive or if it will only use the OSX install on the same HD as Linux.  Can't seem to find where to make the adjustment in molrc.osx.

Also, I can't get full screen to work.  I'm trying Ctrl + Option + F8 but it only takes me to a black screen.  Ctrl + Cmd + F7 returns me to the small MOL window.  Ctrl + Option + F9 takes me to a video configuration screen. 

--any tips would be great, thanks

If full screen is working, you will get a mesage on the console saying "FULL SCREEN ON VT 9" or similar, indicating which console you need to switch to.

Have you run molvconfig first to probe all the available resolutions?  Fulll screen can be a bit picky about which ones it will use.

---

