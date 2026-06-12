---
title: "[SOLVED] Intrepid Ibex woes on Intel iMac"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by apple_and _linux on 2008-11-04
I am dual-booting Ubuntu 8.10 and Mac OS X 10.4.11 on a two-year-old white Intel iMac (5,1).  I'd heard that everything worked beyond complain on Hardy Heron, so I was pretty excited about getting the system set up like this.  A few days after 8.10 came out, I wiped the system, reinstalled Tiger, and put Ubuntu on the free space (following the [online tutorial]("https://help.ubuntu.com/community/Intel_iMac")).  Installation went off without a hitch, and the system is nice and fast.  Unfortunately, a few key components aren't working properly, and it puts a damper on all the fun- and the overall usefulness of having Ubuntu on this computer.

1. Wireless network connection- I have an Airport Extreme router with WPA2 security, and Ubuntu refuses to connect to it.  The system obviously supports WPA2 and lets me enter the password, but it fails to connect, instead asking for a password (I know I entered the right one, I tried it several times).  I disabled WPA2 but left it as a hidden network (leaving it only with MAC control) and it connects fine.  Very odd...
2. HFS+ partition- I have, in addition to the Mac OS X system drive, a partition for documents.  It is NOT journaled, and Ubuntu sees it and mounts it just fine.  However, whenever the system is rebooted, the partition must be remounted, which typically must be done in the administrator account.  Being as all the documents are on that drive, this is no small inconvenience.  Is there a way to automatically mount that partition on startup?
3. ATI Graphics- right now I am running Ubuntu without the ATI graphics driver (I have the X1600 card).  It generally works just fine; Compiz is beautiful, nothing is glitchy- but Flash videos do not play, and nor do DVDs.  I have installed all the libraries recommended for these activities as written [here]("http://ubuntuforums.org/showthread.php?t=766683").  When I try to play DVDs, the player (VLC, Movie Player) simply crash.  Flash player apparently loads the video but does not play it.  When I enable the proprietary ATI driver, Compiz is not as smooth, but I get closer to playing multimedia- I can see the DVD menu and the Flash video plays, but both are very glitchy.  Any idea what is happening here?

Those are my three main problems. One other question, though: is it possible to make use of the Command key on the white wired Apple keyboard?  The Control and Alt keys on the left side don't work, due to liquid spills... it would be really nice not to have to perform keyboard shortcuts exclusively with my left hand.
Thanks in advance for any help!
-Jeremy

---

### Post by cyberdork33 on 2008-11-04
> **apple_and _linux said:**
> 1. Wireless network connection- I have an Airport Extreme router with WPA2 security, and Ubuntu refuses to connect to it.  The system obviously supports WPA2 and lets me enter the password, but it fails to connect, instead asking for a password (I know I entered the right one, I tried it several times).  I disabled WPA2 but left it as a hidden network (leaving it only with MAC control) and it connects fine.  Very odd...
This is an issue affecting a lot of WiFi cards rights now in Ubuntu...

> **apple_and _linux said:**
> 2. HFS+ partition- I have, in addition to the Mac OS X system drive, a partition for documents.  It is NOT journaled, and Ubuntu sees it and mounts it just fine.  However, whenever the system is rebooted, the partition must be remounted, which typically must be done in the administrator account.  Being as all the documents are on that drive, this is no small inconvenience.  Is there a way to automatically mount that partition on startup?You have to add it to /etc/fstab

> **apple_and _linux said:**
> 3. ATI Graphics- right now I am running Ubuntu without the ATI graphics driver (I have the X1600 card).  It generally works just fine; Compiz is beautiful, nothing is glitchy- but Flash videos do not play, and nor do DVDs.  I have installed all the libraries recommended for these activities as written [here]("http://ubuntuforums.org/showthread.php?t=766683").  When I try to play DVDs, the player (VLC, Movie Player) simply crash.  Flash player apparently loads the video but does not play it.  When I enable the proprietary ATI driver, Compiz is not as smooth, but I get closer to playing multimedia- I can see the DVD menu and the Flash video plays, but both are very glitchy.  Any idea what is happening here? the open driver is still a bit glitchy. I have been testing it as well. It was working decently, but the performance with fglrx is much better.

> **apple_and _linux said:**
> Those are my three main problems. One other question, though: is it possible to make use of the Command key on the white wired Apple keyboard?  The Control and Alt keys on the left side don't work, due to liquid spills... it would be really nice not to have to perform keyboard shortcuts exclusively with my left hand.

The CMD key is the SUPER key under linux. Many compiz commands are mapped with it (try CMD+TAB for instance).

---

### Post by apple_and _linux on 2008-11-06
Thanks, cyberdork.  I fixed the HFS+ drive (fstab is my new best friend), and I won't be spending time worrying about the wireless or the graphics now that I know they have driver issues.  As far as video, I can either use the open driver and have Compiz but very glitchy video (DVD and Flash), or I can use the proprietary driver and have beautiful video playback but no Compiz.  So basically, now I'm up 'n running... can't get beautiful effects in Tiger and I can't play DVDs in Ubuntu.  Win-win!  :)

---

### Post by cyberdork33 on 2008-11-06
> **apple_and _linux said:**
> I won't be spending time worrying about the wireless or the graphics now that I know they have driver issues.
Someone has again pointed out that replacing network-manager with wicd seems to fix the problem so you might try that.
> **apple_and _linux said:**
> As far as video, I can either use the open driver and have Compiz but very glitchy video (DVD and Flash), or I can use the proprietary driver and have beautiful video playback but no Compiz.
no, with the proprietary driver you can have compiz too.

---

### Post by apple_and _linux on 2008-11-06
> **cyberdork33 said:**
> Someone has again pointed out that replacing network-manager with wicd seems to fix the problem so you might try that.
Alright, I'll look into that- thanks again.
> **cyberdork33 said:**
> no, with the proprietary driver you can have compiz too.
Oh wow, I see you're right- I had it backwards.  Apparently the proprietary driver is required for Compiz, but it's the open source driver that provides good video.  Is there a way to get around that and use the open driver for Compiz?

---

### Post by cyberdork33 on 2008-11-06
> **apple_and _linux said:**
> Oh wow, I see you're right- I had it backwards.  Apparently the proprietary driver is required for Compiz, but it's the open source driver that provides good video.  Is there a way to get around that and use the open driver for Compiz?
The open driver was working with compiz enabled (for me anyway). This is the driver that the system uses by default. However, if I did certain things everything would go nuts unless I disabled Compiz first. I think this is just a bug in the open driver, and it will be fixed over time.

---

### Post by apple_and _linux on 2008-11-12
Oh yeah, I see now.  Got it all sorted out... with the open driver, I can have Compiz just fine and I can have video playback just fine, but NOT at the same time.  Not a big deal... presumably this will be fixed eventually, like you said.  In the mean time, at least I know what the problem is!  :)  Thanks again for all your help.

---

