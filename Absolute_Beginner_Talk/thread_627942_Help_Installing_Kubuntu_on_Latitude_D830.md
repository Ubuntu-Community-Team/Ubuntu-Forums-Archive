---
title: "Help Installing Kubuntu on Latitude D830"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-11-30
Dear all

I have just received my new latitude d830, sweet laptop
The problem is that when I try to start it from the kubuntu gutsy amd64 livecd the screen goes black and I can't see anything anymore.
I think this is due to the nvidia card. Is there a way I can get the live cd to work? I need to resize the windows partition so that I can install kubuntu in it

Cippa

---

### Post by Cippa Lippa on 2007-11-30
i found out that I can load the x386 kubuntu gutsy but not the amd64. Why that?

Cippa

---

### Post by Sef on 2007-11-30
> i found out that I can load the x386 kubuntu gutsy but not the amd64. Why that?

Dell uses Intel CPUs and motherboards.   Though now some dells are being made with AMD.

---

### Post by Cippa Lippa on 2007-11-30
wow... I thought amd64 installlations were for every dual core processor...

---

### Post by ndtfl on 2008-02-04
I think you can install either Ubuntu or Kubuntu 64 bit.  I tried Kubuntu amd64, and my screen went blank as well, but then when I tried safe mode (the second option), then I was able to get in and install, everything seems to work fine so far except now I m having problem w/ my intel wireless, it's just giving me 10k or less so I had to use my wired connection.  Just remember when you use livecd, make sure you are wired connected, otherwise it will take ages for the installation to finish when it is trying to scan the security update.

Anyway, hope this helps

---

### Post by ajeannotte on 2008-02-04
i've heard that the 64-bit installations are for experienced users only. that it takes some doing to get them stable with all the software you want. 

use the regular (32-bit) versions if you're new as all 64-bit regular intel and AMD chips are compatable with 32-bit architecture. plus, there's far more support for the regular version than the 64-bit ones. 

i use the 32-bit i386 versions of all the distros i use even though i'm running 64-bit AMD dual-cores on both my commputers and i've had minimal issues.

---

### Post by vihai on 2008-02-06
To me it seems like the splash screen is turning off the LCD's backlight and the X server is not turning it on again.

As a workaround I found that disabling the splash screen (by removing "splash" from the kernel's parameters line) made both the installation and normal boot work.

---

### Post by Golem XIV on 2008-02-06
> **Cippa Lippa said:**
> wow... I thought amd64 installlations were for every dual core processor...

Nope.  64-bit installations are for 64-bit processors, regardless of the number of real/virtual cores.  Also, despite being "amd64" they work perfectly with Intel 64-bit systems.

Don't confuse dual core with 64-bit architecture. 2x32 bits in this case != 64 bits :-)

---

### Post by Golem XIV on 2008-02-06
> **ajeannotte said:**
> i've heard that the 64-bit installations are for experienced users only. that it takes some doing to get them stable with all the software you want. 

use the regular (32-bit) versions if you're new as all 64-bit regular intel and AMD chips are compatable with 32-bit architecture. plus, there's far more support for the regular version than the 64-bit ones. 

i use the 32-bit i386 versions of all the distros i use even though i'm running 64-bit AMD dual-cores on both my commputers and i've had minimal issues.

Not really true.  There are a few programs and some drivers that are not available in 64-bit "format" (is "architecture" the right word?), so for those you either have to compile them from source or use some tricks to get them to work.

I have been using a 64-bit installation on an HP laptop for a while now and I had less problems with it than with a 32-bit Dell Vostro.

---

