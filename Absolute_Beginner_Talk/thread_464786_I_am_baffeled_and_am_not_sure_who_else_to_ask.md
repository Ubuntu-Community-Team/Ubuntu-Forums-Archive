---
title: "I am baffeled and am not sure who else to ask"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-06-05
I am not sure if this is an Ubuntu problem or a hardware issue or what, but:

Last Saturday my system just shut itself off for no reason.  At first I thought it was a power outage but the TV and stuff was still on.  I rebooted, no worries.  it ran fine the rest of the night.  The next day, out of the blue it did a partial power down.  Meaning I could hear the HDD's power down and the monitors went blank (no signal) but the fans and the LEDs stayed on.  In fact the, fans went to full RPM as they no longer were speed controlled.  If I pressed the power/reset button, the CD-ROMs would do their self check, but no boot or POST.  I have to power off the power supply for about 15 min, then turn it on to get it to boot.  I thought it might be a heat issue, but I run a pretty cool system and it rarely gets above 35C.  I just replaced the mother board this evening(I was sure that was the problem), and after having it up and running for about an hour, it did it again.  At this point I am really stumped.  Does anybody have any ideas of what it could be?  Does anybody have any ideas of what it isn't?  Yesterday, I would have sworn up and down that it couldn't be the OS, but now I'm not sure anymore.

System:
Asus A8N-SLI Premium Mobo
AMD 64x2 3800 cpu (not over clocked)
7600 GeForce vid card
250 gig Seagate SATA HD
160 gig WD SATA HD
80 gig WD IDE HD
2 generic CD-ROM/writes
Thermaltake case & 500 watt powersupply.
Ubuntu 7.04

Anybody have any ideas?

Thanks!
-B

---

### Post by rich.bradshaw on 2007-06-05
What it is the output of dmesg around the time of the shutdown?

Sounds like an ACPI issue - ACPI should be the thing you search for probably...

---

### Post by orb9220 on 2007-06-05
> I have to power off the power supply for about 15 min, then turn it on to get it to boot.

First Suspect: Bad Power Supply
Second Suspect: Heat

On many bios there is a place to monitor Temps,Voltages,Fans you may have a power supply that is not maintaining voltages within specs. You could watch the levels for a bit and see if any are misbehaving.

Also If the bios has been OC Overclocked for CPU,Ram, or OC'ing a video card can cause these kind of problems.

Sorry can't be more specific without being there and looking myself.

---

### Post by meatpan on 2007-06-05
Good suggestions above.  Definitely check the output of the command 'dmesg' . This command is useful because it reads important system log messages that were written to the /var/log folder by ubunutu.

Also, consider visiting the support pages of your hard drive and memory manufacturers.  Sometimes companies offer hardware fitness tests that you can download and run on your machine.    These tools typically give a nice diagnostic output, which will help you rule out some hardware problems.

---

### Post by shijirou on 2007-06-05
Seen this problem a lot before as I've worked as the IT guy in our company. The culprit is usually the power supply, it might have been grounded.

---

### Post by southernman on 2007-06-05
Just to add to the other good suggestions, IF you have the Livecd, plop her in before going to bed and run memtest86+ on it.

See if you get any errors out of that. Could very well be the culprit... too.

Good Luck

---

### Post by cjssmo on 2007-06-05
I also had this problem.  What would happen is that my system would shut it self down, then one day it just totally quit.  Turn out that it was the power supply. 

Hope this helps

---

### Post by marmaladejackson on 2007-06-05
Thanks guys.... Seems everyone is zeroing in on the power supply.  What would I be looking for in the dmesg output?  I took a look at one I generated last night and didn't see anything that grabbed my attention.  I don't think it is heat because everything is clean and not over clocked.  Prior to this week, it has been on continuously since November in the same configuration with out a hitch.  Guess it is off to newegg to see what they got in power supplies.  I let ya know if that works.
Thanks

---

### Post by Big_Croc7 on 2007-06-05
Before you go out and buy a new one, have a play around with the system.  You've got quite a lot of things in that system; 500 watts should be plenty for overall power, but the 12V rail might be struggling with 5 drives, even from a good power supply.

You sound like you don't mind taking the cover off, so try running it for a while with two hard disks and both cd drives unplugged if possible (or, all HDs and run from the live CD).  Also, if there's integrated graphics on the motherboard, try taking your graphics card out too.  All this will help to reduce the load on the psu (and also heat generated, which is good, even if that's not the problem).

---

### Post by Zzl1xndd on 2007-06-05
Im a little late to the party but I would agree this has al the signs of being a sketchy power supply. saw it a lot when i was working as a tech.

---

### Post by marmaladejackson on 2007-06-23
Thanks all.  Been off the grid for a while waiting for parts.  I can say now that it was most definitely the power supply.  She's been running for about 36 hours now without a hitch.  Thanks again, without your guidance the power supply would have been the absolute last thing I would have replaced.

---

