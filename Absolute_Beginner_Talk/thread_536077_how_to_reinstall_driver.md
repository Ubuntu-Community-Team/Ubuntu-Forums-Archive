---
title: "how to reinstall driver ?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-27
I'm trying to figure out how to reinstall a driver for my sb live sound card.
I've been unable to make it work in edgy, feisty or ubuntu studio.
I noticed that the alsa mixer calls it SBlive value & my card is really the  5.1 Digital that came with a Dell computer. I don't even know how to install the driver let alone get the right one to begin with so could anyone give me a step by step instruction or point me to a site that does. I haven't been too successful understanding the incredible amount of information out there on the web. I'm now using Ubuntu Studio.

---

### Post by kyphi on 2007-08-27
The driver is already in the kernel.

On my system the Creative SoundBlaster 5.1 is identified as a Dell Sound Blaster Live and works perfectly.

If you go to System then Preferences and then scroll down to Sound you should have a window at the bottom that will list your default sound card.  If there are more than one device listed, as may be the case if you have an onboard sound chip, then you need to go into the BIOS to deactivate that.

Would you post the result of typing
 ```
aplay -l
```
 into a terminal, please.

---

### Post by garyed on 2007-08-27
I got the playback to work in the mixer but I can't record.
When I try sound recorder nothing shows up for an option at " Record from Input"

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4780]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SBLive! Value [CT4780]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4780]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by kyphi on 2007-08-28
Great, your sound card is recognised and works.

Look at this link and bookmark it for future reference:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Scroll to the section on alsamixer.  That is where you have to change things to suit you.

---

### Post by garyed on 2007-08-28
Thanks, that's some great info.
Unfortunately it hasn't helped me yet. 
I still can't get the record to work.
Nothing shows up as an input. 
Is there some way to test if the drivers recognize the input of the Sblive?
None of ther recording programs I've tried do.

---

### Post by kyphi on 2007-08-28
Forget about the drivers - they don't need adjusting.

Right click on your speaker icon on the top panel and click on Volume Control.   Go to Capture on the next screen and you will find some symbols at the bottom that have red crosses on them.  Click on the crosses to uncheck them.

Fingers crossed.

---

