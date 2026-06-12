---
title: "wine config problems"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Les Wilde on 2008-03-11
When I run the winecfg command, (after installing wine) either from the menu or by a command in Terminal after a few seconds the whole PC freezes and has to be rebooted to continue.
I am running the latest Ububntu version with a reasonable spec PC. I have fully renistalled Ubuntu and also removed and reinstalled wine several times. Having searched  forums the only mention of a similar problem is quoted below. I am new to linux and wine but fairly knowlegable on PCs.
Any ideas?

Quote
'Running winecfg seems to hang or complain about files when I click the audio tab
The hang is caused by the "NAS" sound driver. This causes it to pause for a while but it should respond eventually. The only way to get around this is to remove NAS from your system and/or build Wine without NAS support in the first place. If you see messages about JACK in the terminal they can be ignored unless you intend to use the JACK driver. If you wish to use the JACK driver then you need to install JACK's libraries onto your machine before JACK will work.'

---

### Post by Arkenzor on 2008-03-11
> **Les Wilde said:**
> 
'Running winecfg seems to hang or complain about files when I click the audio tab
The hang is caused by the "NAS" sound driver. This causes it to pause for a while but it should respond eventually. The only way to get around this is to remove NAS from your system and/or build Wine without NAS support in the first place. If you see messages about JACK in the terminal they can be ignored unless you intend to use the JACK driver. If you wish to use the JACK driver then you need to install JACK's libraries onto your machine before JACK will work.'

This probably isn't the problem here, because this hang only lasts a short time and I've never heard of it crashing anything.

If you really reinstalled your whole Ubuntu (not saving and restoring your home folder) then its probably - and unfortunately - a hardware problem. I can't really imagine any hardware failing by merely calling winecfg though (well, I've heard of wine performing very badly on Ubuntu 64 bit, but never anything that bad). It would certainly be worth doing an extensive search on [winehq.org](http://www.winehq.org).

If you _did_ restore your home folder from your previous installation however, then the first thing to do is to completely delete the .wine folder inside it:
```
rm -r ~/.wine
```
This will reset all of your wine configuration and destroy all the data on wine's internal "C:\ drive" 
(if you want to keep it then make a backup of your "<home folder>/.wine/drive_c" folder before removing it).

---

### Post by Les Wilde on 2008-03-19
Thanks for the reply
It seemed like it was going to be a hardware fault, and it was!!
I tried the same hard drive in another machine and after reinstalling Ubuntu and the installing wine the config command worked as it should with no lockups.
I will try the original machine again when I get the time changing video and sound cards to see where exactly the fault was.
At least I have an answer
Thanks again

---

