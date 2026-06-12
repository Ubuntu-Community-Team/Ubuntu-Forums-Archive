---
title: "Low on memory (?!) while running very little"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-08-07
Hello, all.

I seem to be having problems with my system slowing to a crawl intermittently while I'm doing very little with the machine itself.  First the specs of the machine:

Pentium 4 1.5Ghz
512 RAM
nVidia GeForce 6200
Feisty 7.04

The problems occurred while running the following programs at the same time:

Sonata
MPD
Firefox
Gaim

Should my system be lagging to the point where it's unusable while running these programs?  Also, the lagging seems to be happening randomly.  I try to keep an eye on my system monitor, and the CPU will be at 5% or so, and then all of a sudden it'll spike to 100% and the system starts to lag like crazy.

The system has run fine with XP in the past, and had been fine with Ubuntu up to this point.

Any help is greatly appreciated.

---

### Post by oilchangeguy on 2007-08-07
firefox has been known to cause problems, like those you describe. make sure you've got it set to delete cookies, cache, passwords, etc. when you close the browser. and don't have many tabs open, either.

---

### Post by limberlegs on 2007-08-07
Really!?  I did have a few tabs open, but surely this shouldn't be SUCH a burden, should it? Perhaps I'll look into a browser that uses less memory.  According to my system monitor, Firefox is using 30MB of memory right now.  Is that really high?  

Thanks for your response!

---

### Post by limberlegs on 2007-08-08
Well, I think the problem has something to do with MPD and/or Sonata.  It seems that when I try to access Sonata when MPD isn't running, Sonata freaks out and crashes.  I also experienced a severe lag when Sonata was connected to MPD properly.  I *may* have installed MPD incorrectly, but if I did that, wouldn't I have experienced problems other than this?

Any ideas?  Thanks for your help.

---

### Post by igknighted on 2007-08-08
Do you have the nvidia drivers installed?  Sometimes the 2d drivers that come by default make the desktop lag horribly.

Err, in retrospect it does sound like one of those apps is crashing.  Try running them from the terminal to see if there is any error that gets kicked out when it start to do that.

---

### Post by limberlegs on 2007-08-08
Interesting that you should ask about the nVidia drivers.  When I installed Feisty, I followed the procedure for activating the proprietary drivers through: System>Administration>Enable Drivers (?), but it didn't seem to do anything.  I tried to set the screen resolution to 1440x900 but it didn't present that as an option.  So I installed Envy and set up the drivers that way and now everything looks great.  Could *this* be slowing my system down somehow?

I will also try to reinstall MPD/MPC/Sonata and see if that helps.  When I was installing them I was following instructions I found on one of the forum posts here, and I wasn't able to complete some of the steps.  I did some digging and managed to get things to work, but maybe I missed something important somewhere.

Thanks for your reply!  I'll post here if I can get things working.

---

