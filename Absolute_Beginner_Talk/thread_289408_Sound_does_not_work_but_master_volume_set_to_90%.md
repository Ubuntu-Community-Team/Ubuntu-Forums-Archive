---
title: "Sound does not work but master volume set to 90%"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Sarah13 on 2006-10-30
Alright, so for several reasons, I ended up reinstalling Ubuntu (dapper drake) from scratch. My problem is that my sound does not work. I've been testing it using the examples provided with Ubuntu, because I figured those would be safest, although I have tested it with other files.

Anyways. I have two sound cards/chips. One is a Ensonique Creative Audio PCI (ES1371, ES1373)(WDM), but that one is on the motherboard itself and its ancient, so I installed Soundblaster Live 5.1 and rebuilt Ubuntu with the SB card in place. Now, I still don't have sound. The master volume is set to 90%, the default sound is set to SB, and I don't know what else to do to get it working.

Can anyone help? It obviously recognizes that the SB card is there if it will let me mute/unmute its sound, so why doesn't it work?

Thanks.

---

### Post by Sarah13 on 2006-10-30
Oh, and I don't know if this helps, but this is what I get when I run 'aplay -l'


```
penguin@penguin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SBLive 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive 5.1 [SB0060]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
penguin@penguin:~$

```

---

### Post by MyAnda on 2006-10-30
you mentioned muting...when my sound is gone it is usually because it is muted...try running "alsamixer" (commandline) and make sure you don't see MM at the bottom of any important columns...also make sure pcm is turned up...just to rule out permissions, you may also try to "sudo chmod 777 /dev/mixer" and /dev/dsp...may also want to make sure whatever module for the sound blaster is loaded (lsmod)...maybe that will be somewhere to start...

---

### Post by Sarah13 on 2006-10-30
> **MyAnda said:**
> you mentioned muting...when my sound is gone it is usually because it is muted...try running "alsamixer" (commandline) and make sure you don't see MM at the bottom of any important columns...also make sure pcm is turned up...just to rule out permissions, you may also try to "sudo chmod 777 /dev/mixer" and /dev/dsp...may also want to make sure whatever module for the sound blaster is loaded (lsmod)...maybe that will be somewhere to start...

Thanks. I've done that already though, I guess I should be more clear. That is how I know it's not muted; I went through alsamixer. PCM is turned up, and it's loaded.

I now have run the entire tutorial for fixing sound problems (found [here]("http://www.ubuntuforums.org/showthread.php?t=205449")). and my sound still isn't working.

I've even gotten the Alsa drivers from a fresh kernel.

---

### Post by MyAnda on 2006-10-31
humm...not sure if it will help, but I ran across these
[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t48385.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t48385.html)
[http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/6693-no-sound-sblive-card-mandrake.html](http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/6693-no-sound-sblive-card-mandrake.html)

and have you gone through this?
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1)

---

### Post by jaytek13 on 2006-10-31
I had the same problem... Easiest solution? Disable the onboard sound controller in the BIOS.

---

### Post by caravel on 2006-10-31
Make sure you've selected the correct sound device from the sound menu in the administration menu.  Also it would be a good idea to disable that onboard sound chip from the BIOS if you've got another sound card in there.

---

### Post by Sarah13 on 2006-11-04
> **jaytek13 said:**
> I had the same problem... Easiest solution? Disable the onboard sound controller in the BIOS.

In the Bios, under audio all I see is the SB. Does this mean that the onboard is not loaded and that's not my problem or am I looking in the wrong place?

---

### Post by gitano1 on 2006-11-04
I don't know that this will be of much help, but I had a Sound Blaster card in an earlier computer that would never work in Ubuntu. I spent a lot of time on the forum trying to find someone to help, tried several "solutions" to no avail. My current set up has a integrated sound card on the motherboard and it worked from the first. It seems that Ubuntu works best with that configuration. Sorry if that is discouraging. It is better than](*,)

---

### Post by Sarah13 on 2006-11-04
> **gitano1 said:**
> I don't know that this will be of much help, but I had a Sound Blaster card in an earlier computer that would never work in Ubuntu. I spent a lot of time on the forum trying to find someone to help, tried several "solutions" to no avail. My current set up has a integrated sound card on the motherboard and it worked from the first. It seems that Ubuntu works best with that configuration. Sorry if that is discouraging. It is better than](*,)

It is better than ](*,) . I set up Linux on this old box with the intention of using it as a multimedia computer, even though everything is really outdated. But as soon as I have the funds I'm going to build a new multimedia system from scratch, and that will be the most important one to get everything working on. 

But I'd really like sound on this computer. I'm not stressing it though. Everything working would be wonderful, but I can deal with it if it doesn't. I'll keep working on it off and on.

Thanks!

And I'm definitely open to more solutions/help.

---

