---
title: "HELP! Reinstalling Ubuntu on Intel iMac FAILED!"
date: 2006-07-07
forum: Apple PPC Users
---

### Post by Greywhind on 2006-07-07
I followed the directions on [http://www.planetisacc.com/articles/ubuntuinstall.html](http://www.planetisacc.com/articles/ubuntuinstall.html) to install Ubuntu on my Intel iMac. It worked. I then did a few things that I wanted to get rid of, so I decided to reinstall. I followed his directions again EXACTLY twice, and each time rEFIt came up with a menu having only MacOS and "Legacy OS" with no Linux logo, and said "No operating system found" when I tried to boot into the "Legacy OS" -- I don't know what to do! I removed the linux partitions and re-did them both times, so all previous info should have been gone! Why doesn't it work now?

Please tell me how I can reinstall Ubuntu and get it working - even if it involves reinstalling OS X and repartitioning to one partition and then splitting again and starting over.

---

### Post by chasisaac on 2006-07-07
> **Greywhind said:**
> I followed the directions on [http://www.planetisacc.com/articles/ubuntuinstall.html](http://www.planetisacc.com/articles/ubuntuinstall.html) to install Ubuntu on my Intel iMac. It worked. I then did a few things that I wanted to get rid of, so I decided to reinstall. I followed his directions again EXACTLY twice, and each time rEFIt came up with a menu having only MacOS and "Legacy OS" with no Linux logo, and said "No operating system found" when I tried to boot into the "Legacy OS" -- I don't know what to do! I removed the linux partitions and re-did them both times, so all previous info should have been gone! Why doesn't it work now?

Please tell me how I can reinstall Ubuntu and get it working - even if it involves reinstalling OS X and repartitioning to one partition and then splitting again and starting over.


The easiest way may be reinstall X from the disks, takes less then one hour, the restart Ubuntu install. 

The same basic thing happened to me and I reinstalled X and just took some time. Needess to say I spent some time doing other things. 

My next step is to delete my X partition and run 100% linux while keeping OSX on a bootable external drive.

Edit: Oh yeah totally reformat the macintosh drive.

---

### Post by Greywhind on 2006-07-07
Actually, there's one thing I have to to try first because I think I know what the problem is:

I started the process plannning to install all 3 OSes on my Mac (I still plan to...) and therefore I made a Windows partition. This partition was located at the end of the drive, as it must be. But when I reinstalled Ubuntu, I think I put the Linux Swap drive AFTER the Windows partition, thereby ruining the install. I'll try it again today, fixing the order, and if it doesn't work I'll probably just reinstall everything like you said.

---

