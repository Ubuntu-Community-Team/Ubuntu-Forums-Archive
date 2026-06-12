---
title: "Suspend stopped working"
date: 2009-01-04
forum: Apple Hardware Users
---

### Post by hyperboloid on 2009-01-04
Suspend (to RAM) has been working great for 3 months. Now it stopped working. When I try to suspend, I get a black screen with a blinking cursor in the upper left hand corner, and nothing I do can make it wake up, except holding down the power button to power down and then rebooting. 

Anyone else seeing this problem?

I just tried to hibernate, and that worked.

---

### Post by hyperboloid on 2009-01-06
I recall that recently whenever I run the Update Manager I started seeing a popup message saying
> **Sleep warning**
Your laptop will not sleep if you shut the lid as a running program is preventing this. Some laptops can overheat if they do not sleep when the lid is closed.
I never saw this message before, until recently. And the appearance of this message seems to coincide with my sleep problem, posted above. 

Could it be that a recent update borked my sleep function? If so, does anyone have any suggestions on where to start troubleshooting this problem? A laptop that can't sleep is pretty useless.

---

### Post by bryonak on 2009-01-06
I just checked after doing an update and it's working as good as ever on my MBP3.1
My repos are: 8.10 up to multiverse, Mactel, Medibuntu and WICD... any additional ones on your part?

Do you have a suspect on what this "running program" that prevents it could be?
That sounds strange, because things like video players blocking the screensaver are common, but suspend is handled completely differently.
Could it be some malfunctioning network share, as in: the volume handler tries to unmount it but gets a "resource is busy"?


Btw: how comes your hibernate works? (Mine did never out of the box and I don't care much about s2disk)

---

### Post by cyberdork33 on 2009-01-06
> **hyperboloid said:**
> I recall that recently whenever I run the Update Manager I started seeing a popup...
That is a warning that occurs because you are running the updates at that moment. Normally, after a period of time, your laptop would automatically try to suspend, but the update manager prevents suspend from occurring (we don't want a shutdown in the middle of an import system file being replaced, do we?). Because of this, your laptop may get hotter than normal because some laptops are not designed to operate in a closed position for very long and rely on heat dissipation through the keyboard area.

So, it is really a recommendation to leave the lid open while updating. That is all.

---

### Post by hyperboloid on 2009-01-06
> **cyberdork33 said:**
> That is a warning that occurs because you are running the updates at that moment. Normally, after a period of time, your laptop would automatically try to suspend, but the update manager prevents suspend from occurring (we don't want a shutdown in the middle of an import system file being replaced, do we?). Because of this, your laptop may get hotter than normal because some laptops are not designed to operate in a closed position for very long and rely on heat dissipation through the keyboard area.

So, it is really a recommendation to leave the lid open while updating. That is all.

Well, I understood that. However, I never saw this popup until a couple of days ago, even though I've been using Ubuntu 8.10 since early November 2008. 

Simultaneously with the appearance of the popup, my suspend, which had been working flawlessly since the beginning, has been completely broken. So I suspect this coincidence is not really a coincidence.

---

### Post by cyberdork33 on 2009-01-06
> **hyperboloid said:**
> Well, I understood that. However, I never saw this popup until a couple of days ago, even though I've been using Ubuntu 8.10 since early November 2008. 

Simultaneously with the appearance of the popup, my suspend, which had been working flawlessly since the beginning, has been completely broken. So I suspect this coincidence is not really a coincidence.
I would suspect that there was an update to the power management stuff that added the message, and broke your suspend. related, but not relevant to your problem I guess.

---

### Post by hyperboloid on 2009-01-07
> **cyberdork33 said:**
> I would suspect that there was an update to the power management stuff that added the message, and broke your suspend. related, but not relevant to your problem I guess.

Yeah, that's my guess, too. Wish I knew where to look. The odd thing is that nobody else seems to be reporting this, so there must be something specific about my situation as well.

---

### Post by emmary on 2009-01-07
China Bluetooth Device Wholesale 
  
Today you must own at least one Bluetooth enabled device, namely cell phone, laptop, personal computer, printer, video game console, or digital camera. Bluetooth is actually a wireless protocol which specifications are developed by Bluetooth Special Interest Group. It facilitates short-distance data transmissions and synchronization of these devices. The very common Bluetooth compliant versions at the present time include Bluetooth version 1.2 (1 Mbit/s data rate) and Bluetooth version 2.0+EDR (3 Mbit/s data rate). And Bluetooth Class defines range, such as Bluetooth Class 2 with 10-meter operating range and Bluetooth Class 1 with 100-meter coverage.

The following products are necessities in the Bluetooth-clustered environment. They deserve a look for not only what they show, but also how they perform. Thanks to these devices, you are allowed to connect PC or laptop to the Bluetooth enabled devices, enjoy handsfree communication even without taking the phone out of pocket while driving, and answer calls or put a call on hold with the headset. With the easy-to-swallow price tags, the products that TRADESTEAD offers are irresistible. 

Related Categories: Bluetooth Headset MP4 Player MP3 Watches LED flashlight Digital Photo Frames

---

### Post by cyberdork33 on 2009-01-07
> **hyperboloid said:**
> Yeah, that's my guess, too. Wish I knew where to look. The odd thing is that nobody else seems to be reporting this, so there must be something specific about my situation as well.
yes but I think many have settled on the fact that suspend rarely works and moved on, so they haven't noticed. You might file a bug in launchpad. There are some old suspend bugs there still, but I would make a new one explaining that it was working then broke.

---

### Post by Archmage on 2009-01-07
Did you get a new memory lately? Because the swap-file must be two times your memory, or else you can't susspend.

---

### Post by cyberdork33 on 2009-01-07
> **Archmage said:**
> Did you get a new memory lately? Because the swap-file must be two times your memory, or else you can't susspend.
that is for hibernation... (aka suspend to disk)

---

### Post by hyperboloid on 2009-01-07
> **Archmage said:**
> Did you get a new memory lately? Because the swap-file must be two times your memory, or else you can't susspend.

no hardware changes whatsoever ...

---

### Post by hyperboloid on 2009-01-26
Solved! 

All I had to do was reset the SMC. I followed the instructions posted here [http://support.apple.com/kb/HT1411]("http://support.apple.com/kb/HT1411") and now suspend works again.

---

### Post by cyberdork33 on 2009-01-26
> **hyperboloid said:**
> Solved! 

All I had to do was reset the SMC. I followed the instructions posted here [http://support.apple.com/kb/HT1411](http://support.apple.com/kb/HT1411) and now suspend works again.
Ah yes. Anytime you have weird power issues you should try that. This is true even for problems in OS X.

---

### Post by hyperboloid on 2009-01-29
Scratch my last post. Resetting the SMC did NOT work. The problem is actually with wicd! 

I finally noticed the real pattern, and I can now reproduce 100% of the time. 

A few months ago, I replaced network manager with wicd. At that time, I was connecting only via wireless, and wicd worked flawlessly. When I suspended, everything worked great, and wicd reconnected to the same access point upon resume, if available. 

Early in January, I moved to a different place where wireless is not available, and started connecting using wired ethernet instead of wireless. At the same time, my problem with suspend started. It seems that whenever I am connected to the internet via ethernet wire, if I try to suspend, the suspend hangs as reported in the first post of this thread. But, if I first disconnect the ethernet cable, and then suspend, all is well. I have now tested this multiple times, and the behaviour is always the same. If ethernet cable is present, suspend fails - if absent, suspend works just fine. 

So, it seems to be a problem with wicd scripts, but only in the case of an ethernet wired connection. Pretty strange. I plan to file a bug report on this soon, but thought I'd report to this thread in case anyone else runs into this bug. 

The workaround is just to unplug the ethernet cable before suspending the laptop, obviously.

---

