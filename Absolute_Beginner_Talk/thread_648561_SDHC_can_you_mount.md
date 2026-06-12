---
title: "SDHC can you mount??"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by salida on 2007-12-23
Hey all, i have an internet tablet n800 and just bought an SDHC 4Gb card...
i am having problem mounting the card to ubuntu ...
is something wrong with SDHC cards???

---

### Post by blueridgedog on 2007-12-23
Take a look at System -> Preferences -> Removable Drives and Media

Is you system set to mount them automatically?

When you say you are having problems, can you be more specific?

---

### Post by salida on 2007-12-24
Yes my system is set to auto mount removable drives.
i have no problem with smaller SD cards i have a 2Gb that works fine.


When i plug in my SDHC 4Gb card nothing happens it seems that the computer does not recognize it.

---

### Post by salida on 2007-12-24
i did a little further search in the internet.

is there a possibility to have a card reader that can not read SDCH ?
some people say that they have SDHC card reader enabled ?

---

### Post by blueridgedog on 2007-12-24
Yes, that is possible (an older reader).  Does the "I have a card in me and I am happy" light come on when the card is inserted?

---

### Post by salida on 2007-12-24
it seems that i have to throw away my card reader, it sucks....
yes the light goes on...
my card reader is 2 years old
i didn't knew i need a SDHC card reader
thank you anyway

---

### Post by Neobuntu on 2008-01-21
Same type prob here.

New Adata 4GB Class 6 MicroSDHC.

My Alcore reader is supposed to read it according to a data chart I found on the Internet. "Pass" on 4GB SDHC it said.

Be advised: Perhaps it's not the reader.?.?

testing....

---

### Post by Neobuntu on 2008-01-24
I have now found new information stating that my EXACT Alcor Micro USB reader (6331) is slow and definitely not SDHC compatible after all. I doubt the reader is firmware upgradeable to SDHC.

I would guess that any (Micro)SD**HC** reader should work with (Micro)SD**HC** cards and as you would know, one does HAVE to use a (Micro)SD**HC** reader with (Micro)SD**HC** cards. 

A (Micro)SD**HC** reader is reported to also manage plain old (Micro)SD. Not the other way around.

I am awaiting the arrival of my new USB (2.0) MicroSDHC(2.0) reader.

---

### Post by a9bejo on 2008-01-24
> **salida said:**
> Hey all, i have an internet tablet n800 and just bought an SDHC 4Gb card...
i am having problem mounting the card to ubuntu ...


I'm in the same situation (n800, SDHC card, old card reader).  I just keep the SD card in the n800 and when I want to transfer files, I simply plug the n800 to the computer via USB. The memory card is then recognized  as a external drive.

You can also use ssh to transfer files over wlan.

---

### Post by Drunkinmastaray on 2008-01-27
I had the same problem.  As a matter of fact I had left my SDHC card connected to my computer and to my surprise it locked up my entire system.  In the end I had to switch out  my old card reader to my new SDHC card reader, which came with my 6G MicroSD card. Since I have made the switch, I have had no problems.

---

### Post by Neobuntu on 2008-01-28
There is some confusing and counter information that a now available Windows XP Hot fix would allow an SD reader (some??) to read HC after all. It did **not** work for me.

I applied the HC fix and it hangs. I also applied the <4GB HC MS fix and it hangs. It only works with MicroSD card not my (A-Data 4GB Class 6) MicroSDHC (Micro reader).

I'm waiting for my new MicroSDHC reader this week. Only then I can see if it is the (HC) card or the (likely) reader. 

So that's the Windows (XP updated) scoop. I keep that XP to test. Hopefully this knowledge might help us with Kubuntu somehow.

What's the deal with SDHC and Kubuntu. I suppose the proper reader works?

Has anyone made a (select unit maybe) SD reader work with HC; in some way? 

So if we absolutely **have** to have a SDHC reader, then what's that MS hot fix all about?

I am left to guess, it depends on the model of reader. My Alcor (chipset) MicroSD reader doesn't work but I read there's a Alcor SD reader that can do HC. 

Ugg! Confusing. help please. Info needed.

---

### Post by Neobuntu on 2008-02-06
One needs a (micro)SD**HC** **rated** reader for a (micro)SDHC card. It will not even recognize otherwise. They are made not to. That is in the SD 2.0 spec (along with "Class" ratings).

Even among SDHC USB reader/writers, some do not operate at the faster (class 4 and 6) speeds. 

One HC reader I have hangs and kicks out the mount.

Another new HC one **only** works on Kubuntu and not XP. Go figure.

I highly recommend checking the speed (writes) for a flash and buying it with an also high speed rated reader. Not every combo includes a quality reader.

This is an industry shame. SDHC was not supposed to replace the SD standard but once you get into HC >=4GB territory, you don't want a class 2 slow poke. Thus you must have an HC reader and not just any one will do (fast or without hanging Windows).

I spent a lot of time figuring this out. Please use this info wisely.

P.S. DO NOT USE "fatsort" for Linux, is corrupts drives! Not only if they are "inconsistent".

---

### Post by richiesgr on 2008-02-28
I think that the thread was about problem mounting SDHC card on ubuntu and not wich card reader is best for read card.

Anyway I've a sandisk card 4GB including a original sandisk sdhc reader. I've tries to connect by USB cable the telephone or the card reader both can't be mounted !!!.

Is tehre anybody know how can I mount a SDHC card on ubuntu ??

Thanks

---

### Post by Neobuntu on 2008-03-17
I tried a new SDHC reader and it worked. If all else fails try another appropriate reader.

Several things must be checked before assuming you have a bad or failing (unreliable) memory card. 

1. HC cards require GOOD HC readers. Perhaps, try Two. If you are getting a new "reader", get a SDHC (or MicroSDHC). They read/write both HC and standard SD cards.

2. Panasonic states a format not done in camera, may be corruptible. They state that a computer format is not up to SD specs. Why? ...They don't specify. 

**Edit: Do not use a formatter that erases the position of a Flash [B]partition** that may start; after a bit of space. That space is for Flash drive alignment. If you change it, your Flash will not be stable and there is no easy fix. Windows may do FAT32 wrongly, may make a unmatched partition type (like sdb rather than sdb1) and is still working on their SDHC compatibility.. Beware of some tools when repartition when formating, Many hard drive utilities will trash your flash drive. Do not defrag Flash.

Many have good results only formating in a camera. I guess that depends on the camera. There are reports of not reading the end of partition correctly and losing the last saved "file"  which could be a big movie. I would test your SD to full; before trusting it. Video fills them up fast.

While Sandisk gets high prise, I do not think the brand matters. The speed might. Size too. :)[/B]

3. Try a different USB 2.0 port (different computer). Some USB controllers are reported to be problematic.

4. Was the system turned off during a write? Perhaps it needs maintenance or (in-device) reformatting. Maybe you could take your card by the local camera (For sale) display and reformat to the new SDHC spec in it.

5. Do not defrag Flash drive memory cards. It could trash your drive. Reformat instead. beware other low level (spinning) hard drive utilities. They are not for Flash cards.

6. Always buy from reputable source that do not charge for exchanges or refunds. Shop long; shop hard. You can still get a low price.

7. There are fake clone copies of memory cards out there. Be careful.

Is the card's WRITE speed fast enough for what your device writes? I've seen some tests that suggest a big 6 or 8GB (SD 2.0 spec, SDHC, FAT32 by necessity) Flash cards with the class 6 (Class 4 may be fast enough for you) are as fast or faster than any non "class" fast claimed card. But some of those 2GB and less card are not slow pokes, non the less. The point is, FAT32 and it overhead does not seem to be an issue **on computer**. Still it might be, on your device. So a max 4GB SDHC formated VFAT16 may be fastest for those devices. Then, as I said, a speed bottleneck, may be in the device (but most likely not).

If you buy anything. Make sure it is SDHC. The device and the USB adapters/readers. They still use old SD but not the other way around. if you don't need anything bigger than a 2GB SD then that's fine (if it's a fast one) being not "HC". Save a few bucks and it works on legacy devices/readers. Yet if your devices and readers are SDHC, you can do either. personally with 8GB SDHC hovering under $30 shipped, it's worth it to go all SDHC.

---

