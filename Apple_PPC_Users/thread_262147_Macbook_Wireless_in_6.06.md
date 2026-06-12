---
title: "Macbook Wireless in 6.06"
date: 2006-09-21
forum: Apple PPC Users
---

### Post by auximini on 2006-09-21
Hello -

I downloaded and tried 6.06 as a Live CD (have not installed it to my hard drive yet) last night. I noticed the wireless did not work. Doing some searches in the forums (keywords ath0 and Macbook), I see that some people think that there's a problem with the madwifi drivers.

Can anyone confirm a previous Ubuntu release that works with wireless out of the box? I just want to verify that I'm able to get wireless working before I install it. After that, I can pin the madwifi release in apt from being updated.

Thanks
-Joe

---

### Post by Neobuntu on 2006-09-21
Welcome to Apple. It's funny how that that limited set of hardware, that  Apple writes for, tends to work about as good as Win-modem did (including  in Windows)in 1995. You see, they must play fair, but they have no incentive to help you.

As a solution, I'd say to do just what you would if you find your Windows box (you bought) has an unsuported (and not reverse engineeer yet) cheap Wireless device. Spend $10 and pop in a known automaticlly working substitute. It beats beating your head against a wall.

Seriously, if your wireless doesn't just work with the latest (k)ubuntu today AND you can't use an XP driver (via ndiswrapper) for it either (remove other driver/modules first) then just google a known champ. I got mine for $10 PCMCIA, shipped free and no sales tax! (and I still wrap another with ndis-GTK. It's point and click the XP driver upon automatic "kernel" upgrade. No problem.) 

There's no doubt, my zero driver set-up 802.11 PCCARD is the way it should be. Do your home work, It's not Ubuntu's fault. Go native!

---

### Post by auximini on 2006-09-21
Thanks for your reply.

Since the Apple Bootcamp CD contains windows drivers for the wireless card, ndiswrapper might be possible.

However, I've read several stories from people who say their card worked right away. I'm assuming this was a previous version of Ubuntu with an older version of the madwifi drivers.

I agree that it's not Ubuntu's fault. I was just curious as to which version of Ubuntu people used when they say that their wireless card worked.

---

### Post by Neobuntu on 2006-09-21
Me too. Yeah I just want all to know the real unpunished anti-competitive stuff going on and that we can just use/buy another device today, on the cheap.

I too would like to play with Kubuntu on a Mactel but I already know, it's disadvantaged compared to mainstream hardware. One thing you don't want with computers, is needless complications. The development lags.

I'm proud Kubuntu is a major step in our time saving direction.

---

### Post by sbentzen on 2006-09-22
did you try to do it on the live cd, cause if you did it won't work.

---

### Post by auximini on 2006-09-22
Yeah, I originally tried it on the live CD. You're right -- it didn't work.

I installed Dapper on my Macbook last night in hopes that upgrading to the latest kernel and module revision would get it to work, but no luck.

The card is recognized and I can scan for networks, but it will not join a network. It's very similar to this problem:

[http://thread.gmane.org/gmane.linux.drivers.madwifi.user/11492/focus=11492](http://thread.gmane.org/gmane.linux.drivers.madwifi.user/11492/focus=11492)

I've now realized that there probably isn't a previous Live CD that I can fall back on to test this out. That and now that it's installed on my hard drive anyways, it doesn't matter. I'm now more focused on what kernel and madwifi version is installed on the working computers.

From most of the reports I've read, people had wireless working on their Macbook until a certain update and thats when all the problems began.

---

### Post by auximini on 2006-09-23
OK. I got my wireless to work. I compiled the madwifi drivers from the SVN repo. After that, wireless came right up.

---

### Post by rscow on 2006-09-23
I have a macbook.  I had wireless out of the box IF I booted into Ubuntu, then opened Networking.  Then disabled ATH0 if it were up. THen enabled ATH0.  When it was up, I opened a terminal and typed sudo ifup ATH0. And I would be off to the races.  It never went down until I rebooted.

Now, I got some EBDA error on booting yesterday, and couldn't fix the problem with the LiveCD.  Don't know what went wrong, but LILO wouldnt run.  So, I reinstalled Ubuntu.  My setup was kind of crazy anyway, because I had been adding stuff and building stuff and really didn't know what I was doing.  

When install was done, I went with the usual triple/dual boot steps, like at /bin/false.  THEN I installed Network Manager and rebooted.  All of a sudden Network Manager worked, and I can see adn connect to wireless networks all over the place.

Go figure.  Long post, but I find stuff can be made to work.  If only I could get my hfsplus partition to mount properly, I'd be very happy.

Roger

---

### Post by hajk on 2006-09-24
Probably due to some upgrade of the madwifi-ng drivers. I've heard of people compiling the latest madwifi-ng source code and having the ath0 interface up in a flash at full 94/94 signal strength when next to the wireless AP. 
No such problems when running Ubuntu in a Parallels VM, BTW, since the underlying OS X interface for the wireless is used...

---

