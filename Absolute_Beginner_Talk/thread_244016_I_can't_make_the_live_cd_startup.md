---
title: "I can't make the live cd startup"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by cmolinap on 2006-08-25
Hi, I've got a problem: I can't make the Ubuntu's 6.06 LTS live cd startup. I've follow all steps possible: make change in BIOS boot secuence (cd-rom first, HD second place and floppy in third place; floppy en first place, cd-rom in second place and HD in last place); I've turn off the pc with the live cd in cd-rom and start it; I try it restart the pc; nothing is working for me. But if I put the live cd in cd-rom, while WinXP is running I can see the browser windows and all the info about the apps inside it.
OK. I need help. Any suggestion?
CPU: Intel Celeron 1.2 GHz
Motherboard: D815EGEW fully updated.
OS: WinXP SP2, fully updated.
Memory: 512 MB
HD: 40 GB (19 GB unused).
CD-R/RW: LG 8320
Ubuntu disc: original from Ubuntu (shipit.ubuntu.com), not downloaded.
Thanks in advance. Best regards.

---

### Post by Bloch on 2006-08-25
Does it even begin to boot? Or does it boot into windows?

I am no expert, but it might be the cd drive. I had an older system that had no problem reading cd roms, but was very unreliable about booting from a CD-rom - about 2 times in 3 it failed to boot from the CD-rom.

You have a cd-writer - perhaps you could download and burn an iso of Puppy Linux and see if you can boot from it? (They have a 'live disk')
Have you ever succeeded in booting anything from that CD drive?

---

### Post by orb9220 on 2006-08-25
also if you have more than one cdrom you also have to setup which is  first in the bios or put the cd in the other cdrom drive.

Yep had me stupped for a few minutes.

---

### Post by telegramsam on 2006-08-25
You are restarting right?  The computer has to restart in order for it to boot into Ubuntu. (You said Windows can see the files on the disc)

Also, the disc has to be an ISO, which isn't a run-of-the mill disc burn.  You might try burning one that you download--sometimes discs are just bad.

Also make sure your BIOS has the CDROM first in the boot order.  Which it appears is what you have...

---

### Post by nalmeth on 2006-08-25
Does it try to load and fail, or does it simply skip right to windows?

Are you sure you burned the disc as an ISO?

When in windows, I use this app to burn ISOs:
[http://www.terabyteunlimited.com/downloads/burncdcc.zip](http://www.terabyteunlimited.com/downloads/burncdcc.zip)

---

### Post by Minemapper on 2006-08-25
I'm having exactly the same issue.

ISO file is burned correctly as such. Manually set the single CD drive to boot first. System ignores that and boots straight to XP. ](*,) 

*edit...This is the filename of the distro I downloaded and burned

ubuntu-6.06.1-desktop-i386.iso

TIA

Matt

---

### Post by clapper65 on 2006-08-25
I would suggest booting with a known good CD, Windows recovery CD etc.  If that doesn't boot then you know it's your drive, otherwise  you probably have a bum CD.

---

### Post by cmolinap on 2006-08-26
Guys, thanks so much for yours comments; my english is very bad, but I do my best to make me undestands in order to explain all of you exactly what is going on: I receive recently a package from Ubuntu-Canonical with five disk of Ubuntu 6.06 LTS My purpose is change my SO (actually WinXPSP2) to Ubuntu, but before to do that I want try Ubuntu from the live cd. 

I change the BIOS setup to boot from the CD-R/RW, in first place, (really I have two: the first one as master -the CD-R/RW-, and the second one as slave, a CD-R). When I insert the cd in the cd-r it boot and show me the browser window, I can read all the info regarding Ubuntu and the apps that I can install in Windows (like FF, Thunderbird, etc). When I restart the PC to boot it with the live cd, don't catch the live cd, instead windows start as normally do. Well, I try another combination in boot secuence: floppy in first place, cd-r/rw in second place and HD the last one. The same result. Windows start up normally.

I test all the five cd received from Ubuntu-Canonical, I don't think that all the five cd are bad (the chances are almost zero), but, again, the results are the same. Don't boot. I don't have problems with anothers cd with windows apps.

Again, thanks all of you for yours comments, I appreciate that.

---

