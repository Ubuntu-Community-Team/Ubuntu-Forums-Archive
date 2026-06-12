---
title: "Questions Before Mac Mini Install"
date: 2005-10-03
forum: Apple PPC Users
---

### Post by billg_g on 2005-10-03
After using Ubuntu on Intel, I've been playing with the livecd on a Mac Mini. Before I repartition and install Ubuntu, I've got some questions:
1. The fan is always running with the livecd. (I assume it is the fan that makin' all the noise.)  Will it stay quiet after I install?  I've seen reports that the fan will run more frequently than on OS X. True? (I rarely see the fan operate on OS X.)
2. The Mini has 512kb of ram. What kind of swapping will I see?
3. If I devote the drive to Ubuntu, but then decide to reinstall OS X, will I see problems?  Any monkeybusiness with the boot sector?
4. Is it worth burning my Mac fonts to a CD and then installing them on Ubuntu for use by X?  If so, how? Googling hasn't uncovered anything.
Thanks.

---

### Post by kingc8 on 2005-10-06
Hi,

I'm running Ubuntu on Mac Mini right now! Its lovely. WIth Breezy I get sound, 3D acc and all.

>The Mini has 512kb of ram. What kind of swapping will I see?

I assume you mean 512MB. Well, I got a Mac Mini 1.42Ghz with 256MB, it wasn't too bad with OSX, for Ubuntu? It swapped out, to be honest, I didn't think it was the bad, sure after 2 or 3 apps, loading slows down to 15 seconds as it juggles swap, but Linux is an old hand at swapping out.

Your 512MB  of ram should be just fine. I popped the trunk on my Mini to put in a 1GB clip. The only thing now is to buy a new hard disk, even when idle it spins up again, bad for movies and even music files.

You are advised to install OSX *first*, and set the partition to something like half the drive 40GB/80GB or whatever you like.

*Then* install Ubuntu, it will spot the Apple FS (Ubuntu can't manipulate Apple's FS, which is why you have to set-up OSX first) and install Yaboot in the right place for you.

Use Ubuntu to set up a FAT32 partition if you want to share data between the partitions. WIndows tech bridging Apple and Linux? -Yes, ironic.

Anyway, it should sail nicely.

If you ever open the Mini case, I personally recommend popping either side first, then moving the blade around to the front, because the opposite side of the case will be under too much pressure to pop, unlike what video's demonstrating the procedure tell you to do.

Good luck,

Cameron

---

