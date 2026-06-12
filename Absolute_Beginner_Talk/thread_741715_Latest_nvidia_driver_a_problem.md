---
title: "Latest nvidia driver a problem?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-01
I haven't had a chance to try this myself yet, as I am waiting on replacement hardware so I can actually see my hard drives again.  My probems started with a GeForce 6600GT and trying to get it working in Gutsy.  Envy was of no use - it installed the latest driver from nvidia and made the device "amd" - the "nv" and "nvidia" modules weren't found.  I tried downloading the driver from nvidia and it would bomb out with a compiler mismatch.  What I am wondering is if someone else having problems with the nvidia driver as of late, be it via Envy or by direct download, has tried an archived version to see if it works?

Thanks!  :)

---

### Post by njparton on 2008-04-01
What's your graphics hardware?

---

### Post by anewguy on 2008-04-01
The "new" video card (I know it's old, but it was given to me a far better than what I currently have :) ) is a PNY Verto GeForce 6600GT.  I had 2 other posts about this problem on this forum, with the net result being with everything I did I should go back and start with a clean install.  When I did that I somehow messed up my BIOS and now I can't access my hard drives, so I'm using the LiveCD.

I installed Envy using my current video card, the shutdown, changed cards, and booted again.  Could not get a readable GUI screen.  In terminal, killed all of X, then ran evny in terminal mode.  It downloaded and compiled everything and made the changes to my xorg.conf file.  Only problem is that it made the driver "amd" and a subsequent startx of course bombed out saying no card found.  Tried "nv" and "nvidia", but it said the modules weren't found.  So I went into Envy in terminal mode again and had it deleted all the drivers.  Next, I downloaded the newest file from nVidia, which aborts saying the module nvidia.ko can't be used because the compiler used for the kernel was different than that for the module -> this is when it was recommended I start with a completely fresh install, and that's when I lost my disk access.

I posted this question as I have seen more and more posts regarding problems installing the nvidia driver lately - be it via Envy or by direct download.  Considering the invalid driver added via Envy (using the same download from nvidia) and the compilation problems with the new nvidia download, I was wondering if some sort of identification bug was introduced and hence why myself and others are having problems.  And, if so, if anyone had tried one of the archived downloads from nVidia.  I would try myself but I'm waiting on another motherboard, processor and power supply so I can try to access my hard drives again.  The board and processor are used, and probably considered old by today's market, but I'm on disability so it's all I could afford.  It is a KT7-RAID with an Athlon 1000 processor.  I ordered the new power supply as mine is currently only 250 watts so it needs to be upgraded.

;)

---

