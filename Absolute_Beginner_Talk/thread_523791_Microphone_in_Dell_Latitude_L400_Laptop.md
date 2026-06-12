---
title: "Microphone in Dell Latitude L400 Laptop?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-08-12
Just noticed my [Dell Latitude L400](http://www.mbhoy.com/21-07-2007/dell-latitude-l400-laptop) has a built in microphone. 

No sign of it working though, never had Windows on here so don't know if it's Ubuntu specific or just a hardware fault. Would kinda like to see it working, no huge deal though.

Any ideas? Where do I start?

---

### Post by MenZa on 2007-08-12
You could start by running lspci or sudo lshw, which will list any hardware devices you have. Just a guess, though.

---

### Post by Old Pink on 2007-08-12
> 00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)>         *-multimedia
             description: Multimedia audio controller
             product: Crystal CS4281 PCI Audio
             vendor: Cirrus Logic
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=CS4281 latency=64 maxlatency=24 mingnt=4
             resources: iomemory:fedef000-fedeffff iomemory:fedf0000-fedfffff irPretty much the extent of it's multimedia/audio findings.

---

### Post by designwiz on 2007-08-12
i have got the same problem on a dell xps m1210. works perfectly fine in vista
searched alot and finally landed on the conclusion that microphone is not detected
try this out

right on sound icon--> open prefereneces--> search for Mic 
also from terminal 
run 
alsamixer
and increase the bar for capture/mux

but for me i cant see the mic option!

try it out i may work for u
regards

---

### Post by Old Pink on 2007-08-12
There is a Mic1 and Mic2 option, and a capture option. I've played music from my phone beside the microphone, and messed with all the settings whilst recording, yet no sound plays back to me, even with all full, alternating between Mic1 and Mic2. Interesting.

---

### Post by Old Pink on 2007-08-12
Mic Capture Option found, ticked, nothing.

---

### Post by designwiz on 2007-08-12
hmmm... did  u try alsamixer

---

### Post by ugm6hr on 2007-08-12
As a starting point - I always recommend posting the output from:
```
amixer
```

Then post a screenshot from:
```
alsamixer
```

This may give us enough info to get it working.  Of course, that depends on the sound card already working!

---

