---
title: "What's the proper way to prepare for an upgrade to Feisty/Beryl?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-29
Greetings!

I'm looking forward to the feisty upgrade that is due out next month.  I figure once I get that up and running, I'll give a shot at getting Beryl going.  My question is this:  What and/or how do I have to backup so if things get fouled up I can easily revert back to the last working configuration?  I've installed the "simple backup"  and have it set to do a back up nightly with a full backup weekly.  Is that enough?  Should I mirror any directories on another hard drive (I have PLENTY of space)?  If Beryl some how gets gacked up and the desktop becomes unusable, is getting it un-gacked as easy as reverting to a pre-Beryl xorg.conf?

As always, thanks for the help!
Brian

---

### Post by dbbolton on 2007-03-29
first off, i would recommend that you DO NOT upgrade to feisty unless you have plenty of experience, and are prepared to deal with A LOT of bugs. last i heard, feisty was still alpha. i don't know if that's the case, but it seems that a lot of beginners are posting threads here about feisty problems. it s my opinion that "absolute" beiginners should stick with dapper.

i especially don't think you should upgrade just to try and get beryl running. feisty is for devs and testing users. anyhow, beryl isn't that great. i'd rather have a stable, boring system any day.

there is a nice back-up utility that you can install with automatix- you should check it out if you decide to upgrade.

---

### Post by gogogo111 on 2007-03-29
Well as of now, Feisty is in Beta. But to answer the original question, I believe the best way to prepare for a upgrade is to back up your data, and hope for the best. Someone more knowledgeable may help you with the more technical standpoint. :)

---

### Post by seshomaru samma on 2007-03-30
> **dbbolton said:**
> first off, i would recommend that you DO NOT upgrade to feisty unless you have plenty of experience, and are prepared to deal with A LOT of bugs. last i heard, feisty was still alpha. i don't know if that's the case, but it seems that a lot of beginners are posting threads here about feisty problems. it s my opinion that "absolute" beiginners should stick with dapper.



I second that

---

### Post by Drakkor on 2007-03-30
I run a dual boot XP/Ubuntu,on seperate drives machine and regularly back up image,the entire Ubuntu drive (second) to my (first) drive. That way if I screw up anything, a perfect working Ubuntu installation is about 10 minutes away !!
I use Acronis True image, and it will make a perfect image of your Ubuntu system,
boot loader and all !  :)  BTW, It's just my personal preference but usually a clean install is the best , seen lots of "upgrade" problems here.

---

### Post by RobMBaker on 2007-03-30
I agree with Drakkor on two counts:-
1) Image backups are probably the 'safest' way to go; so that you know you'll get EVERYTHING back the way it was before the 'upgrade'
2) Clean installs are easiest - obviously, it's just a case of writing new stuff (with a few install options) to the disk; but there are a LOT of things that can go wrong with upgrades, as it's hard to make sure *every* possible system configuration will be upgraded correctly ... I had issues upgrading to Edgy from Dapper, mainly because of config files that the installer either tried to overwrite, or just didn't check to see if the current settings would work in the new version.

I'm going to wait until Feisty is released, and then some, so the early-bird users can find all the major bugs! I can't afford to spend days faffing about with config files and the like - but if you can, then go for it! And good luck :P

---

