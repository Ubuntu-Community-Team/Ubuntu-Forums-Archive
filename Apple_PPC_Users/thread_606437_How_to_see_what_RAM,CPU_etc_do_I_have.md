---
title: "How to see what RAM,CPU etc do I have?"
date: 2007-11-07
forum: Apple PPC Users
---

### Post by ondoin on 2007-11-07
I just got an iBook with Mac OS X and XFCE installed (dual boot) and I am new to this so sorry for my stupid question.
How can I see what RAM,CPU,HD etc does the computer have?
When I tried to do it through the Mac Os all I found was that I had 128 RAM PowerPC Processor.
I am not sure what version of Xubuntu I have.

---

### Post by 3rdalbum on 2007-11-08
You can find out the model of PowerPC processor by typing:

```
cat /proc/cpuinfo
```

at the command prompt.

I'm not sure about the rest, but I know there's a way.

---

### Post by Sef on 2007-11-08
> I am new to this so sorry for my stupid question.

Not a stupid question.   I have learned lots by asking and listening.

For ram: ```
free -m
```

For system information: ```
 sudo dmidecode | more
```

---

### Post by frog_pilot on 2007-11-08
You can also use the System-Profiler in Mac OSX. There is much detailed Information about your hardware in a user friendly gui...

---

### Post by ondoin on 2007-11-08
Thank you guys.
For the command cat /proc/cpuinfo gave me these results and I have a couple of questions.

processor       : 0
cpu             : 745/755
temperature     : 19-21 C (uncalibrated)
clock           : 400.000000MHz
revision        : 51.17 (pvr 0008 3311)
bogomips        : 33.19
timebase        : 24960000
platform        : PowerMac
machine         : PowerBook4,1
motherboard     : PowerBook4,1 MacRISC2 MacRISC Power Macintosh
detected as     : 257 (iBook 2)
pmac flags      : 0000001b
L2 cache        : 256K unified
pmac-generation : NewWorld

First,why it says Processor 0?
The CPU is 745/755.Does it mean my CPU is 750 MHz?
What about the clock?It says it is 400MHz.

Generally do I have a good computer?

---

### Post by stoodleysnow on 2007-11-08
I know that in Ubuntu with Gnome you just go to System > Administration > System Monitor, and click on the far left tab at the top.
:)

---

### Post by ondoin on 2007-11-08
> **frog_pilot said:**
> You can also use the System-Profiler in Mac OSX. There is much detailed Information about your hardware in a user friendly gui...
How exactly do I go there?Because I was told to click About this Mac and choose More but there is no More!

---

### Post by frog_pilot on 2007-11-08
In the default Application-Folder you will find an Utilities-folder (or a similar name) there you can find system utilites and one of them is System-Profiler. - It is a program and it`s part of a default OS X installation.

I would say... click here and there and you will find everything you need.

---

