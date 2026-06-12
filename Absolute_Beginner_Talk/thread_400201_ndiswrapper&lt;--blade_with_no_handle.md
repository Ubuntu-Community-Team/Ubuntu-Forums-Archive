---
title: "ndiswrapper&lt;--blade with no handle"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by ebichuhamster on 2007-04-03
Here it goes, 

Yesterday i spent a couple of hours investigating if ndiswrapper was right for me.  I have a Broadcom 802.11b card standard for the HP pavilion dv6000 laptop.  I started setting the ndiswrapper up and righ after i had loaded the driver that i needed i found something else in the device manager.  It said "bcm43xx" on the 'info.linux.driver" key, so i thought to investigate.  As it seems there was a package specified for network cards that use this driver, i installed it.  But nothing happend :( . So i continued with the ndiswrapper installation.  The card's light wasnt turning on and as i typed 'dmesg' on a terminal, i got these 2 messages concerning what i had recently done

> ndiswrapper version 1.41 installed 
             new driver detected (alternate driver ....)(this might not be the exact quote but it was something pretty close to this)

The message I was supposed to get, (following this wiki page:[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)) was 
>  ndiswrapper: driver ''driver1'' loaded


What i did get was accompanied by a huuuuuge load of errors which would take up too much space to copy/paste, which were about 200 lines saying "ignoring bad line: *here go a bunch of unrecognizable characters*

Any suggestions as to what might the messages mean?? How do i take them off? (allready uninstalled/installed ndiswrapper and unloaded/loaded driver.  Tried different driver too. Ultimately,, any suggerstions on how to actually geting this wireless to work?
 Thx a million in advance!

---

