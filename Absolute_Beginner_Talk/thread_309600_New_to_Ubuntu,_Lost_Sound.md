---
title: "New to Ubuntu, Lost Sound"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2006-11-29
I am currently using Ubuntu 6.06 LTS, and this is my first linux experience. I ran the live cd, and audio worked. I installed Ubuntu, and the audio worked, then after several days, the audio stopped working. When I boot to XP, sound works fine.

Computer is a Dell desktop, about 2 years old. Has a PCI sound card.

I read the sound guide, but I couldn't find a solution to my problem

When I run aplay -l

I get the following output:
> **** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The computer sees the sound card, but for some reason stopped making sound.

I ran alsamixer, and there are a lot of sliders. I have Master, PCM, and Surround unmuted, although there are some other options, such as 3D contour which are muted.

Anyone have any ideas how to get my sound back?

-Andrew

**Edit: Resolved. See post #9 for details. **

---

### Post by OptimusPrime on 2006-11-29
Unmute and turn up all the sliders in the sound control, and your PC's speakers to.  You might have already done that, but I was dumb enough to turn up all the sliders, but I didn't turn on the computer's speaker.

---

### Post by Atreus12 on 2006-11-30
I unmuted everything, and maxed all the volumes out, but I still don't get any sound. Sound works fine in windows, so it's not a speaker issue. Any ideas?

I've been through the sound guide about 10 times, have done all the steps to get my card set to default etc.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

-Andrew

---

### Post by Atreus12 on 2006-12-01
I fixed it. I was never so happy to hear the login sound.

So for other people who have the same issue, I muted the analoge / Digital jack, and external amplifier. After these were muted, everything worked. Somehow, when installing software or something they got unmuted, and thus my sound went away.

---

### Post by kamaruus on 2006-12-10
Hey i'm an extreme drunk noob. Your last comment about muting the external amplifier and output jack solved my dilemma. I follwed every post i could, and i was so happpy when my audio worked. Thank you so much, and long live Ubuntu!

---

### Post by hazillow on 2007-01-07
Hey -

I also have the same problem you had, with the same soundcards etc. However, muting Analog/Digital Jack and External Amp. did not solve my problem. If you have time, could you go through your alsamixer for me and see exactly what you have on and to what volume?

Thanks a lot in advance.

---

### Post by houstonbofh on 2007-01-07
> **hazillow said:**
> Hey -

I also have the same problem you had, with the same soundcards etc. However, muting Analog/Digital Jack and External Amp. did not solve my problem. If you have time, could you go through your alsamixer for me and see exactly what you have on and to what volume?

Thanks a lot in advance.
An easier solution is for you to boot the Live Cd.  If sound works, you can see the configs for it yourself.  The Live CD is a wonderful tool for fixing personal screw-ups.  Don't ask me how I know. ;)

---

### Post by hazillow on 2007-01-07
> **houstonbofh said:**
> An easier solution is for you to boot the Live Cd.  If sound works, you can see the configs for it yourself.  The Live CD is a wonderful tool for fixing personal screw-ups.  Don't ask me how I know. ;)

You are my hero. You have no idea how happy this makes me. I'll give you my first-born if you want him.

---

### Post by Atreus12 on 2007-01-09
> **hazillow said:**
> Hey -

I also have the same problem you had, with the same soundcards etc. However, muting Analog/Digital Jack and External Amp. did not solve my problem. If you have time, could you go through your alsamixer for me and see exactly what you have on and to what volume?

Thanks a lot in advance.

In case anyone else needs it here's what I have for a dell soundblaster live pci card

In alsamixer, I have the following settings:

Master - **unmuted** (Important)
Master Mono - unmuted (doesn't seem to make a difference)
3D Control Switch- unmuted (as the title claims, it somehow makes the sound seem like it's coming from all around, not just in from the speakers, try playing a song and muting / unmuting it)
3D Control Sigmatel Depth - unmuted (volume not at 0)
3D Control Sigmatel Rear Depth - unmuted (volume not at 0)
PCM - **unmuted** (Important)
PCM Out - no options to mute / unmute
Surround - muted (doesn't seem to make a difference)
Line - muted (doesn't seem to make a difference)
CD - muted (doesn't seem to make a difference)
Mic - muted (doesn't seem to make a difference)
Mic Boost - muted (doesn't seem to make a difference)
Mic Select - no options
Video - muted (doesn't seem to make a difference)
Phone - muted (doesn't seem to make a difference)
PC Speakers - muted (doesn't seem to make a difference)
Aux - muted (doesn't seem to make a difference)
Mono out - no options
Analog / Digital output jack - **muted** (Important)
External Amplifier - muted (doesn't seem to make a difference)
Sigmatel 4 speaker stereo - muted (doesn't seem to make a difference)
Sigmatel Output Bias - muted
Sigmatel Surround - muted (doesn't seem to make a difference)
Sigmatel Surround Phase Inversion Playback - muted (doesn't seem to make a difference)


Hope this helps anyone who gets stuck.

I highly recommend turning on the 3D control. I had it turned off until I went through and played with them, it makes a significant difference with music quality. Maybe some of these (or other) tips could get put in at the end of the comprehensive sound guide?

-Andrew

---

