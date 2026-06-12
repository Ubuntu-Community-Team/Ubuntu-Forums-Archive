---
title: "trying to fix sound, don't understand this part"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-02-11
i'm following the guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

i just got to the part where it says

(3) Reboot
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.
(4) At this point, try using

aplay -l

and this is the output i got. it looks to me like the soundard is there, so i tested a cd out & still hear nothing. the settings in alsamixer are all unmuted & up to 100%. i have no idea what all those subdevices are. should i just continue & compile?

```

gail@gail-oldpos:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4871]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SBLive! Value [CT4871]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4871]], device 3: emu10k1 [Multichannel Playback]  Subdevices: 1/1
  Subdevice #0: subdevice #0
gail@gail-oldpos:~$

```

---

### Post by deadgobby on 2007-02-11
Hi,
 This is a very simple thing to do. You have a SB card and to get every thing to play out of your SB live like mine. You'll need to go into your BIOS and disable the on board sound card. That is it. After that play with the ADSL and adjust the levels to your liking. 
Gobby
PS that guide is a little bit out dated. Do the above and you'll be rocken.

---

### Post by lunaz on 2007-02-11
hm, i went into bios to disable onboard sound bu i didn't see any option for that anywhere. this is an old gateway
edit: hm, i got something by putting my name in the audio group. i got a really cruddy set of speakers tho, so u put in headphones & got better sound from those. i'll bring home a set of cheap spekers & see what happens next. :P

---

### Post by deadgobby on 2007-02-11
Oh damn! There has to be a way to disable the on board sound. When it goes to the BIOS, does it give a name. If you are not sure
[http://support.gateway.com/support/drivers/help/whichbios.shtml](http://support.gateway.com/support/drivers/help/whichbios.shtml)
 Then when you found out. Google it and find out how to disable the on board card.

---

