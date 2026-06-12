---
title: "Problems with sound continue..."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by merkki on 2007-10-28
I got my sound working yesterday, but after I restarted computer today I haven't got it to work. Yesterday I tried everything like lspci -v which gave access denied to both sound cards. Also in bios soundblaster was disabled and then I enabled it. Unmuted everything in alsamixer and it began to work. But now I try these and it doesn't work. 

Any ideas on how to solve this problem? Should I disable the other soundcards somehow?

---

### Post by Octavgmail.come on 2007-10-28
i know this may sound weird but it worked for me. 

open up your volume control go to edit prefs enable external amplifier go back to your volume control go to switches and click the external amplifier off you may need to switch it off then on then off again real quick!

hope this helps it worked for me but they do need to fix this, several other people have had this problem also.

---

### Post by merkki on 2007-10-28
didn't work...

Here are my soundcards, 
----------------------------------------------------------------------------------------------------------------------
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
        Subsystem: Giga-byte Technology Unknown device a000
        Flags: medium devsel, IRQ 10
        I/O ports at d800 [size=256]
        I/O ports at d400 [size=4]
        I/O ports at d000 [size=4]
        Capabilities: [c0] Power Management version 2

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at c400 [size=32]
        Capabilities: [dc] Power Management version 1
----------------------------------------------------------------------------------
and I only want to use the SB live soundcard


and i got this squeling sound when i turned mix on
ouch!!

---

### Post by merkki on 2007-10-28
According to aplay -l I have 3 soundcards?

**** List of PLAYBACK Hardware Devices ****
card 0: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive! Value [CT4832]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SBLive! Value [CT4832]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive! Value [CT4832]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by merkki on 2007-10-28
ARRGHHH

I can't understand why the sound won't work, cause it worked yesterday!

---

### Post by Therion on 2007-10-28
> **merkki said:**
> I got my sound working yesterday, but after I restarted computer today I haven't got it to work. Yesterday I tried everything like lspci -v which gave access denied to both sound cards. Also in bios soundblaster was disabled and then I enabled it. Unmuted everything in alsamixer and it began to work. But now I try these and it doesn't work. 

Any ideas on how to solve this problem? Should I disable the other soundcards somehow?
Two things:

1.  Disable the onboard sound in your system's BIOS (the AC97 Audio Controller chipset).

2.  Right-click/Open Volume Control.  
Click on Edit/Preferences (do not use "Preferences" from the context menu).
Scroll down till you find the **Audigy Analog/Digital Output Jack**. 
Put a check mark in that box and new tab will show in the Volume Control panel called "Switches".  
Unmute the channels in the "Switches" tab.

If that doesn't work, take a look a the [[color=blue]Comprehensive Sound Problems[/color]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problems") thread for more suggestions.

---

### Post by merkki on 2007-10-29
Ok, i've done all of that (also disabled onboard soundcard in BIOS). Btw, The FIRST thing I did was try everything in that comprehensive sound problems, but it assumes that the onlpy possible problem there can be is that your switches are muted, provided your soundcard shows up when u type lspci -v.

I've tried setting the SB live soundcard as my default, no help. 

Man, this was so much easier in windows, just install the driver and ta dam.

---

