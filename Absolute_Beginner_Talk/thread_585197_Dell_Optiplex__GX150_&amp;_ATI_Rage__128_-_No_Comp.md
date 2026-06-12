---
title: "Dell Optiplex  GX150 &amp; ATI Rage  128 - No Compiz!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by schagg on 2007-10-21
I just put 7.10 (gutsy) on a Optiplex GX150. Everything is stock except the video card. I just put in an ATI Rage 128. 

For whatever reason, no matter what I do, I cannot get Compiz Fusion to actually run (work at all). I've tried all kinds of different guides. At this point, I'm not sure I have the right driver installed, although the install automatically recognizes the video card. So I thought that it would automatically install the correct one.

Could it be that the machine and card just don't have enough power to run Compiz? Below are some guides I've tried to follow. I've reached my limit on Linux knowledge, which isn't saying much since I'm a n00b when it comes to Linux ;)


_*Tried:*_

http://forlong.blogage.de/"#blogentry_451

[https://ubuntu.com/ubguntu/desktopguide/C/hardware.html](https://ubuntu.com/ubguntu/desktopguide/C/hardware.html)

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

[http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)


I'm willing to  try just about anything. What should I try next?:confused:

---

### Post by Paulmd on 2007-10-21
> **schagg said:**
> I just put 7.10 (gutsy) on a Optiplex GX150. Everything is stock except the video card. I just put in an ATI Rage 128. 

For whatever reason, no matter what I do, I cannot get Compiz Fusion to actually run (work at all). I've tried all kinds of different guides. At this point, I'm not sure I have the right driver installed, although the install automatically recognizes the video card. So I thought that it would automatically install the correct one.

Could it be that the machine and card just don't have enough power to run Compiz? Below are some guides I've tried to follow. I've reached my limit on Linux knowledge, which isn't saying much since I'm a n00b when it comes to Linux ;)


_*Tried:*_

http://forlong.blogage.de/"#blogentry_451

[https://ubuntu.com/ubguntu/desktopguide/C/hardware.html](https://ubuntu.com/ubguntu/desktopguide/C/hardware.html)

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

[http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)


I'm willing to  try just about anything. What should I try next?:confused:


The Stock Gx150 is a p3, 933-1000mhz. No more than 512MB ram is supported.

The rage 128 is a decent OLDER gard, but it just doesn't have the horsepower for compiz. It won't run aero, either, in case you're curious. :) These come with 8-32mb ram.

A Radeon 9200 or equivlent nVidia card would do the trick, videowise. I think, however that you also don't have enough processor power for that feature, either. You MIGHT, but... I think not.

This is the long way of saying, no, you probably won't be able to run compiz on that machine. If you spend the money on extra ram (if you have less than 512) and video card, maybe.... but it's not going to be economical.


PS: I just about guarentee that the moderators will shortly move this post to the Desktop Effects section.  The stated reason that Compiz is 'expirimental.' Personally, I think that they should not be shippping beta software, installed and enabled by default (in Gutsy). And then not support it on the main board.

---

### Post by schagg on 2007-10-21
I thought so,,, I guess I was hoping against hope :) I may try a slightly better ATI or nvidia card. Thanks.

---

### Post by schagg on 2007-10-21
Does anyone think this card would work? : 


[http://www.newegg.com/Product/Product.asp?Item=N82E16814121525](http://www.newegg.com/Product/Product.asp?Item=N82E16814121525)

---

### Post by Paulmd on 2007-10-22
> **schagg said:**
> Does anyone think this card would work? : 


[http://www.newegg.com/Product/Product.asp?Item=N82E16814121525](http://www.newegg.com/Product/Product.asp?Item=N82E16814121525)

The card, with the proper drivers, should work. However, the caveats about ram and processor speed (and the beta-ness of compiz) still remain.

I tried the 9200 (which is a step lower than this card) on a sempron 3200+ system, and compiz worked. However, keep in mind that that system runs rings around any p3 (and many p4s) in terms of processor power.

---

### Post by schagg on 2007-10-23
I agree.. I just upped the RAM to 512. but no dice.  But I have devised another plan.

I have a P4 3.2GHz w/ HT sitting in a box. It used to be in a ASUS P4P800 SE board, and ran awesome. Albeit not with linux ;) Soooo, I'm going to get another socket 478 Intel board and get a 1GB stick of DDR400 and just put the chip on that mobo and slap it in the dell case. Keeping the psu, hd, and optical drive. 

That my fellow Ubuntu-ites should do the trick...... I hope:)

---

### Post by Paulmd on 2007-10-23
> **schagg said:**
> I agree.. I just upped the RAM to 512. but no dice.  But I have devised another plan.

I have a P4 3.2GHz w/ HT sitting in a box. It used to be in a ASUS P4P800 SE board, and ran awesome. Albeit not with linux ;) Soooo, I'm going to get another socket 478 Intel board and get a 1GB stick of DDR400 and just put the chip on that mobo and slap it in the dell case. Keeping the psu, hd, and optical drive. 

That my fellow Ubuntu-ites should do the trick...... I hope:)

Sorry to tell you this. But you're definitely not keeping the PSU if you want it to work. P2 and P3 dells have a proprietary power supply that is wired differently  from the standard ATX.  Quite aside from not having the extra +12v rail found on most p4 systems.

I think also that the case has the screw-holes in the wrong spots for mounting a standard ATX motherboard within. 

The service manual is here:

[http://support.dell.com/support/edocs/systems/opgx150/en/index.htm](http://support.dell.com/support/edocs/systems/opgx150/en/index.htm)


It's OK if you say AARGH now. :)

---

### Post by schagg on 2007-10-24
> **Paulmd said:**
> Sorry to tell you this. But you're definitely not keeping the PSU if you want it to work. P2 and P3 dells have a proprietary power supply that is wired differently  from the standard ATX.  Quite aside from not having the extra +12v rail found on most p4 systems.

I think also that the case has the screw-holes in the wrong spots for mounting a standard ATX motherboard within. 

The service manual is here:

[http://support.dell.com/support/edocs/systems/opgx150/en/index.htm](http://support.dell.com/support/edocs/systems/opgx150/en/index.htm)


It's OK if you say AARGH now. :)


well.. I do have a drill ;) I could mod the case if need be. we'll see. who knows maybe I'll get all crazy like and get a different psu too.

AARGH!!! how's that?:lolflag:

---

### Post by Paulmd on 2007-10-24
> **schagg said:**
> well.. I do have a drill ;) I could mod the case if need be. we'll see. who knows maybe I'll get all crazy like and get a different psu too.

AARGH!!! how's that?:lolflag:

I can't help you with case mods, you're on your own there. 


Getting a different psu than that dell one is NOT Optional if you want to run a non dell motherboard. Really. 

These are the pinouts of a standard ATX

[http://pinouts.ru/Power/atxpower_pinout.shtml](http://pinouts.ru/Power/atxpower_pinout.shtml)
[http://pinouts.ru/Power/atx12v_pinout.shtml](http://pinouts.ru/Power/atx12v_pinout.shtml)

These are the pinouts of your power supply

[http://pinouts.ru/Power/dell_atxpower_pinout.shtml](http://pinouts.ru/Power/dell_atxpower_pinout.shtml)
[http://pinouts.ru/Power/dell_atxaux_pinout.shtml](http://pinouts.ru/Power/dell_atxaux_pinout.shtml)


If you attempt to run a standard motherboard with that power supply, you will be putting +5v where +3.3v should go (pin 1), and worse putting +5 where ground should go (pin 3)

It will definitely not work, and may damage the motherboard and/or the power supply. If damage does not occur, it is only by God's grace and good engineering.



It is possible, in theory to rig a pin to pin adapter, but don't go there. Really.

You could do this easier, and better by getting a proper case and power supply.


Are you sure you want to spend all that time and money on this issue? After all compiz is just eye candy.  If you're having fun, and have the money, it's ok... but i don't want to lead you on a wild goose chase.

---

### Post by schagg on 2007-10-25
> **Paulmd said:**
> I can't help you with case mods, you're on your own there. 


Getting a different psu than that dell one is NOT Optional if you want to run a non dell motherboard. Really. 

These are the pinouts of a standard ATX

[http://pinouts.ru/Power/atxpower_pinout.shtml](http://pinouts.ru/Power/atxpower_pinout.shtml)
[http://pinouts.ru/Power/atx12v_pinout.shtml](http://pinouts.ru/Power/atx12v_pinout.shtml)

These are the pinouts of your power supply

[http://pinouts.ru/Power/dell_atxpower_pinout.shtml](http://pinouts.ru/Power/dell_atxpower_pinout.shtml)
[http://pinouts.ru/Power/dell_atxaux_pinout.shtml](http://pinouts.ru/Power/dell_atxaux_pinout.shtml)


If you attempt to run a standard motherboard with that power supply, you will be putting +5v where +3.3v should go (pin 1), and worse putting +5 where ground should go (pin 3)

It will definitely not work, and may damage the motherboard and/or the power supply. If damage does not occur, it is only by God's grace and good engineering.



It is possible, in theory to rig a pin to pin adapter, but don't go there. Really.

You could do this easier, and better by getting a proper case and power supply.


Are you sure you want to spend all that time and money on this issue? After all compiz is just eye candy.  If you're having fun, and have the money, it's ok... but i don't want to lead you on a wild goose chase.

You're right. I just liketo build things. I've done a bit of research, and it's not a ton of money, really. I mean, yeah it could be, but I don't need bleeding edge hardware. I have another machine for that. 

What I'm going to do first, is get comfortable with Gutsy, before I do anything really crazy.

---

