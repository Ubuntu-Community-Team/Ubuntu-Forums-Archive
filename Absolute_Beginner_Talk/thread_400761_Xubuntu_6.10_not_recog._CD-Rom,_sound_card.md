---
title: "Xubuntu 6.10 not recog. CD-Rom, sound card"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Hugo Sleestak on 2007-04-03
A few days ago, you good folks helped me until I found a "flavor" of Ubuntu that would work on my aging PC. That would be Xubuntu 6.10. Now for the next leap - after installing Xubuntu on my 466mhz, 128mb, 4.3gb machine, the system isn't recognizing the built-in CD-Rom, the sound card, and who knows what else. I spent a couple of hours fishing through the system trying to see if I could find *something* to help the system recognize the various pieces of hardware. No luck whatsoever. 

So, I have no error messages. Nothing that lets me know that the computer "sees" anything amiss at all. There's just nothing. And I'm such a pathetic newbie that I don't know where to look, since there doesn't seem to be anything comparable to a "Control Panel" that would let me search for hardware, etc. I did find various controls that managed the desktop look and fonts used, but nothing pertaining to hardware details. Thunar file manager had a folder marked "CD-Rom," but it was empty.

Help would be much appreciated.

Thanks again.

= H

---

### Post by phr0z3n on 2007-04-03
Not sure about the cd-rom, but post specs on the sound card, please.

---

### Post by Hugo Sleestak on 2007-04-03
> **phr0z3n said:**
> Not sure about the cd-rom, but post specs on the sound card, please.

Here's a hardware breakdown, including the sound card details, if that helps:

CPU:  	Intel Celeron 466MHz (w/128KB L2 Cache) PPGA CPU
Operating System: Xubuntu 6.10
Memory: 	128MB SyncDRAM (expandable up to 256MB)
Hard Drive: 	4.3GB HDD (Ultra DMA EIDE)
Optical Drive: 	40x Max. CD-ROM Drive
Video: 	ATI Rage Pro Turbo 2X AGP with 4MB SGRAM
Audio: 	Crystal CS4280 3D PCI Audio
Ports/Other: 	2 USB Ports (1 is on Front), Audio In & Out / Game Port on Front, 1 Serial / 1 Parallel
Expansion Slots: 	3 Expansion Slots

Thanks again,

= H

---

### Post by phr0z3n on 2007-04-03
Just a quick post, install the ATI driver for your video card.EDIT: I thought you meant EVERYTHING LITTLE THING wasn't working, so ignore that, ANYWAYS, for your audio card, I would suggest just buying a dirt cheap audigy from creative, I have one and it plays well in Ubuntu, by the way, couldn't find anything in Google for it, sorry :-(

---

### Post by Hugo Sleestak on 2007-04-04
> **phr0z3n said:**
> Just a quick post, install the ATI driver for your video card.EDIT: I thought you meant EVERYTHING LITTLE THING wasn't working, so ignore that, ANYWAYS, for your audio card, I would suggest just buying a dirt cheap audigy from creative, I have one and it plays well in Ubuntu, by the way, couldn't find anything in Google for it, sorry :-(

Nope, didn't mean every little thing. Most of the time people make the mistake of giving too little information about their systems, so I just thought I'd give anyone interested a full snapshot of what mine looks like.

Misbehaving: just the CD-Rom, sound card ... haven't seen the floppy drive recognized (though I almost never use it anymore anyway - still, it would be nice if it worked). Haven't checked to see if the USB ports are working yet.

I found this page in the Ubuntu documentation that may help the sound card issue, and will have to check it out later:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

Thanks for the suggestion. 

= H

---

### Post by Hugo Sleestak on 2007-04-05
Thanks to the info contained in the URL above, I opened up a terminal window, typed in "aplayer -l," and the system listed the only sound card I have. Since it really was recognizing the hardware, then I knew that it had to be disabled or muted in some way in Xubuntu's controls. Getting into the sound controls, I simply had to switch the sound card setting from "default" to my specific sound card. Instant happiness.

The CD-Rom issue is a little more tricky. I still don't know why the internal CD-Rom isn't working. BUT I can hook up my external DVD and so at least I have access to material on disc AND I know for certain that my USB ports are functional.

Thanks everyone.

= H

---

