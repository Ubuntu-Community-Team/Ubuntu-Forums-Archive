---
title: "PnPBios, Graphics Card"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by drbob07 on 2007-04-07
OK, so, I thought my installer was hanging, but then I thought way back when, to when I installed Windows XP... I have 2 graphics cards

The onboard, and my GEForce FX 5200...

The installer seems to be accessing the On-Board, which will be problematic later, because, I don't use my On-Board.... 

It's just a black screen, unless I plug my monitor cable into the on-board slot.

So, is there a way I can force the installer to go to my GeForce FX 5200, and not my onboard graphics?


Secondly, I had to use the pnpbios=off flag to get it to boot properly. Is this going to be problematic after the install phase, or will this option become a permanent boot option?

Please help, I don't wanna be stuck with on-board graphics for the rest of my life ;)

**EDIT: Plugged into my onboard graphics card... the display is corrupted. Which is to figure, as my OnBoard graphics were starting to screw up, which is why I bought a card... So, installing graphically may not be an option if I can't put it on my GeForce *****

(Thanks in advance, and
my time on this computer is limited, so please reply quickly :(, please?)

---

### Post by chewearn on 2007-04-07
> **drbob07 said:**
> OK, so, I thought my installer was hanging, but then I thought way back when, to when I installed Windows XP... I have 2 graphics cards

The onboard, and my GEForce FX 5200...

The installer seems to be accessing the On-Board, which will be problematic later, because, I don't use my On-Board.... 

It's just a black screen, unless I plug my monitor cable into the on-board slot.

So, is there a way I can force the installer to go to my GeForce FX 5200, and not my onboard graphics?

There should be an option in the BIOS that set the graphics card priority (on board or external).  You can also look for a BIOS option that disable the onboard graphics.

> Secondly, I had to use the pnpbios=off flag to get it to boot properly. Is this going to be problematic after the install phase, or will this option become a permanent boot option?
From my limited knowledge back in the days of Win95, the pnp bios option is to autodetect ISA bus cards and such; unless you have an old system which still have ISA slots (and you are using an ISA card), it should be save to keep this  permanently off.

---

