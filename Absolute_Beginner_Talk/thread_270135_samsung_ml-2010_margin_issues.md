---
title: "samsung ml-2010 margin issues"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-02
i installed this printer on a new computer and i didn't add the admin cups user as suggested before installing; thus the margins are off. i tried uninstalling the printer drivers and removing it from cups and starting over after adding the user, but still no go. it prints perfectly on the network machines, just not on the local computer. 

i'm using the samsung provided drivers at the time and i've also tried the gdi driver. i tried to use the splix driver, but i got hung up on the raster error part. not much support on their website.

any help would be great!!

---

### Post by shanepardue on 2006-10-02
i know this is kind of an obscure issue, but i've seen many people get it working without a problem. i don't know if i'm just more picky or what.

---

### Post by shanepardue on 2006-10-03
this is the last attempt at a response for this issue then i'm giving up on the printer for awhile.

---

### Post by Scunizi on 2006-11-09
Download the latest drivers from the website and install.  After installing go to System/Admin/Printers and add the printer there as you would normally do.  The drivers will show up now (SPL II)

---

### Post by shanepardue on 2006-11-10
Yeah, I did that..I actually got this fixed awhile ago and forgot to respond
 to this thread. It took changing the paper size to letter (instead of A4)
 through cups' web-based utility, not just through the gnome-cups-manager.

---

### Post by ArchVile on 2007-08-06
i guess i have to reopen this thread. i'm using feisty (standard, with gnome) and got a new ml-2010. i've done the following.

1. installed the current drivers from the samsung page, did setup, margins are still (but less) off.
2. uninstalled the drivers, added cupsys to shadow group, reinstalled the driver, same thing.
3. noticed that i kept running the gdi driver even after installation of the samsung files, tried manually selecting the SPL II drivers (which turn up as "CUPS (standard)" in the gnome printer setup) with [http://localhost:631](http://localhost:631) -- and the printer gives me an error page, saying "use proper drivers". it doesnÄt matter whether i use the gnome printer administration or the samsung tool.

besides that, the gdi driver (the only one that has ever worked for me) rescales the page, roughly by 10%. this is damn unusable! i would so far NOT recommend this driver for linux (at least feisty) users. unless someone knows an answer.

note: i've also tried the ml-4500 driver. works, but with same probs.

ive changed /etc/papersize to a4, no change.

this is really annoying, because i read at several places that the ml-2010 worked fine with linux, even explicitly with feisty!

PLZZZZ HELP!

greets
a/v

---

### Post by shanepardue on 2007-08-06
> **ArchVile said:**
> i guess i have to reopen this thread. i'm using feisty (standard, with gnome) and got a new ml-2010. i've done the following.

1. installed the current drivers from the samsung page, did setup, margins are still (but less) off.
2. uninstalled the drivers, added cupsys to shadow group, reinstalled the driver, same thing.
3. noticed that i kept running the gdi driver even after installation of the samsung files, tried manually selecting the SPL II drivers (which turn up as "CUPS (standard)" in the gnome printer setup) with [http://localhost:631](http://localhost:631) -- and the printer gives me an error page, saying "use proper drivers". it doesnÄt matter whether i use the gnome printer administration or the samsung tool.

besides that, the gdi driver (the only one that has ever worked for me) rescales the page, roughly by 10%. this is damn unusable! i would so far NOT recommend this driver for linux (at least feisty) users. unless someone knows an answer.

note: i've also tried the ml-4500 driver. works, but with same probs.

ive changed /etc/papersize to a4, no change.

this is really annoying, because i read at several places that the ml-2010 worked fine with linux, even explicitly with feisty!

PLZZZZ HELP!

greets
a/v
I'm assuming you're using Ubuntu and not Kubuntu?
Also, don't set /etc/papersize to A4..You will want "letter" as the paper size.
Check that the paper size is set to "letter" in gnome-cups-manager and at [http://localhost:631/](http://localhost:631/)

---

### Post by ArchVile on 2007-08-06
thanks for the (amazingly :) ) quick reply. however, i had set /etc/lettersize to "letter" before, and in retrospect, i can say that none of my efforts made a change in feisty.

but, i've found a solution! ---> use the SPLIX drivers [http://splix.ap2c.org/](http://splix.ap2c.org/)

however, use them with a different distro. i put in the PCLinuxOS 2007 live CD, and immediately had perfect printouts, without adding cupsys to any group, without doing localhost:631, etc... just by selecting the out-of-the-box SPLIX 1.0 driver.

then i went and installed splix in feisty from the repo. and it sucks! :mad: it gives me the "use proper driver" message. all in all, i'm growing STRONGLY dissatisfied with feisty, because this is only one of MANY issues i've had over the last months.

however, it seems like SPLIX is the way to go, because with the GDI driver in PCLinuxOS, i had exactly the same problems as in feisty (horrible margins).

i feel i should mention that otherwise, the ml-2010 is an amazing printer for the money (paid 69 EUR). fast, reasonably quiet, nice printing quality (even with tonersaving turned on).

cheers!
a/v

---

### Post by shanepardue on 2007-08-08
I'm glad you got it working properly. Not sure what the issue is with Feisty as I use it perfectly fine!

---

