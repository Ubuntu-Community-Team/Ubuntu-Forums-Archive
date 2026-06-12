---
title: "ati install"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by yazuki101 on 2008-01-30
hey, I am trying to install gutsy gibbon on a machine with no other OS. it has these specs:

-Intel Pentium II -400mhz
-512MB PC133 RAM
-6.5GB Fujitsu HDD
-128MB Rage 3D ATI GPU
-Creative soundcard

I cannot load into gutsy using the alternate cd. I get through the load screen, but after that the monitor flickers and then goes blank.

I was wondering how to get the ATI drivers using the recovery.

---

### Post by Cute Poison on 2008-01-30
sounds like the video card is  one of the few that utterly refuse to work under ubuntu. I have a simular problem with my narly 7600 nvidia 
However... 
if you can get you X server up, find and run ENVY. or AUTOMATIX, both these programes automaticly build, compile new drivers for you video card. 
try that. Hope it works 


(for reference for these programs search thru this forum.. there is BOUND to be a link someplace)

---

### Post by mikeyphi on 2008-01-30
> **yazuki101 said:**
> hey, I am trying to install gutsy gibbon on a machine with no other OS. it has these specs:

-Intel Pentium II -400mhz
-512MB PC133 RAM
-6.5GB Fujitsu HDD
-128MB Rage 3D ATI GPU
-Creative soundcard

I cannot load into gutsy using the alternate cd. I get through the load screen, but after that the monitor flickers and then goes blank.

I was wondering how to get the ATI drivers using the recovery.

Try this advice: 

Blank screen with some ATI hardware

      People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. Bug #132716

---

### Post by yazuki101 on 2008-01-30
would using my on board video card instead of the rage card do anything?

---

### Post by mikeyphi on 2008-01-30
> **yazuki101 said:**
> would using my on board video card instead of the rage card do anything?

Depends!!  What is the on-board card?

---

### Post by yazuki101 on 2008-01-31
none, actually. I thought it did. I have since upgraded to a P3 733MHz board, maybe it will help.

---

### Post by yazuki101 on 2008-01-31
none, actually. I thought it did. I have since upgraded to a P3 733MHz board, maybe it will help.

---

