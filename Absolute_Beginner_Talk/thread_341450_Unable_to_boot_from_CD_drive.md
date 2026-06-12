---
title: "Unable to boot from CD drive"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by ACF1 on 2007-01-18
I am knew to Linux and Ubuntu so Thanks to all who help me out.:D 

I have an Ubuntu Edgy CD that I know is good.  I did all of the checks and ran it from the CD drive on our fairly new Laptop (Gateway with Windows XP).  It worked well on that computer.

Now when I try run it from the CD drive on an older computer (It has 256 mb of ram and Windows 98SE) I have problems.  The Ubuntu screen comes up with the options (run from CD drive, check CD for problems, etc.) just fine.  But when I try to run it from the CD drive it does not work.  The window that says "Starting..." "Loading Linux Kernel" freezes at 12% (most of the time, one time it stopped earlier).  Then a window comes up that says "I/O error" and "Error reading boot CD"  

Is there something wrong with the CD drive?  It works for other things.

Thanks for any help

---

### Post by JamieC on 2007-01-18
It may be possible that the disc is corrupt. Did you check the checksum was correct before burning the image to disc?

---

### Post by ACF1 on 2007-01-18
> **JamieC said:**
> It may be possible that the disc is corrupt. Did you check the checksum was correct before burning the image to disc?

I did and they were correct.  

The problem only happens on the older computer, not the newer one.  So the CD should be good.

---

### Post by JamieC on 2007-01-18
Hm, it may be possible that the drive is having issues.

Have you tried using safe graphics mode? You could also try the alternate CD (providing you intend to install it of course)...

---

### Post by ACF1 on 2007-01-18
I tried it in safe graphics mode and it did not work.  

Is it possible that the CD drive is just too slow?

---

### Post by JamieC on 2007-01-18
Irregardless of how slow it is, it should still eventually load...

---

### Post by Hendrixski on 2007-01-18
that's an interesting problem.  Have you tried other linux distributions for this older computer?  like maybe Damn-Small-Linux?  That thing can load on ANY piece of hardware you throw at it.

---

### Post by irish_flu on 2007-01-18
This won't help you at all, but I have an (otherwise very very nice) box which, for some unknown reason, hates booting to CDs and USB keys (even though the six-month-old motherboard supports both).

You mention that the CD drive works for other stuff; is that just using CDs, or booting from other CDs?

You might want to research and see if there's an updated BIOS for your motherboard that clears up some errors related to booting to CD (guess I should follow that advice myself).

---

### Post by bodhi.zazen on 2007-01-18
Do you have a floppy drive ?

	[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by ryantmer on 2007-01-18
I also had problems booting from this machine's CD drive, and it turned out to be a problem with the CD drive itself. I just replaced it with another one I had lying around, and it worked splendidly.

---

### Post by ACF1 on 2007-01-18
> **irish_flu said:**
> This won't help you at all, but I have an (otherwise very very nice) box which, for some unknown reason, hates booting to CDs and USB keys (even though the six-month-old motherboard supports both).

You mention that the CD drive works for other stuff; is that just using CDs, or booting from other CDs?

You might want to research and see if there's an updated BIOS for your motherboard that clears up some errors related to booting to CD (guess I should follow that advice myself).

I have not tried booting anything from the CD drive before.  We did install Windows 98SE not to long ago from that CD drive but I do not think that required booting from the CD drive (I am not sure though, a friend helped).

Is there any way to figure out what kind of motherboard I have with out opening the case? But I am not sure that the BIOS is out of date because it did boot up to the Ubuntu screen that lists the options for what you can do.

---

### Post by ACF1 on 2007-01-18
OK.  Puppy Linux boots from the CD drive just fine.

---

### Post by ACF1 on 2007-01-19
Still no go.  I can not boot past 12% loaded of the Linux kernel.  And I can not boot in safe graphics mode nor can I do the CD check.  But on our other computer I can do the CD check and it was good and it boots up just fine.  Any Ideas?  Thanks.

---

### Post by bodhi.zazen on 2007-01-19
Try the alternate CD, although it will install and not run "live"

Try Fluxbuntu:

[Main page](http://fluxbuntu.org/)

	[forums](http://community.fluxbuntu.org/)

	[ Download fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

	MD5SUM  : 
	> c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso

You can install Fluxbuntu and then, if you like,

[code]sudo aptitude update && atpitude upgrade && install ubuntu-desktop[/url]

---

### Post by ACF1 on 2007-01-20
I was thinking.  Could it possibly have something to do with the computer?  It has 256 mb of ram and a Pentium III processor.  I am going to download the alternate CD.  But that looks like it is going to be considerably harder to install.  Thanks.

---

### Post by bodhi.zazen on 2007-01-20
It is not that hard to install from the alternate CD

Here is a nice how-to:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by LavaHot on 2007-05-11
I'm having a similar problem. Did the Alternate install work for you ACF1? I'm running a celeron 500MHz w/ 256 MB. I'm planning on using it in a MAME cabinet conversion. I'm going to try Xubuntu first, then I'll go with the alternate install of Ubuntu. Wish me luck.

---

### Post by LavaHot on 2007-05-12
Ok, so Xubuntu managed to load the Kernel, but froze shortly afterward with the blue-tinted cylon-esque Xubuntu loading screen. I'm going to try Fluxbuntu then the Alternate CD.

---

