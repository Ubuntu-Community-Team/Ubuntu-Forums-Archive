---
title: "Audigy 2 not playing sound in Feisty Fawn:"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by jrelprestoo on 2007-05-28
I'm about ready to pull my hair out over this... so any help would be greatly appreciated.  I'm a total Linux noob, so you'll have to keep things REEEEAL simple for me (well, as simple as possible).  So far, I've managed to get most of the OS configured on my own--but this has completely and utterly stumped me.

I've scoured practically every thread  in these forums, and nothing has worked so far... including:

1. Disabling the Analog/Digital switch.
2. Putting the snd-emu10k1 in that one modules file.
3. Installing alsamixer.
4. Disabling the onboard audio through the BIOS.
5. And a myriad of other things that have probably wound up screwing me in the end.

I've seen people post certain file type things, so I'll do the same in the hopes that it may illuminate the Ubuntu wizards as to the nature of my problem.  Me?  I'm totally stumped and practically bald from all the hair I've ripped out of my head over the last four hours.

From aplay -l:

> **** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

From lspci -v:

> 01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Unknown device 1002
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at ac00 [size=64]
        Capabilities: <access denied>

I'm leaving town tomorrow morning through next Monday.  I'll have limited access to the Ubuntu forums in case anyone has any questions that might allow them to pinpoint an answer; unfortunately, I won't have my computer with me, so my memory may be vague at best--and clueless, at worst.

I appreciate any help that any of you can provide.  I'm gonna go play a computer game before I wind up tossing this rig out of my second story apartment window.  ;)

Best wishes and many thanks,
J.

---

### Post by jrelprestoo on 2007-05-28
I guess it should be noted that I'm pretty sure this is just a plan ol' Audigy 2.  Not Audigy 2 Gamer, etc.  Not sure if an Audigy 2 is the same as an Audigy Platinum... or if that whole package deal is just related to the bundled software.  :)

---

### Post by sevencapitalsins on 2007-05-30
I have malfunctioning of my Audigy 2 Platinum: it should be noted that before the upgrade to (Kubuntu) Feisty it worked like a charm, ant this made me a little upset... It's like your wife going to bed with your worst enemy.

Me too I did search the forums, and no one of the solutions worked:
when I boot up, the audio sometimes works and sometimes doesn't!

After 1000 tries, I discovered that maybe there was a slight correlation with the audio switch provided with my Creative Inspire T5100 sound system: if i turn off the PC with the audio-power-switch set to OFF, at the reboot Xine would fail miserably to find an audio device. If I held it ON, the audio device was recognized--- but it does NOT work everytime.

Another thing I have noticed: when it fails, Kmix always reverts back to Intel ICH5 (I tried also to disable it via bios, but nonetheless Xine won't find a device).

I noticed also that alsa and alsa-utils are not enabled on runlevel 2 (weren't on the list of services that are loaded at bootup), I enabled them to be loaded at bootup and still.. tadan... don't work.

](*,)

:roll: maybe Mummy Debian knows the solution to her son's faults... bad boy bad boy [-X

---

### Post by sevencapitalsins on 2007-05-30
WOAH!

I think I found the right thread, cause now i hear my lyrics pretty well and strong enough to blow off the house!!!

[http://ubuntuforums.org/showthread.php?t=457761&highlight=audigy](http://ubuntuforums.org/showthread.php?t=457761&highlight=audigy)

Also, get a look at this thread

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+audio+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+audio+guide)


Sorry Debian, I'll stick with Ubuntu for now :)


I hope this might help you, jrelprestoo.

---

### Post by sevencapitalsins on 2007-05-30
EDIT:

i rebooted and now the audigy totally disappeared from aplay -l...

**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0



I'm totally fed up :(

---

