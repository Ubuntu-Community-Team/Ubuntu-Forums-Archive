---
title: "Sound only from headphones not speakers-Ubuntu 8.04"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by roocraig on 2008-04-20
I just installed Ubuntu 8.04 this morning, so I am a newbie I guess. I have noticed that I get sound through my headphones, but not through my speakers.  sudo lshw -class sound 
  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

and sound card description is:
ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

Knowing all of this, can some help me and give my step by step instructions through the terminal and help me get my sound.

Thanks in advance.

Ryan

---

### Post by seijiroikeda on 2008-04-21
Upfront thanks for any help...!!!

I'm having the same problem. I get sound from my headphones but not from my speakers... I found this guide here in the forum: [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound)    

But it seems too old (2006), and I did found my Sound Card by following the commands #1, #2 in that guide, but when i get to part #3, I get stock. I don't find the "drop down box" in that link provided, and I tried to find my Sound Card Driver, too match it just like it says there, but no luck...!!!

Please can some one explain how the ALSA works? or provide the right Link for ALSA, so I can check if I have the right Sound Driver, and keep on moving with that guide? Or even better, the right solution to get the sound working from the speakers..!!!

This is what i have:

chino@chino-laptop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

chino@chino-laptop:~$ lspci -v

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Rioworks Unknown device 2052
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Rioworks Unknown device 2052
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f8efc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

