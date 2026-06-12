---
title: "installing over win98"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by jarviscares on 2006-03-06
Hey, I'm very new to Linux (first experience with it)... But I'm determined to give it a go and learn some things. 

My first problem: I've downloaded the Ubuntu 5.10 install ISO for i386, and burned it as an ISO to a cd (using NERO in Windows XP). All is well up to this point. I put the freshly burned CD into an older computer (intel 633mhz, 128 mb ram, Hitachi CDR-7930 CDROM), set the BIOS to boot from CDROM, restart... and my windows 98 loads up off the harddrive. No trace of the boot install cd. 

The CD ROM drive does work with other CDs (dunno about boot cds though). 

I plan to install Ubuntu right over win98, should I wipe my HDD first or will the install CD do that for me? And How can I get my install cd to work as a boot cd? 

Any help is much appreciated... and if you need more info, let me know what!

Thanks!

---

### Post by Lord Illidan on 2006-03-06
At what speed did you burn it?

---

### Post by Lord Illidan on 2006-03-06
Also, does the boot cd work on other computers? Test it on the XP computer. It will not install automatically, don't worry.

---

### Post by jarviscares on 2006-03-06
I believe the burn was at 32x, and I did not test the install cd on the XP computer... I did however try out the live CD I burned in the exact same way and it worked fine... I'll try out the install cd and let you know what happens. 

Thanks for the quick replies!

---

### Post by kaamos on 2006-03-06
Are you sure burned it as an image? 

[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

EDIT: too slow, nevermind.

---

### Post by Bartender on 2006-03-06
jarvis -
First, the easy answer...if you can get your CD to boot it'll ask if you want to reformat the entire drive.  For you that would be a yes.
As to your PC skipping right past the CD; that happens sometimes.  My modern PC looks at the stamped CD's I received for fifteen seconds or so, then gives up & moves on to the HDD.  Does yours at least try to start the CD?  Do you hear the drive spin up, then stop (perhaps several times) before giving up?
Another thing to try.  If I start up in Windows then put the stamped Ubuntu CD in the tray, it can't even tell that there's a disc in the tray.  Can you at least explore yours?
I don't have an answer for you.  I'm guessing this is some form of hardware incompatibility that affects a small percentage of would-be users.

---

### Post by Lord Illidan on 2006-03-06
Try burning at a lower speed, say 8x.

---

### Post by jarviscares on 2006-03-06
I just tried booting the install disk on my XP machine... and same deal, skipped right over and booted off the HDD. The CD drive on my xp does spin and make noise, but no booting. As for the 98 computer, it tries to spin it twice before anything is on the screen, then windows boots with no more activity from the CDROM... and lets me know that the boot record on the CD ROM was not found. 

When I try to explore it in my win98 computer it tells me that it can't access the drive... but putting in a different CD it works fine. in XP I can just see the ISO file... I think I may have screwed up the burn somehow... I am going to re-try burning it at 8x and let you know how it goes. 

Hopefully my CDROM on my older comp isn't incompatible...

---

### Post by SZF2001 on 2006-03-06
While your computer is booting up, have to tried holding down Alt and F4 together? It brings you to some menus, or something, look at around to see if it says to push F-something to find an option to boot from the CD. That *might* work.

---

### Post by jarviscares on 2006-03-06
Well, I re-burned the install CD and it works like a charm as a boot cd on my XP machine... 

Sadly, however, my older machine still does not like it... skips right over on boot, and when I try to explore it in my computer, it tells me D:\ is not accessible. The device is not ready. (though other cds work fine). I'm thinking at this point that it might be my CDROM drive that the cd doesn't like... but shouldn't it at least let me explore the cd, even if it won't boot off of it??? 

Thanks!

---

### Post by jarviscares on 2006-03-06
bump :neutral:

---

### Post by barbarian on 2006-03-12
Hei,
I've heard that Breezy minimum hardware requirments is 128 mb ram; maybe that's why your instalation stuck..

---

### Post by barbarian on 2006-03-12
try Hoary?

---

### Post by steveneddy on 2006-03-12
Did you SAVE the changes to the BIOS?

Thought I needed to ask. I would think that if there was an option for booting from the CD-ROM in the BIOS, then it would actually boot from the CD.

Hmmm.....

---

### Post by 3rdalbum on 2006-03-13
My Mac has a bunged CD-ROM drive. The first Live CD I burnt wouldn't boot; OpenFirmware would look at the disc a couple of times and then just boot Mac OS. The Mac OS wouldn't mount the CD either; the drive would just keep trying to spin it up but never read it.

It's just like your problem. However, I burnt to a different disc, and that one worked perfectly.

The moral of the story: Some older drives don't like CDRs. Try using CDRs that are made specifically for music; they're designed to work in old players. Burning at 8x rather than 32x never hurt either.

---

