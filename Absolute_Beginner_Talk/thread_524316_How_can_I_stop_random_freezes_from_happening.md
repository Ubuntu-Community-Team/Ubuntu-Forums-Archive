---
title: "How can I stop random freezes from happening?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by juice19 on 2007-08-13
Ok so I really want to like linux and have wanted to make the transition from windows to linux forever but just recently made the move.  
I installed Ubuntu 7.04 with Feisty.

My problem is that my computer freezes all the time now at random.  When it freezes I can move my mouse until i Hit the K start button in the bottom left then everything is frozen.  

I have tried looking all over the forums for help but havent found anything that has helped so far.  
Please help me with this so that I can enjoy Linux.

Some information about my computer:

I have a toshiba Satellite a75 s213.
P 4 3.3 GHz with 1 gig Mem.
Graphics card is ATI Mobility 9100IGP ( I heard theres problems with Nividea but heard nothing with ATI)

System info says my total physical memory is 883.96 MB
Free Physical Memory is 69.50 MB
Disk buffers - 33.52 MB
Disk catch 585.64 Mb
Total swap memory 956.99 MB
Free swap memory 956.99 MB

-------------
Total Free Memory --- 55%
Used Physical Memory 44%
----------

Free Physical Memory 7%
Disk Cache 66%
Application Data 22%
-----

Please help me know what to do to fix this freezing issue.  

Thank you sooo much for looking at this post.

---

### Post by ramjet_1953 on 2007-08-13
As you have an ATI card, it sounds like you may be having issues with video.

Have you loaded the ATI driver?

Are you running any desktop effects, such as Beryl, Compiz Fusion?

Regards,
Roger 8)

---

### Post by tgalati4 on 2007-08-13
Turn off your screen saver.  Sometimes the random screen savers will bring up a 3D screen saver that will hang the video.

If that doesn't fix it, then run from a live CD in safe graphics mode and let it run for several days.  If no lock up, then you can be pretty sure that it's a graphic chip problem.

If you play a lot of games in windows, it's possible that you have warped your graphics chip.  Build quality on modern laptops is poor.

---

### Post by juice19 on 2007-08-13
Thank you for your replies first of all.  As far as screen saver I do not have one set up.  I also don't have any desktop effects enabled or installed.  I would try the live Cd but my friend was the one who installed Ubuntu for me and we just moved so I dont have the CD. 

I ran memtest86 last night 8 times and there is no problem with my memory.  From what I have read on the forums it sounds like it is due to my video drivers.  I did not install anything related to those and I am pretty sure my friend didnt either so they must be what ubuntu autodetected.  

I know how to change the drivers from proprietary in windows but have no idea how to do this in ubuntu.  Like I said I want to learn linux better and like Ubuntu sorry if this sounds really newbish.

Thanks for your help again.

---

### Post by toidi on 2007-08-13
You could try installing the drivers through the 'Restricted Drivers Manager'.  You can find it by clicking on System>Administration.Restricted Drivers Manager.

Your ATI driver should be listed there. Try ticking it and follow the instructions to install.

There is other ways to get them installed.. I found this guide to suit me best when installing my x1800 card
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hope this helps.

---

