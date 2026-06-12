---
title: "Mac Performa 475 Revival~!"
date: 2006-09-05
forum: Apple PPC Users
---

### Post by bunny64 on 2006-09-05
**Hello Ubuntu Community ^o^~!**

*(Scroll to bottom to cut to the chase).*

I'm a 17 year old Software Development student from the UK, who has been in love with computing since he first got his paws on an Atari ST at the age of 2 :O.

I've gone though quite a few machines and operating systems in my time: Atari ST/TOS, i386 Win32 (95, NT, 98, XP)/ Linux (SuSE 6.1 -> 10.0, Debian, Slackware, Ubuntu), Macintosh (G3 OS 9.2 -> OS X.4 / Ubuntu, Motorola 7.0 -> 8.1); and throughout my life I've developed a great affection for the Macintosh (allthough cautiously dubious of Steve Jobs).

Unfortiently on my current course of education I've had to sacrifice my Mac obsession to run a 64bit AMD machine running Windows (allthough when I get a chance to slip over to the other partition I run Ubuntu 6.06).

However~! The other day in the IT Lab I stumbled accross a Macintosh Performa 475, a beautiful machine, inside and out, even with the beige plastic exterior. And after following up a few leads to make sure the machine was completly out of use, I was allowed to take him home :3.

But~! He does not boot ;--;. I can hear the HDD cycling, I can see the fan moving... but nothing on my monitor :\. I don't even hear the chimes.

This may have been a result of being left in a room with bored (and often complely disinterested) teenagers for 5 years without any TLC. And thus, may, truely be ******.

I can't accept this tho~! Not yet! I love this machine, the modular, compact design, the inivotive case, and also, the scientific applications and documents that apparently lurk on that HDD.

I'm wondering if there is anything else that may have gone wrong... For example, I'm currently leaving it plugged into the mains and on, in an attempt to charge the BIOS / Computer Clock Battery / Whatever (correct term?). I have a spare one from another (larger, far more ugly and powerful) Performa, but it looks completly different.

It may be a case of simply having to replace almost every part, or building something newer (a friend of mine has offered to donate his iBook G3) into the case.

But is there anything else I could have missed? I see no additional memory, however allot of what appears to be on board RAM.

There is no obvious physical damage, however there could be years of static that I unleashed on it when I first picked it up....

Why did I ask this here? Well, I've tried a number of seamingly more relevant forums, newsgroups, email addresses, to no avail. And I have noticed a small, but consistant, group of hardened Mac users her in the PPC section of the Ubuntu Forum. And thought, that allthough I shan't be porting anything close to Ubuntu onto this 68k machine, that I would be giving it a shot.

I plan to (hopefully) run either the Mac OS that's installed, OS 8.1, or NetBSD, and use the machine to manage things like IdleRPG, email and newsgroups, to play old Macintosh games, do some old school development, check out the apps that are hopefully still on the HDD and perhaps give it a new LCD monitor and use it in a very visible place, for IRC etc.

(If I can find a SCSI ethernet interface and drivers that is).

Oh and the other thing I may do (at some point... maybe <.<), is make a 68k version of Ubuntu~! Complete with GUI? Who knows *Shrugs*. But if anyone else is interested in this, or has any knowlege that will help, please reply or get in contact.

*YES TL;DR. But I was in a writing sort of mood.*

Old Mac Performa 475, no screen display but making noises HDD, fan etc (not chimes), possible bios battery depletion? Anything that you could suggest? Thanks :3

---

### Post by Tofu on 2006-09-06
The machine may still be OK. The fact that you can't hear a chime doesn't necessarily mean the machine is kaput.

I have an old Mac 7500 which has the same symptoms. I noticed it had a bent pin on the monitor cable. I straightened it, but the monitor still doesn't work.

Maybe something similar is happening on your machine. The sound volume may just be turned down, and you can't see it because the screen is not working.

Don't write off the machine just yet   :)

---

### Post by jdp on 2006-09-07
I frequent the forums at [http://www.applefritter.com](http://www.applefritter.com) as Jon quite often.  The group over there can help very easily.  ALso, look into the 68kMLA.

Try turning the machine on, wait a few secs, then flip the power switch off and back on quickly, once.  If it comes up, you need to get a new PRAM battery.  Only use a 1/@ AA 3.6v Lithium battery.  Don't use a differnt type of PRAM battery (eg, the 4.5v cube ones) from another Mac.  THe correct battery should run $6-$15USD.  SOme places sell them for fairly cheap and others will rip you off.  I can walk on to a few local battery specialist stores here in the USA and get one for just over $8USD.  If I go to RadioShack (Tandy) they want $14.95, IIRC.

Applefritter is a great site with many very long term Mac/Apple fans.  It's also home of the Official Apple I Owners group. ;)

---

### Post by bunny64 on 2006-09-20
Awesome thank you~! I was just about to modify the case/back IO to fit a iBook 500 logic board x.X; You stopped me just in time :3.

I shall try this straight away~! Thank you both!

(Been wanting an apple 1 for some time now *contemplates*)

I just tried this, and I still get no display nor chime, something I didn't consider was that the monitor is not the original monitor.. I'm using a spare Apple Multiple Scan 15" Display that I had lying around. Could this be an issue?

---

### Post by zxee on 2006-09-22
You may want to have a look at the specs here: [http://www.everymac.com/systems/apple/mac_performa/stats/mac_performa_475.html](http://www.everymac.com/systems/apple/mac_performa/stats/mac_performa_475.html)
The standard vram (video) was 512_k_ so and while I use to work with these older macs-don't fully recall-cause I'm older too :) but your performa may not be able to drive a 15" 
The onboard ram is 4MB-you might do well to upgrade that-I think I even have some of those old simms lying around. As was said previously replace the pram battery and maybe reset the pram (hold down the apple command + option + p + r keys). Good luck.

---

