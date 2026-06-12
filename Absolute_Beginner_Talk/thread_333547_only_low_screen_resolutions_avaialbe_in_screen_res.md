---
title: "only low screen resolutions avaialbe in screen resolution preferences"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by mistafeesh on 2007-01-07
Hi,

I've just got Ubuntu up and running on my old Dell laptop (huzzah!) With a bit of help from this forum, but now I seem to be stuck at 800X600 resolution.I know my computer can do 1024X768 though...

 I did the "sudo dpkg-reconfigure xserver-xorg" bit, which is how I can even see anything at all, and I tried to follow the instructions [here](http://ubuntuforums.org/showthread.php?p=454217) to add 1024x768, but I got a bit confused, to be honest. It's got that resolution listed as available (I think) in that file, but it's not there in the menu......

I'm probably being daft. I mostly use Mac OSX, so I'm fairly familiar with the terminal, but mostly for fiddling with a webserver...

and idea whayt I need to do?


Ta

Dan

---

### Post by houstonbofh on 2007-01-07
Need more info...  What Dell laptop?  More importantly, what graphics card?  What have you tried so far?  Can you post your xorg.conf?

---

### Post by mistafeesh on 2007-01-07
Hi,

thanks for the quick reply...

It's a Dell latitude Cpi D300XT. It's got a 300mhz P2, 128 meg ram, and according to the specs **[here]("http://support.dell.com/support/edocs/systems/pmojav/specs.htm")** it's got a NeoMagic 2160 gfx card.

posting the xorg.conf is a bit tricky. I haven't got a network card for it yet - I'm posting this from my mac.... Is there a particular bit that's pertinent? I could type it out...

---

### Post by mistafeesh on 2007-01-07
ahah! I got it on a hunch.... I changed the colour depth from 24 to 16, and that made 1024x768 available! thanks!!



Dan

---

### Post by brain_freeze on 2007-01-08
Gah, nevermind!

---

### Post by houstonbofh on 2007-01-08
I will put it here for the ages.  A lot of older graphics cards are quite short on memory, and will not do high resolution in high color.  One machine I have needs 8 bit to do 800x600!

---

