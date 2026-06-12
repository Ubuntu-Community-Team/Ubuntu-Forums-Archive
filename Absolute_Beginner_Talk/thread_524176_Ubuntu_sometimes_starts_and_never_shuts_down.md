---
title: "Ubuntu sometimes starts and never shuts down"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Coward on 2007-08-12
I have recently installed Ubuntu 7.04 on my laptop. This is my first time using Linux (except for experimenting with an embedded version of Damn Small Linux). I have two problems but don't know if they are related.

When I turn my computer it always gets all the way through the loading bar. About 1 in 6 times it will go to the login screen without problems. The rest of the time the screen will go black. I have read in my searches to try ctrl+alt+f1 but this does nothing for me. I have to hold the power button to turn off the computer so that I can try again and hope I'm lucky. I have tried booting Ubuntu in recovery mode, but it gets stuck sometimes aswell. It does not always get stuck in the same place when loading in recovery mode.

When I try to shutdown the computer begins to turn off but gets caught in an endless loop with the shutdown sound. Unlike the startup, this always happens.

This is what I know about my laptop from the setup screen. Tell me if you need more information.
**Notebook Model**
HP Pavilion dv6000 (RX945AV)
**Processor Type**
AMD Anthlon 64 X2
Dual Core Processor TK-53
and it has an integrated NVIDIA something.

So what should I try to solve either of these problems?
Would it help if I told you the various places it gets stuck when booting recovery mode?

[Solved (kind of)] I enabled the Nvidia drivers. It solved these problems but I have a new one. I will post this in a new thread.

---

### Post by Coward on 2007-08-13
The most common stopping point for my recovery mode boot is this:

[   0.000097] CPU#1 had 212 usecs TSC skew, fixed it up.

The 212 changes but has always been in the 200s so far.

Does this mean anything to anyone?

---

### Post by Lucifiel on 2007-08-13
To do a "safe" reboot, try:

> hold down Alt + Print Screen(key) and press the following keys: YUIB 
Your issue sounds a little like an ACPI issue to me but ... I'd let those who're more experienced comment on this.

---

### Post by Lucifiel on 2007-08-13
Okay, try the "permanent solution" in this thread which involves editing menu.lst . It should work for Feisty:

[http://ubuntuforums.org/showthread.php?t=21189](http://ubuntuforums.org/showthread.php?t=21189)

---

### Post by Coward on 2007-08-13
I haven't been able to boot Ubuntu at all for a while, I'm trying to reinstall. The graphical install isn't working (it took a couple tries the first time) so I'm going to try the alternate CD.

When should I be pressing that key combination for the safe restart? Is that once Ubuntu is completely loaded?

I'll update this once I've reinstalled.

---

### Post by Coward on 2007-08-13
I've reinstalled using the alternate CD. This time I got the 64 bit version.

The install went smoothly with it working the very first time, but Ubuntu never boots now. The loading bar now always gets stuck in the same place, and when I boot in recovery mode it now always gets stuck at the line

* Loading hardware drivers . . .

Although this seems like a step backwards it may be easier to solve now that it is consistent. I don't know what to do though.

Edit: It just got past it and went to * Setting up console font and key map
Edit: It got through the entire thing this time and then got to a black screen. It hasn't fully booted yet, and the stopping points are completely different from last time.

---

### Post by Happy_Man on 2007-08-13
Yes. That would help loads.

EDIT: Hmm... didn't see your second post. THat does look like your hardware is having trouble. What is it all?

---

### Post by Coward on 2007-08-13
If it gets past the step *Setting up console font and keymap... it waits allows me to type like it was a terminal. Currently I'm just typing "exit" to allow it to go on (to a black screen). Should I try typing something else?

It still usually gets stuck at Loading hardware drivers though, so I really want to solve this problem.

---

### Post by Coward on 2007-08-13
Sometimes instead of stopping at *Loading harware drivers... it stops at the next line which says "error receiving uevent message: No buffer space available." I googled it but the only time I saw this error solved was by someone's reinstall miraculously fixing it. Does anyone have any suggestions?

---

### Post by Coward on 2007-08-13
What step is normally after "* Setting up console font and keymap..." ? It says [ OK ] next to it but doesn't get to the next step (if it is lucky enough to get to this step). I'm curious about what is getting stuck. I feel like Ubuntu must be close to booting.

(I have tried reinstalling, again, but get the same results)

Will update after I eat with the hardware I have.

---

### Post by Coward on 2007-08-14
So Ubuntu seems to have problems detecting my hardware. Any idea of what could cause the problem?

HP Pavilion dv6000z CTO NB
AMD Athlon(TM) 64 X2 Dual-Core Mobile Technology TK-53 ( 1.7 GHz, 512KB L2 Cache)
15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
1GB DDR2 System Memory (2 Dimm)
NVIDIA(R) GeForce(R) Go 6150 with Additional Productivty Ports
HP Imprint Finish + Webcam + Microphone
802.11b/g WLAN
120GB 5400RPM
DVD/CD-RW Combo Drive
High Capacity 6 Cell Lithium Ion Battery

---

### Post by sml on 2007-09-01
What are the symptoms that make you think it is not detecting your hardware?

---

