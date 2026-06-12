---
title: "No sound on 12&quot; Powerbook 1,5 GHz"
date: 2012-02-20
forum: Apple Hardware Users
---

### Post by tasha77 on 2012-02-20
Hello everyone,

I almost successfully installed xubuntu 11.10 on my above mentioned Powerbook.

However, I'm not able to get sound output working. I've read the PowerPCFAQ and thus tried the following:


[LIST]
[*]checked if the sound is muted: it isn't
[*]checked if my device is supported by snd-aoa: Powerbook6,8 is supported
[*]commented out snd-powermac in /etc/modules
[*]added snd-aoa to /etc/modules
[/LIST]
But I still have no sound.

It's not a hardware problem, sound is working in Mac OS 10.4.11.

What should I try next?

---

### Post by rsavage on 2012-02-21
Hi, have you checked the channels are muted or just the master volume?  I'm not sure if alsamixer is loaded in xubuntu - it probably is.  It's quite hard to see at first if a channel is muted with alsamixer, but you'll be able to see if you just toggle a channel with the m key.
 
If you have a file, /etc/modprobe.d/blacklist.local.conf, that blacklists many of the snd-aoa modules then you'll need to delete that file or load the required modules in /etc/modules (you'll have to add more than just snd-aoa).

---

### Post by tasha77 on 2012-02-22
> **rsavage said:**
> Hi, have you checked the channels are muted or just the master volume?  I'm not sure if alsamixer is loaded in xubuntu - it probably is.  It's quite hard to see at first if a channel is muted with alsamixer, but you'll be able to see if you just toggle a channel with the m key.
 
Thank you very much for directing me to alsamixer again. It solved the problem. There was no muted channel, but the volume of the PCM channel was set to zero.

---

### Post by rsavage on 2012-02-23
Thanks for the feedback.  I've added a bit more to the FAQ based on your experience to try and make it clearer.

---

### Post by seinch on 2012-06-12
Hi to all,

This is my first message to this group, thanks in advance to all for your patience...

I have the same PB G4 than Tasha77, but we did a dual install with MacOSX and Lubuntu 12.04.

It was fine with alternate CD, we can configure the B43 driver of Airport Extreme but no luck with soundcard.

Attached here I will put some info:

**cat /proc/cpuinfo**

processor    : 0
cpu        : 7447A, altivec supported
clock        : 1499.999000MHz
revision    : 1.2 (pvr 8003 0102)
bogomips    : 36.86

total bogomips    : 36.86
timebase    : 18432000
platform    : PowerMac
model        : PowerBook6,8
machine        : PowerBook6,8
motherboard    : PowerBook6,8 MacRISC3 Power Macintosh 
detected as    : 287 (PowerBook G4 12")
pmac flags    : 0000001a
L2 cache    : 512K unified
pmac-generation    : NewWorld
Memory        : 1280 MB


**/etc/modules**

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

apm_emu
loop
snd-powermac
therm_adt746x
pmu_battery
snd-aoa
snd-aoa-codec-tas
snd-aoa-fabric-layout
snd-aoa-i2sbus
snd-aoa-soundbus
snd-aoa


**/etc/modprobe.d/blacklist.local.conf**

# Local module settings
# Created by the Debian installer

#blacklist snd-aoa-codec-tas
#blacklist snd-aoa-fabric-layout
#blacklist snd-aoa-i2sbus
#blacklist snd-aoa-soundbus
#blacklist snd-aoa

---

### Post by seinch on 2012-06-12
Sound working.

I don't know how i tested before, I haven't got sound on system but playing a mp3 I have it!

BR

---

