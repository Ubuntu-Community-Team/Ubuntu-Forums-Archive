---
title: "HELP! Partitioning without killing OS X..."
date: 2008-10-07
forum: Apple Hardware Users
---

### Post by phmadore on 2008-10-07
Hi,

Okay, so I've been trying to figure out how to install Ubuntu on my iBook. Gotten pretty far being a complete mac novice, but now I've hit a wall. I have to resize the partition of OS X, which is dedicated to OS X (there is not enough otherwise space to install...), but I cannot figure out how to do this. I did some research and found this: [http://ubuntuforums.org/archive/index.php/t-89960.html](http://ubuntuforums.org/archive/index.php/t-89960.html)

I got as far as using parted, right, but then it was automatically on "/dev/hdb" which is an 800MB device I have no knowledge of... So I figured out how and attempted to "select" HDA, the 27 gig device, to no avail. It says I do not have permission to access it. Why would this be?

Thanks in advance... I would like to get Ubuntu running by Thursday midnight so I can take it on my trip with me in working order... I want to dual-boot OS X with it because OS X didn't turn out to be such a piece of crap after all (if you're a little patient)...

Thanks.

---

### Post by thenes on 2008-10-08
It seems that you are new to os x. If you have os x 10.5 (leopard) on the iBook, you can easily change partitions using boot camp. I think that [hhis guide]("https://help.ubuntu.com/community/MacBook#Basic%20instructions") would work similarly on an iBook with boot camp, as on the macbook mentioned in the guide.

If you are on os x 10.4 (tiger): I tried to go through the guide you linked to and read the help file for parted, but I was able to find out how to gain the permission you were denied using parted. (I am a newbie user, but thought that my answer is better than no answer. Someone else on the forum will probably be more able to help you if using parted is the only way to go for you).

How ever, if you are able to back up your data, I think the easiest way would be to make a fresh install of tiger. Then you would use disk utility during the install of tiger to divide the disk into two partitions and install Ubuntu on the second partition after you have installed tiger.

You might be a much more experienced user than me, and thus this post might only have stated the obvious. However, I hope I could be to some help.

---

### Post by phmadore on 2008-10-08
Actually, the newest OS X you can have on the Apple iBook G3 800 (dual USB) is 10.3.9, so even if I was to buy a new OS X it would do me no good. I bought this laptop on eBay--it came booted with a lot of programs but did not come with a reinstall disk. I asked about one and they gave me some info on where I might get one from, but didn't include one. There has to be a way to do this without wiping my hard drive.

---

### Post by cyberdork33 on 2008-10-08
> **thenes said:**
> It seems that you are new to os x. If you have os x 10.5 (leopard) on the iBook, you can easily change partitions using boot camp. I think that [hhis guide]("https://help.ubuntu.com/community/MacBook#Basic%20instructions") would work similarly on an iBook with boot camp, as on the macbook mentioned in the guide.BootCamp is only for Intel based Macs. The iBook is a PowerPC Mac.


> **phmadore said:**
> Actually, the newest OS X you can have on the Apple iBook G3 800 (dual USB) is 10.3.9, so even if I was to buy a new OS X it would do me no good. I bought this laptop on eBay--it came booted with a lot of programs but did not come with a reinstall disk. I asked about one and they gave me some info on where I might get one from, but didn't include one. There has to be a way to do this without wiping my hard drive.
I have 10.4 on an iBook G3 Clamshell. I am pretty sure you can get it on yours too, not that it matters all that much since that is not even what you want.

Have a look at the PowerPC FAQ. I think you can use the Ubuntu CD to resize your OSX partition and create the needed partitions for Ubuntu.

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by rjcalifornia on 2008-10-09
don't forget to format as "empty space"!

---

