---
title: "No Sound Problem, please help"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by iiieckiii on 2007-10-11
Hi I'm using Ubuntu 7.04 and I haven't been able to get sound working on my system for quite sometime now. I've tried to research as much as I could before posting for help but nothing seems to do the trick. I've tried using the alsa mixer and unmuting and that didn't do the trick either. I've also tried using this guide [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and tried the command aplay -l and came up with this:

card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have no idea what this means but I'm guessing Ubuntu is indeed reading my soundcard but for some reason I'm not able to hear it. So I'm guessing because Ubuntu is reading the soundcard I don't have to follow the getting the alsa from fresh kernel and compiling it and all that stuff (correct me if I'm wrong here though). I have no idea what to do, I am currently dual booting with Windows XP on my other HD and the sound works perfectly in Windows. Please oh please someone help me get sound, all I'm trying to do is get just a few things working on Ubuntu.

---

### Post by overlord.gaurav on 2007-10-11
Well, I have similar problem, but I'm waiting for Gtusy to solve it

---

### Post by linuxwizard on 2007-10-11
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab

---

### Post by iiieckiii on 2007-10-12
> **linuxwizard said:**
> check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab


Sorry. I'm beyond noob so if you don't mind me asking how do get to the switches for analog or digital and how to get to the gnome panel? Sorry gotta have my hand held for a bit.. :(

---

### Post by linuxwizard on 2007-10-12
Gnome panel where you clock is. To the left of your clock their should be a speaker icon

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab

---

### Post by iiieckiii on 2007-10-12
OMG!!!!!!!! I am so noob I cannot believe I didn't think about this before and tried to make my life harder but trying to install new drivers and all that. God damn I'm stupid....... finally sound thank you VERY MUCH!

---

### Post by linuxwizard on 2007-10-12
That's great you have sound now. I have a Creative Audigy sound card also. Every install I do I have to change the switches in order to have sound. I use Dapper/Edgy/Feisty both Ubuntu/Kubuntu in everyone I had to change the switch settings.

---

