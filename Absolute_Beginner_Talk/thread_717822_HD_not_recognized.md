---
title: "HD not recognized"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by runnerdi7 on 2008-03-07
tried installing Gutsy using the livecd, It made it all the the way through the install, then when I attempted to boot it up, It froze pretty much immediately. I just tried installing again with the text based version, the install went fine until the partition hd section where the computer did not recognize my hd at all. This is the hard drive I'm running

Toshiba / Hitachi 120GB 2.5inch 5400rpm 8MB SATA Notebook Hard Drive

This is a Serial ATA drive, not a Parallel ATA (PATA) drive.

Capacity: 120 GB
Rotational Speed: 5400 rpm
Cache: 8 MB
Interface: SATA 150
Max. External Transfer Rate: 150 MB/s
Seek Time:
Track to Track: 2 ms
Average: 12 ms
Full Stroke: 22 ms
Shock:
Operating: 325G @ 2ms
Non-operating: 1000G @ 1ms
Dimension (WxDxH): 3.94 x 2.75 x 0.37 inch
Weight: 0.22 lbs

can anyone suggest a driver for it? The text based install gave me a list of drivers to choose from, I just don't know enough to figure out which one (if any) would work.



Another issue I had was even when using the live cd, I have never been able to load in anything other than safe graphics mode. I don't know if thats why the first install i did failed or not. I'm not sure if that means something to whether i am going to be able to install this or not.
__________________

---

### Post by Hospadar on 2008-03-07
You might have a hard drive with a flash memory cache (my dell laptop does I know) which requires special raid drivers/settings.  To solve this you may want try going into the bios and disabling the cache.

This may not be your problem, but it sounds similar to when I first tried to install OS's on my lappy so it may work for you.

---

