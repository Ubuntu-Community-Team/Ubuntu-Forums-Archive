---
title: "a really simple question about Remastersys. any takers?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by ijason on 2008-02-12
hello all.

i just used remastersys to make a live install dvd following this tutorial ([http://www.systemshock.co.za/forums/index.php?showtopic=19101&st=0&p=173852&#entry173852](http://www.systemshock.co.za/forums/index.php?showtopic=19101&st=0&p=173852&#entry173852)), but before i label the disk i was wondering if the disk only contains drivers for the hardware in the machine remastersys was used on? or does it contain all the universal drivers of a normal live cd?

in other words, is this an install cd that is now specific to the machine i made it with, or is it a globally usable install disk?

thanks!

---

### Post by dstew on 2008-02-12
I think that a regular Ubuntu installation retains all the drivers for different hardware, so if you change something (add a video card for example) you do not need to re-install. People tell me (but I haven't checked this out) that you can install Ubuntu into a hard drive on one computer, and take that drive out, put it in a different computer (has to be the same processor of course, but can have a different motherboard, memory, hardware etc.) and the system will boot and run. You sometimes have to reconfigure the video (dpkg-reconfigure xserver-xorg) but they say it will run.

So, probably the disk made by that tool will be globally installable.

---

