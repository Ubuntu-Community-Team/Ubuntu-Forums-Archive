---
title: "Sound problems - please help"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Absolut139 on 2007-10-09
Been trying to get sound working for a few days now, have read the comprehensive guide and failed repeatedly to see any positive changes.  On fresh install and live cd of Ubuntu Feisty sound works no problem, but after a few days the sound disappears with no apparent reason or connection to certain desktop changes.  Had sound to start, lost it, did a fresh install, got sound back, now its gone again.  Not very well versed in linux but wiling to learn.  Running an Asus M2N 32 Sli deluxe which i believe runs the soundmax AD1988 chipset. Also have a pci turtle beach catalina which seems to be completely unsupported but whatever.  output from asplay -l

rick@rick-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AV710 [Chaintech AV-710], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

just downloaded the most current alsa driver 1.0.15rc3
also edited to prioritize soundmax over turtlebeach.  

selected output of lspci -v

00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

and

00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
If anyone knows how i can get either to work i would be delighted
thanks:confused:

Don't have any idea what to do. Please help

---

### Post by chrisTGc on 2007-10-10
Hi,

Dunno if this will help but recently changed my motherboard which meant a new soundcard for a while until i reinstalled my 5-1 c-media card Fiesty and the Linux kernel took it all and no problems except initialising the changed sound card which i always do from Systems>Preferences>Sound and clicking the various fields and selecting the new card then testing it.Perhaps i have been lucky but it has been as simple as that.

Best Wishes Chris.

---

