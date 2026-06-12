---
title: "Moving from XP to Ubuntu"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Rxq on 2007-07-29
I have a XP in NTFS hard drive formate.

I created an new partition and installed Ubuntu on it.

However, since Ubuntu is in EXT3 format. is there anyway to access my files in NTFS from is?

Basically I'm switching to Ubuntu because my CPU is 64bit but my copy of windows is for 32 bits.
I hope to get faster speeds.
I also here Ubuntu uses up less resources and is more stable.
So how can I configure it for speed?
I plan to use Linux for Web Browsing, media, word processing, etc and use windows for Gaming.

Is there anything I need to do with my fresh copy of Linux like install drivers?

Any good tutorials? (Short reads please)

---

### Post by misfitpierce on 2007-07-29
True it does use less resources etc. and you can try [http://getautomatix.com](http://getautomatix.com) it has a NTFS read/write thing which I believe allows you to grab stuff from a NTFS partition.

---

### Post by mikewhatever on 2007-07-29
To access your ntfs partition, install ntfs-config package. Here is how to install software guide [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Ubuntu should be at least as fast as Windows or faster, but do not expect great speeds if you have, say 256 MB of RAM. If you have nvidia or ati card, the driver can be enabled in the Restricted Drivers menu. The rest should be working best out of the box if the hardware is supported.
Good Luck!

---

### Post by zerobinary on 2007-07-29
and get crossover linux a app u have to pay cough cough not in isohunt 
a good app 
cough cough u did not hear this from me

---

### Post by CptPicard on 2007-08-17
I know this response comes very late, but I just have to chime in regarding your motivations about speed, and what you're using your computer for... the "bitness" of your OS in relation to your CPU has nothing to do with speed, really, unless you're doing, say, scientific computing, where you are doing extreme number crunching and absolutely NEED the 64bit register in one piece instead of doing two memory fetches to fill 2x32 bits, OR if you're doing something extremely data-intensive, where you need to be able to address humongous amounts of memory (over 4 gigs).

When you're surfing or word processing, your CPU is already idle the vast majority of time. Switching to a 64bit OS makes no difference whatsoever in these applications. I am sure you will find out, rather, that Linux is still less responsive on the desktop than Windows...

Don't fall for the advertising hype. :)

---

### Post by mikewhatever on 2007-08-18
I kind of agree with what you are saying about 32 vs 64 bits speed difference. However, in my case, Ubuntu is at least as responsive as XP. It definitely uses less swap, and hard disk. I think, generally, if the hardware is supported, the advertisements are not far short of truth.

---

