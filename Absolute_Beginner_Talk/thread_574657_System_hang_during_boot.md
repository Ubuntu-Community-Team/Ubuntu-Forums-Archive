---
title: "System hang during boot"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by bevy_of on 2007-10-13
Hi all,

Today I am trying to install ubuntu v7.04 (FF) to dual boot with xp, with each OS having its own HDD.  I am using the AMD64 alternate disk.  I'm trying the method where you install ubuntu then modify grub and add xp drive in after that.  Both drives are SATA.  Only one is hooked up at the moment so for all intents and purposes this is just a simple one OS on one HDD right?

I have an ATI X800XT card and have ready the sticky posts and others about the problems with these cards.  I can boot into recovery mode and I got a chance to update the distro and put in those ati drivers mentioned in mike's sticky thread, that should work.  That all seemed to work fine.

**The problem:**

My system just hangs during boot, the screen goes black.  My monitor then goes into idle state presumably because it is getting no signal.

**The Specs**

Athlon64 3500+
Gigabyte K8NS-939 Ultra mobo
1GB Corsair XMS3200XL (2x512 dual channel)
ATI X800XT VGA card (feeding Samsung 205BW 1680x1050)
120GB WD caviar SATA
Audigy 2

Any help would be greatly appreciated.  If there are any obvious threads about this please smack me on the head and point me to them.

Thanks in advance,
Willis

---

### Post by shearn89 on 2007-10-13
have you tried booting with "noacpi" at grub? hit esc, then modify the command line. I've found that to solve lots of probs, although it may not help...

---

### Post by bevy_of on 2007-10-13
ok, sounds promising. i will try it and let you know the result.  i'm just heading upo to the pub for a guiness and need to do some minor toolwork with the HDDs to try, so will be about an hour.

_thankyou very much._

---

### Post by bevy_of on 2007-10-13
hey, do you mean hit esc to bring up grub, then edit, the open a new line and then on that new line simply type "noacpi" (without punctuation of course)?

if that is all then no luck i am afraid.

---

