---
title: "powerbook g4 1ghz (titanium, tibook IV, dvi) temperature issues"
date: 2006-11-25
forum: Apple PPC Users
---

### Post by donlaverty on 2006-11-25
Hey Folks,

I'm running Xubuntu 6.10 on my 1Ghz PowerBook G4 (the last Titanium Model, also called TiBook IV or TiBook DVI as far as i know).
I'm trying to run it as silent as possible for quite a while now, but unfortunately information on my particular model seems to be quite rare (or i'm just too stupid to find it - this case is more likely). It runs quite cool already, but after the fan kicks in it does not shut down anymore. So i concluded that trying to save some more power should do the trick.

The information from the 'Powerbook/iBook thermal issues'-thread ([http://www.ubuntuforums.org/archive/index.php/t-12388.html](http://www.ubuntuforums.org/archive/index.php/t-12388.html)) is only partly useful...
As far as i know powernowd runs without errors:
```
# powernowd -l 100 -u 100 -m 2 -v
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Settings:
powernowd:   verbosity:        1
powernowd:   mode:             2     (PASSIVE)
powernowd:   step:           100 MHz (100000 kHz)
powernowd:   lowwater:       100 %
powernowd:   highwater:      100 %
powernowd:   poll interval: 1000 ms
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 667Mhz - 1000Mhz (2 steps)
powernowd:      step1 : 1000Mhz
powernowd:      step2 : 667Mhz
```

dmesg shows no errors

```
$ cat /proc/cpuinfo 
processor       : 0
cpu             : 7455, altivec supported
clock           : 667.000000MHz
revision        : 0.2 (pvr 8001 0302)
bogomips        : 66.56
timebase        : 33331035
platform        : PowerMac
machine         : PowerBook3,5
motherboard     : PowerBook3,5 MacRISC2 MacRISC Power Macintosh
detected as     : 80 (PowerBook Titanium IV)
pmac flags      : 0000001b
L2 cache        : 256K unified
pmac-generation : NewWorld
```

but i still don't know
a) how i can access the actual temperatures measured by the sensors
b) whether i missed some important kernel-modules (maybe a pendant to therm_adt746x)
c) whether i can use cpu throttling to further reduce power-consumption
d) whether i can reduce the power consumed by the graphics card (ati radeon  9000 mobility ( often identified as 7500 by other linuxes, xubuntu says it's a  Radeon R250 Lf [FireGL 9000] (rev 01))

If you you know of anyting that might help me i'd be glad to hear from you.
Thank you all
DonLaverty

---

