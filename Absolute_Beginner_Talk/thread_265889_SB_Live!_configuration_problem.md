---
title: "SB Live! configuration problem"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by apkolev on 2006-09-26
Hi!

I have a problem to configure my sound in Ubuntu. Here is the output from the  ***aplay -l*** comand:

> 
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4832]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
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
card 0: Live [SBLive! Value [CT4832]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4832]], device 3: emu10k1 [Multichannel Playback]  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


As you can see I have two soundcards. One is the VIA that is integrated in the motherboard and the other is SB Live. When I installed Ubuntu for the first time the sound was working fine from the SBLive output. That was when Ubuntu was fresh and clean from the box. Than I started fixing it - put VLC, Skype and other small things. What I have noticed was that the sound was gone after some restart. I tryed the output from the VIA and it was working and again dissapeared after a couple of restarts. This time it switched back to SBLive. That was anoying but ok - I still had sound. As a possible solution I disabled the VIA soundcard from the computer setup. At the moment there is no sound output at all ](*,) . The system started with the Volume Control Muted. I tried the increase the volume but nothing happens. 

I want to use SBLive for the sound output or VIA but how to make at least one of them work!

I would be grateful if you have any suggestions.

P.S. I have a microphone connected to SBLive and whan I was using it with Skype I noticed that I can hear my voice in the headphones. I tried to mute to sound but it unmuted by iself and even increased its volume. Any idea how to fix this? Thank's in advance!

---

### Post by bodhi.zazen on 2006-09-26
Try this:
[[color=blue]Comprehensive sound guide[/color]](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by apkolev on 2006-09-26
Looks good! I will try it now! Thanks!

---

### Post by apkolev on 2006-09-30
Thanks for the link! It is very useful and helped me a lot. Still I keep the VIA soundcard turned off in the BIOS but SBLive is running fine!

Cheers!

---

