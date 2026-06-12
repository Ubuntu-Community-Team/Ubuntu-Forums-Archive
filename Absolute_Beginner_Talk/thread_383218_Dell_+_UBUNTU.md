---
title: "Dell + UBUNTU"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by suntin on 2007-03-13
I started running Ubuntu on my laptop at work, an AMD 1ghz that was dying. Worked fine and was faster and more comfortable than XP.

This week my new Dell Dimension arrived, Athlon 3800+ with 2gb ram, so in theory it should beat the laptop?

So I set up Ubuntu immediately to avoid any further exposure to Vista and...

All the software says it was not designed for the i386, scroll rates are appalling and downloading patches and software seems to take forever, often bugging out saying that the files couldn't be found. sadly right now Vista performs much better.

Now I know this isn't right. 

I am using the 32 bit OS on the 64 bit processor, is that where I went wrong? 
I assumed it would be ok as:
Dell only supply the 32 bit vista,
I went to redownload Ubuntu and the website's top page reads like you get one download and it detects what parts to install

I don't think that's the case because attempts to install the 64 bit Nvidia drivers said it was 32 bit but even so 32 bit OS should run on 64 bit processors? I don't know...

Being a work PC I can't spend ages trawling the web for answers and I can't do it at home because the installer (Live CD) hangs with a blank screen.

Can anyone save me from having to use that shoddy piece of !#$ that Dell are forcing down their customers' throats.

---

### Post by kinson on 2007-03-13
> **suntin said:**
> I started running Ubuntu on my laptop at work, an AMD 1ghz that was dying. Worked fine and was faster and more comfortable than XP.

This week my new Dell Dimension arrived, Athlon 3800+ with 2gb ram, so in theory it should beat the laptop?

So I set up Ubuntu immediately to avoid any further exposure to Vista and...

All the software says it was not designed for the i386, scroll rates are appalling and downloading patches and software seems to take forever, often bugging out saying that the files couldn't be found. sadly right now Vista performs much better.

Now I know this isn't right. 

I am using the 32 bit OS on the 64 bit processor, is that where I went wrong? 
I assumed it would be ok as:
Dell only supply the 32 bit vista,
I went to redownload Ubuntu and the website's top page reads like you get one download and it detects what parts to install

I don't think that's the case because attempts to install the 64 bit Nvidia drivers said it was 32 bit but even so 32 bit OS should run on 64 bit processors? I don't know...

Being a work PC I can't spend ages trawling the web for answers and I can't do it at home because the installer (Live CD) hangs with a blank screen.

Can anyone save me from having to use that shoddy piece of !#$ that Dell are forcing down their customers' throats.

Regarding to your appalling scroll rates, its probably because you haven't installed your video drivers, or didn't install it properly.

There shouldn't be any problems installing the i386 version of Ubuntu on top of a 64bit hardware. Its strange that it says that the software isn't designed for i386 though...cause its normally the AMD64 version having the problems, because most of the stuff is designed for the i386 version.

Cheers,
Kinson

---

### Post by suntin on 2007-03-13
What with their obvious deal with M$ (and the number of Dell issues on this forum) I'm beginning to suspect Dell have done something underhanded.

Unless Ubu is detecting the 64 bit processor even with a 32 bit install.

I'm so not going to stick with that insult of an OS Vista so I guess I'll be doing a few late nights to troubleshoot after work.

---

### Post by 3rdalbum on 2007-03-13
32-bit Ubuntu works completely seamlessly on 64-bit; or it should do :-)

Instead of using the Add/Remove Applications program, try using the Synaptic Package Manager. Indeed, I have no idea why you're getting the error about the wrong architecture, unless there are 64-bit-only or PPC-only repositories that you've added?

Loading the correct Nvidia (32-bit) drivers will definately make graphical things like the scrolling much better.

---

### Post by suntin on 2007-03-13
OK, it totally shouldn't work like this I'm sure but I followed your advice and searched for a few of the apps in Synaptic, then needed to consult the Add/Remove to remind myself what else I needed and all of a sudden it isn't complaining.

GFX card and whatever the equivalent of IME is left to go and I never need to look at that suck fest Vista again. (well hopefully)

---

### Post by tgalati4 on 2007-03-14
Sometimes it takes a while for the kernel to get comfortable with your hardware.  I have experienced this as well.  Sometimes multiple boots causes the hardware detection algorithm to take different paths (checking existing /var/log messages for instance?)  Hardware detection is like cancer treatment--pretty crude.  Load a driver and see if the system takes a dump.  No, then load the next driver.

Eventually you get through all of the hardware detection and you get a running kernel.  Sometimes it's magic.

Share with us interesting tidbits from dmesg.

---

### Post by charles.g.moore on 2007-03-14
I run a 32-bit sys on a 64-bit architecture with no probs. so it is fine.
Keep trying and good luck.

HP dv6000t
1.8GHZ core2duo
256 Nvidia

---

