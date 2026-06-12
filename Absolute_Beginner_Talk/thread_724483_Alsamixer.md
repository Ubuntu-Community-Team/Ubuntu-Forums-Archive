---
title: "Alsamixer"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by r5gtt2k3 on 2008-03-14
Since i just updated my system my sounds no longer play, and you know how frustrating that is, Well im on the alsmixer wiki page and it's tellimg me all these options to press (i had this problem before but just got rid of Ubuntu an went back to windows) I have an Audigy 2 ZS and it was working just fine earlier, But, It's not seeting as my default card i think think, Alsamixer is showing my HDA Nvidia soundcard which is onboard, Now how do i go about changing it back to my audigy ? an I have checked all the settings in prefrences, the digital output isnt ticked nothing is muted either, I get one thing working, another goes wrong :*( 

I have ran in the terminal "sudo /etc/init.d/alsa-utils reset" yet that didnt do anything

---

### Post by mali2297 on 2008-03-14
Post the output of
```

lspci | grep [Aa]udio
aplay -l
cat /proc/asound/modules

```

---

### Post by r5gtt2k3 on 2008-03-14
lspci | grep [Aa]udio

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/modules

0 snd_hda_intel
 1 snd_emu10k1


1 snd_emu10k1 <-- thats the one that i want as default, But I've no idea (I've been looking for the answer on the net for ages) it's starting to get tedious now 
Thanks for your reply :)

---

### Post by mali2297 on 2008-03-14
> **r5gtt2k3 said:**
> 
cat /proc/asound/modules

0 snd_hda_intel
 1 snd_emu10k1


1 snd_emu10k1 <-- thats the one that i want as default, But I've no idea (I've been looking for the answer on the net for ages) it's starting to get tedious now 
Thanks for your reply :)

OK, then open the file **/etc/modprobe.d/alsa-base** with
```

sudo nano /etc/modprobe.d/alsa-base

```
At the end of the file, add these lines
```

options snd-emu10k1 index=0
options snd-hda-intel index=1

```
Save (Ctrl+o) and quit (Ctrl+x). Reboot.

From [here]("https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea").

---

### Post by r5gtt2k3 on 2008-03-14
Got it, Thanks dude :) I must write that down :)

---

