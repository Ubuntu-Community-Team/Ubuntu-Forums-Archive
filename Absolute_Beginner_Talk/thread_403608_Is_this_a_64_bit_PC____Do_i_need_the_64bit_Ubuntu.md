---
title: "Is this a 64 bit PC ?   Do i need the 64bit Ubuntu ?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Maxwell7 on 2007-04-07
Hi everyone, 

I've been trying to install Ubuntu on this system for a while now, and nothing *ever* works. I mean, the life cd's do start up..... for about 20 seconds, after which they hang. The same thing happens with Knoppix, .... 

Maybe I have to use the 64 bit version of Ubuntu ? So if anyone could confirm whether this system is indeed a 64 bit ? 


So here are the specs of the PC :

*Medion 8800
intel Pentium D dual core processor 830
3.0 GHz, 2x1 MB L2 cache, 800MHz FSB
(they mention 64 bit support ? like this :  this pc is "prepared for the future by 64 bits support".) 
is this actual 64bit cpu, or just a compatibility thing ????

*1GB RAM DDR2 533MHz
64 bits dual channel
*250GB HD
S-ATA 150-interface
*NVIDIA GeForce 6700XL

thanks a lot

---

### Post by xopher on 2007-04-07
You can use 32-bit OS's on your 64-bit processor. So that's not your issue. 32-bit OS's are still better all-rounders, and that's what you should use.

Have you tried installing with the alternate-install-cd? It will install Ubuntu directly on your computer, no LiveCD-fuzz.

Have you tried Feisty? The newer the distribution is, the better the change is for it to work correctly.

Have you searched the forums or google for other users having problems with a similar setup?

---

### Post by Hieronymus on 2007-04-07
First of all your system will be able to support a 64-bit OS, you can find this information [here,]("http://www.intel.com/products/processor/pentium_d/prodbrief800.pdf") on the bottom of page 3. Normally any 64-bit processor will also support 32-bit OS so this should not be the problem. You can change to Feisty but since the system is already quite old that should not make a difference. What you could try is run the installation in safe mode, see if that works. If that does work than you might have an issue with one or more of the standard loaded drivers. 

Jeroen

PS. Everywhere I go on the net it still is unclear whether you processor is purely 64 or 32 bits. Since it is so misty I whould say it is not purely 64-bit.

---

### Post by Maxwell7 on 2007-04-07
OK, bedankt Jeroen,  and xopher

I'll try the safe mode thingy again and inform you on the progress. 


ps : thanks for pointing out that you can run 32bit OS on 64 bit cpu ;-)


***update* :**
Hurray !!  I've been able to boot the live cd in safe mode. Yes ! :D :D

(ok, it still doesn't work with edgy, but as long as i already have dapper, i should be ok. Maybe i could do a direct update via the repo's ? )

---

