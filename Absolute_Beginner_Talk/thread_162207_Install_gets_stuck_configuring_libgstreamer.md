---
title: "Install gets stuck configuring libgstreamer"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by bacon_sandwich on 2006-04-18
Any ideas on why the installation freezes when it tries to configure libgstreamer0.8???

My install CD is good (checksums ok), I did a memcheck (found a bad stick of RAM, failed everything). It finally goes through the install, but then when it spits out the cd and reboots and starts installing all the packages, it ALWAYS freezes when it gets to 64% and says "configuring libgstreamer0.8"

I have a soyo kt600 plus. Somebody told me that linux doesn't like the VIA chipset with the network card built-in and to try using a PCI network card. I'm trying that tonight. It also has a sound card built in. I have a soundblaster card that I can also put in, but I thought that might confuse things. 

Also, I was told to reformat the hard drive. Erase all partitions and start from scratch. I'll try that tonight, too.

Any other suggestions? 

Out of frustration I checked out Debian and I installed that from the net-install. Debian installed just fine, I'm just having a hard time getting my nvidia graphics card drivers installed. Stuck at 800x600 resolution. 

I was told Ubuntu is much better than Debian, especially for a linux newbie like me. 


Help!!!

---

### Post by anthonyn on 2006-04-24
Sorry I don't have the answer but I do have exactly the same problem as you describe.

The only insights are that the checksums for the files do not appear to fit:

./pool/main/g/gst-plugins0.8/libgstreamer-gconf0.8-0_0.8.11-0ubuntu5_i386.deb
supposed to be: c3d214abea8896f7245c1c9377fec120
is:		3cf390a55a6f0863585a8048c5a0d09f

./pool/main/g/gst-plugins0.8/libgstreamer-plugins0.8-0_0.8.11-0ubuntu5_i386.deb
supposed to be: d0442cc31070fe2ab03b1fef916bde6f
is:		c3d214abea8896f7245c1c9377fec120


./pool/main/g/gstreamer0.8/libgstreamer0.8-0_0.8.11-1ubuntu1_i386.deb
supposed to be: 9afd224a4337af2aa2f296c99b318c3f
is:		a7f4f31019d53b6b1329f12edecf0245

AND I then I fiddled with the aptitude package manager and loaded the packages in the task for the desktop.
It all ran fine until:

Setting up libstreamer0.8-0 (0.8.11-1ubuntu1) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
Fontconfig error: Cannot load default config file

I presume this is what is happening when we try to install from a CD automatically.

CAN ANYONE OUT THERE EXPLAIN WHAT TO DO? IS THE RELEASE BUGGED or CORRUPT?

---

### Post by anthonyn on 2006-04-26
Got advice via a bug report to try the Dapper beta release available from the developers page of [www.ubuntu.com](www.ubuntu.com). Loaded fine and appears to work.

---

