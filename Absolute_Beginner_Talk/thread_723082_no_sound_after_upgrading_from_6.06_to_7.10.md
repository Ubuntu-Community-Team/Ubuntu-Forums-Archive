---
title: "no sound after upgrading from 6.06 to 7.10"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Gusx1 on 2008-03-13
yesterday i put ubuntu 6.06 onto my pc everything worked including my sound really didn't have to configure anything it did it all itself, anyway i get 7.10 by reinstalling over 6.06 from the CD after that i noticed i had no sound and  followed everything in this guide [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) with no prevail i'm sure i did everything right, i need sound because i always listen to music and use youtube help please and thanks.

---

### Post by kpkeerthi on 2008-03-13
Did you try changing the settings with alsamixer?

---

### Post by Gusx1 on 2008-03-13
I think so i put all the volumes full etc, im using a SB Live! device.

---

### Post by kpkeerthi on 2008-03-13
Make sure the mixer channels in alsamixer are not muted although volume appears to be raised to fulli. 'MM' indicates muted. Press 'm' key to toggle mute/unmute. 'OO' indicates unmuted.

---

### Post by Gusx1 on 2008-03-13
> **kpkeerthi said:**
> Make sure the mixer channels in alsamixer are not muted although volume appears to be raised to fulli. 'MM' indicates muted. Press 'm' key to toggle mute/unmute. 'OO' indicates unmuted.
just doublechecked there all OO every single one, i have no clue whats wrong. If it worked on 6.06 it should surely work on 7.10 right?

---

### Post by Arthur Archnix on 2008-03-13
What's the output of ```
aplay -l
```

Also, I recently installed Arch and when I came back to Ubuntu suddenly my sound was gone. I'm on a laptop, and the way I got it back was by shutting down, rebooting into bios,resettting, saving and closing then doing a hard-power down. Then I took out the battery and held down the power button for 10 seconds.

This worked for me, but some people report having to do it nude, during a full moon, standing in a puddle of tears of their enemies. [-X

---

### Post by Gusx1 on 2008-03-13
> **Arthur Archnix said:**
> What's the output of ```
aplay -l
``` [-X

i followed the guide thats why theres the emu10k1 thing there.. i donno how to reset it back to normal because i didnt do it in 6.06 and heres the output when i type aplay

```
gusx1@gusx1-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [SBLive! Value [CT4832]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 2: Live [SBLive! Value [CT4832]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Live [SBLive! Value [CT4832]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gusx1@gusx1-desktop:~$ 
```

---

### Post by superprash2003 on 2008-03-13
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Gusx1 on 2008-03-13
Alright sorry i had to go to work, sorry if im not allowed to bump my topic, alright i have my sound preferences on "ADC Capture/Standard PCM Playback on  everything when i tested it the first time it gave a very loud screatching soundsound but only when i test it, I clicked test a second time and i get this error now

```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

alright i got sound on everything except my broswer and im not sure about mp3s yet or videos if someone can help with my broswer problem please

mp3 and videos work, still no sound in broswer witch seems wierd to me help please and thanks.

---

### Post by Gusx1 on 2008-03-13
anyone able to help me in my no sound in broswer problem please :(

---

