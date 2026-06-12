---
title: "[server] machine shuts down by itself"
date: 2014-01-03
forum: Any Other OS
---

### Post by sowdust on 2014-01-03
Hi everyone! as the title says, I have a server that used to run Ubuntu and now has Debian, but the same problem still arises:
randomly, the machine - being or not attached to the network - at some point shuts down.
The front led, which is usually green, stays yellow blinking.
The logs (sys, kernel, apache, mail, ssh..) do not show any regular pattern before the shutting down.
The intervals are not regular either (it has stayed on for weeks up to yesterday, today has shut down twice).
The problem has been going on for years now and I still haven't found the cause.
It might be worth noting that the bios is set up to power on the computer in case of power deficiency.
Another weird thing is that sometimes the fan speeds up apparently with no reason.
The fan speeding up and the computer shutting down do not usually occur at the same time.
On this same forum, on another thread (I had initially thought it was an intrusion problem) I was suggested to replace the paste/glue between the CPU and its fan.
Before touching there, I would like to know if anyone had an idea of another possible cause, whose detection could be less intrusive.
Thanks,

---

### Post by Bucky Ball on 2014-01-03
*Thread moved to **Other OS/Distro Support**.*

You might also try posting on the Debian forums. You might have more luck.

[http://forums.debian.net/](http://forums.debian.net/)

---

### Post by sowdust on 2014-01-03
I'm sorry I didn't mean it to be "distro-offensive".  I have been using Ubuntu on my personal machine for years and have participated, even though mostly as a learner rather than an expert, to this community for a long time, always finding it very friendly. I know it is not a problem related to the software, so I had thought it wouldn't be bad asking here. I will try with the debian forum and see if I have more luck.

---

### Post by Bucky Ball on 2014-01-03
> **sowdust said:**
> I'm sorry I didn't mean it to be "distro-offensive". 

All good. Not 'distro-offensive' (unsure what that is!). The general support area here is for Ubuntu and derivatives: Ubuntu/Kubuntu/Xubuntu/Edubuntu/Lubuntu. Although Ubuntu is based on Debian, Debian is not officially supported here, thus the move. 

Good luck.

---

### Post by ian-weisser on 2014-01-03
> **sowdust said:**
> 
randomly, the machine - being or not attached to the network - at some point shuts down.
The front led, which is usually green, stays yellow blinking.
The logs (sys, kernel, apache, mail, ssh..) do not show any regular pattern before the shutting down.

A blinking LED looks a lot like a BIOS error code. The OS you run on that motherboard would be irrelevant.
Go to the manufacturer web site and look for the manual or error code list for your specific model.

---

### Post by lisati on 2014-01-03
Another possibility is that the machine is switching into hibernate or suspend mode. When I close the lid on my day-to-day laptop, the power LED switches from steady blue to blinking orange.

---

### Post by tgalati4 on 2014-01-03
You don't mention the hardware but a blinking front LED could be a power supply problem.  Also on Dell servers, when the fans start to scream, that could mean that a fan has failed.  Power supply problems will cause random shutdowns with inconsistent and misleading log entries.  Do you have an UPS on this machine?

---

### Post by sowdust on 2014-01-04
thank you all very much for the support.
First of all, let me clarify that even though I use it as a server, mine is a very small DellTM OptiPlexTM GX520.

I am almost sure it is not a problem with suspension/hibernation because 1) I have never set up any of that (neither now nor in my previous OS install) and 2) the intervals in which the machine shuts down are not regular at all (can go from 3 weeks to an hour).

Following Ian's suggestion I looked up the manual for my computer model and here is what it says about the yellow (it calls it amber) blinking led light:

[quote="Manual"]
If the power light is blinking amber :
The computer is receiving electrical power, but an internal power problem might exist.
 Ensure that the voltage selection switch is set to match the AC power at your location (if applicable).
 Ensure that the processor power cable is securely connected to the system board.
[/quote]

in the same doc, another chapter, I found

[quote="Manual"]Blinking amber indicates a problem
with an installed device; solid amber indicates an
internal power problem[/quote]

The only "external" devices that are installed are two external USB hdd, one of them not even working and always turned off.
Internally, I had removed the floppy and dvd drive.

I do not have a UPS system, but the Bios is set up to restore the most recent state in case of power failure: if it is on and I disconnect the power cable, when I reconnect it the computer turns back on.

Note that might be important: the machine is connected to the same set of power outlets of my tv, decoder and a couple of other things.
When the server shuts down, all else keep working perfectly. I don't know if it has anything to do with it or if it is just bad luck trying to confuse me, but sometimes the tv decoder has the same behaviour and either reboots after it has been used for long or just shuts down (again here, no standby or sleep mode). Honestly thought I think I just have a crappy tv decoder and the two things are not related.

Bios Log: since the OS installation, no entry has been added there at all.

---

### Post by tgalati4 on 2014-01-04
Dell has spent several hundred million dollars replacing bad power supplies under warranty.  The power supplies typically have cheap capacitors that leak or short and cause problems.  Do a web search on your model.

---

### Post by sowdust on 2014-01-04
> **tgalati4 said:**
> Dell has spent several hundred million dollars replacing bad power supplies under warranty.  The power supplies typically have cheap capacitors that leak or short and cause problems.  Do a web search on your model.
thank you. A shrewd google search supports your idea very much, suggesting it is probably a power supply problem. I should have a spare couple at my parents', as soon as I have a chance to go there I'll try installing those and let you know if it works.
Thanks all for the help!

---

