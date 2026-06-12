---
title: "LiveCD booting problem"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ichimeno on 2007-03-20
Hi everyone i'm new to this forum. I've found out about Ubuntu and have decided to try it so i got the Ubuntu 6.10 Edgy Eft LiveCD and tried to boot it. So the meu pooped up and i chose the first option to install it on a clean HD. So its loading the desktop and right after the cusor on the very top right of the screen it became orange and then nothing happened. Is this like a video problem cause the same thing happened when i tried Fedora Core 6, Debian and Xubuntu. Is there a way that i can fully load up the desktop and install ubuntu? 

Here are my PC specs:

2 160 gbs HD on RAID
Nvidia 6800
1gb RAM
Intel Pentium D


Thnx in advance.:)

---

### Post by jbayone on 2007-03-20
Maybe I'm not following right.  Have you installed it yet?  Or is this a problem with the live CD?  If you can't even boot up with the CD, try safe graphics mode.

---

### Post by ichimeno on 2007-03-21
i hadnt even installed it. like before it boots the desktop the screen is orange and stays that way forever. and i tried safe graphics mode but that didnt work either

---

### Post by BobG999 on 2007-03-21
I'm having the same problem. I popped the disk in and it booted to the main choices. I took the first option live and install - or whatever the actual wording is.

It's now been sitting at a basic dull orange/brown screen for two hours grinding away at the cd rom!

I downloaded it this morning, burnt the CD (with verify). There is a pointer on the screen but has little response when i move it - though it does eventually jerk round the screen in between cd rom grinds.

It's a lowly little laptop so I let it carry on, in case the spec of the machine is causing problems, but two hours is silly.

Has this been heard of before? Is it a dodgy disc? Is there an MD5 hash for the ISO?

TIA for any help.

TTFN
BobG

[edit] Found the MD5 hash and it matches the website (Ubuntu 6.06.1 LTS (The Dapper Drake): June 2006) and I'm now trying the safe mode install. As before it got to the Ubuntu Mac OS icon loadery thingy. If it works I'll post back [/edit]

---

### Post by twikletoes on 2007-03-21
What are the specifications of your computer? How fast is your processor?

I actually had that same problem myself and i found out my computer wasn't good enough for a desktop livecd. I downloaded the alternate CD and installed it that way and it worked just fine.

---

### Post by BobG999 on 2007-03-21
Machine specs:
Toshiba Tecra
300Mhz or thereabouts
128mb Ram (I have a suspicion this might be the problem, when i was looking for the MD5 I noticed the 256mb requirement :( so this could be my own stupidity!)

I'll try the alternative version after this current test.

Thanks for the heads up.

TTFN
BobG

---

### Post by jrandolph on 2007-03-21
I had a problem that sounds just like this --
mine ended up having to do with APIC if I booted it and put apic=off at the end of the boot line it booted fine -- 
I dont know but I thought I would let you know of my problem

---

### Post by ichimeno on 2007-03-21
ok im gonna go download the alternate vers and if that dont work then ill try wit APIC off thingy

yea i have the edgy eft and i thnk thats the alternative..it doesnt work :(

---

### Post by twikletoes on 2007-03-21
If you say it is the alternate then it would come up with a blue screen after you have chosen the text mode or oem mode.
if you have the desktop then you will com up with a orange background and it would try to load the desktop environment with the gnome panel and the install button

---

### Post by oilchangeguy on 2007-03-21
given your machines specs, 300mhz. cpu and 128mb of ram. your machine does not meet the requirements to run ubuntu. you may want to try xubuntu, or damn small linux.

---

### Post by Bartender on 2007-03-21
> **BobG999 said:**
> Machine specs:
Toshiba Tecra
300Mhz or thereabouts
128mb Ram (I have a suspicion this might be the problem, when i was looking for the MD5 I noticed the 256mb requirement

OK, two things here - the LiveCD won't work with only 128 MB RAM.  
Secondly, even if you can get it to install with the alternate install version, the finished product is going to be loggy and slow to respond.  I'm not sure it'll even run.
Your best bet is to look at lightweight distros like DamnSmallLinux or Xubuntu or maybe that new Fluxbuntu

---

### Post by sk8dork on 2007-03-21
[here's a how to]("http://community.fluxbuntu.org/index.php/topic,205.0.html") on how to install fluxbuntu on a tecra 8000 (not sure if this will help you or not, the guy that wrote the tut apparently had 256mb ram, but some people have gotten fluxbuntu to run on 64mb of ram i think).

personally i use fluxbuntu on slow and fast machines. it's nice.

---

