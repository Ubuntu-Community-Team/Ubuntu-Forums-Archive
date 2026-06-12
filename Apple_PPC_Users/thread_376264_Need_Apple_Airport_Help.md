---
title: "Need Apple Airport Help"
date: 2007-03-04
forum: Apple PPC Users
---

### Post by Matt_Pitt on 2007-03-04
I've tried not to post too soon, but I cannot get my Apple wireless card working.  I have a G3 iBook with a legacy Airport card installed (not Airport Extreme).  It worked perfectly under OS X.  I've read many of the post and must be missing a step.  I tried to do various things indicated in the posts with no luck.  I am running Ubuntu 6.10.

Here is what I get when I type iwconfig:

lo  no wireless extensions

eth1  IEEE 802.11b  ESSID: "MW"  Nickname: "HERMES I"

It then continues with other information, but shows no access point.

eth0  No wireless extensions

sito  No wireless extensions


I've tried everything from telling my router to use no security, to trying WEP and have had no luck.  I have downloaded WiFi Radar but it cannot see the router either.

It seems like I am missing some piece that lets Ubuntu "talk" to the older Airport card.

When I am plugged into via CAT-5, it works fine.  I just cannot get the wireless to work.

Anyone have any ideas?  Is there some other package I need?

Thanks very much!

---

### Post by aysiu on 2007-03-04
I know you say you've tried a bunch of stuff, but since no one's answered you in five hours, I figured it might be worth throwing another link at you, even though it's for a G4 with Ubuntu 6.06, and you're using a G3 with Ubuntu 6.10.
[http://joona.kuori.org/ubuntu-powerbook/](http://joona.kuori.org/ubuntu-powerbook/)

---

### Post by monkeytwotwo on 2007-03-05
Hello Matt_Pitt

I think I can help you. Your problem is that Ubuntu includes the driver for the wireless card, but not the firmware. So it only works partly.

Check this out, it helped me:
[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx)

I'm on a PB 15" G4

Have Luck!!!

---

### Post by Tommy on 2007-03-06
But the original poster said he had an ORIGINAL Airport card (not Extreme, so not Broadcom). I believe the original Airport card uses the Orinoco driver.

---

### Post by meathook on 2007-03-06
i have a g4 ti with legacy card that's not airport extreme. it was a "key largo mac i/o" or something or other when listed with lspci from command prompt.  it worked out of the box though, minus wpa support. after researching, it doesn't support wpa so i put in another pcmia eth card to use. but your eth controller for wired is seperate from your wifi so having it work connected won't really help you troubleshoot your wifi. i think best way is to see which chipset your wifi card is using and start from there. doesn't seem like all legacy airport cards use the same chipsets from my research.

---

### Post by Matt_Pitt on 2007-03-10
Thanks, everyone.  I am going to try and see what chipset my card uses, and then try and find an appropriate driver.

Thanks for your help.

---

