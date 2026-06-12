---
title: "Ugly static when using JACK"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by acl123 on 2007-11-23
Hi,
I'm trying to use JACK but I am getting heavy distorted static during playback. I can hear the sound correctly but the static is on top.
A program like ZynAddSubFX works fine when JACK is turned off but not when JACK is on.

This is the output from my aplay -l

> 
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA25 [UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have tried running JACK and JACK-enabled applications using sudo and turning on realtime scheduling, but this doesn't help the problem.

I am using the alsa driver and I'm running Gutsy.

Any help would be greatly appreciated. I feel this is the final step to being able to record some music without having to switch back to Windows.

---

### Post by acl123 on 2007-11-26
I fixed this by using my UA25 for both input and output, instead of using the onboard card. Not sure what were the problems with the onboard card.

---

