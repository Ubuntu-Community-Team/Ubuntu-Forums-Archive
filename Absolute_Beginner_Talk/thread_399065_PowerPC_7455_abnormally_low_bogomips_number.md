---
title: "PowerPC 7455 abnormally low bogomips number"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by miniteg on 2007-04-01
Hello,

I installed Ubuntu server (Edgy) on a PowerMac G4 quicksilver, 1GHz / 768MB RAM / Bus 133MHz.

At first I had trouble to get it to start if no screen was connected: things would just die very early on (couldn't even see anything in the logs). After tweaking the list of startup daemons, I got it to work. Point being, maybe I touched something sensitive here, but I'm not sure what.

I then installed a few other things like Gnome, PHP5, MySQL, and Coppermine. The machine is connected to the LAN but has no screen/mouse/keyboard.

Anyway, now it works okay, however I noticed that it takes a very long time to import pictures (when using batch process), much more than needed: about 30 seconds to create a thumbnail and a 800*600 image from a 3.5MB master (about 2300x3500 pixels) using Image Magik ("convert -antialias ..."). I'm sure it can do better! It's a 1GHz G4! Ethernet transfer is very fast, and so is hard drive transfer, but the CPU seems to lag...

And then I noticed that the bogomips number is abnormally low:

[FONT="Courier New"]miniteg@ubuntu:/proc$ more cpuinfo 
processor       : 0
cpu             : 7455, altivec supported
clock           : 999.999997MHz
revision        : 0.3 (pvr 8001 0303)
bogomips        : 66.56
timebase        : 33304558
platform        : PowerMac
machine         : PowerMac3,6
motherboard     : PowerMac3,6 MacRISC3 Power Macintosh
detected as     : 129 (PowerMac G4 Windtunnel)
pmac flags      : 00000010
L2 cache        : 256K unified
pmac-generation : NewWorld[/FONT]

I'm pretty sure that even if the bogomips are bogus (I know how this works), it should still return a bigger number.

So I recompiled a vanilla kernel just for the sake of it, but am getting the exact same performance (note: recompiled with the altivec flag on, to be sure).

So here is the question: how can I make sure that I'm *really* using the most out of this computer?

Thanks,

Teg-

---

### Post by Gen2ly on 2007-04-02
uh, r u sure you're in the right area?

---

### Post by miniteg on 2007-04-02
I moved this over to the PPC area.

Teg-

---

