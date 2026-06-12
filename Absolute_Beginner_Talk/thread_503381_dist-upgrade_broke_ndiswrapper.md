---
title: "dist-upgrade broke ndiswrapper"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by !Klams on 2007-07-17
Having spent a day getting ndiswrapper to work, I did a stupid thing and went and followed the tutorial stickied on this forum for getting my radeon X1900 to work. I say stupid, because I'm running dapper, not feisty (which the tutorial is intended for) and because after doing the dist-upgrade, my wireless no longer works. 

If I try and modprobe ndiswrapper, I get an error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): invalid argument

I went to try re-installing ndiswrapper because I read somewhere that dist-upgrade on dapper can delete random .ko's, only to find that I had the same problem I'd had before, in that make and make install wouldnt work. The reason before was because I hadn't got the kernel headers, which I solved with

aptitude install linux-headers-`uname -r`

only now when I run that, I get the error, temporary failure resolving 'security.ubuntu.com' but of course its going to have that error, I cant get on the net! I guess before it was getting the headers off the CD but now it cant because I updated? 

I read about some issues with bcm43xx, so I blacklisted that, but trying to rmmod bcm43xx tells me that 'module bcm43xx does not exist in /proc/modules' so I dont think thats the issue here.

Any help would be much appreciated, sorry if I've left out any vital info. Its so very frustrating that connecting to the internet is the problem, because it seems every suggestion I come across involves having a connection in the first place!

Cheers.

/edit: Sorry, I realise this is in the wrong forum really, but I dont see how I can delete the thread?

---

### Post by lsutiger on 2007-07-21
[This guide here]("http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html") is for the same card thats in the Dell Inspiron 1501, but it has the same chipset. It's worth a try.

---

