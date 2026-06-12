---
title: "how do i find my MAC Specs on ubuntu?"
date: 2008-06-23
forum: Apple Hardware Users
---

### Post by collarfor12 on 2008-06-23
how do i find out what/how much ram i have and my processor speed?


i have an imac G3 with xubuntu 


cheers

---

### Post by ilrudie on 2008-06-23
Use the following commands in a terminal:

CPU:
cat /proc/cpuinfo
Mem:
free

---

### Post by stream303 on 2008-06-23
Keep in mind that your if your cpu supports frequency scaling, you might not see the fastest speed depending on what is going on with your box at the time you issue the command.

For example, my 1.8ghz rated machine is currently running at 900 mhz when I checked with **cat /proc/cpuinfo**

```
processor       : 0
cpu             : PPC970FX, altivec supported
clock           : 900.000000MHz
revision        : 3.0 (pvr 003c 0300)

timebase        : 33333333
platform        : PowerMac
machine         : PowerMac8,1
motherboard     : PowerMac8,1 MacRISC4 Power Macintosh 
detected as     : 338 (iMac G5)
pmac flags      : 00000000
L2 cache        : 512K unified
pmac-generation : NewWorld
```

I also have 1.5gb of ram installed in my iMac, and here's the result of **free -m**

```
             total       used       free     shared    buffers     cached
Mem:          1445        380       1064          0         12        182
-/+ buffers/cache:        186       1259
Swap:         4235          0       4235
```

I used the -m switch to show the output in megabytes, rather than K.  You can also see that I have a ridiculously large swap, but this is because the automatic computation based on installed ram, is a bit unrealistic when you have a large amount to begin with. :)

To help keep an eye on things, the *top* command is quite useful, although I prefer downloading and running *Htop* as a substitute.

---

### Post by collarfor12 on 2008-06-23
cheers guys!

---

