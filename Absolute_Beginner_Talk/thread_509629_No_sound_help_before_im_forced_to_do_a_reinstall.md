---
title: "No sound help before im forced to do a reinstall"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by erealz on 2007-07-25
ok i cant get sound from my system when i boots?however i could get it to work at start up by ether going to ,system ,administration services and clicking on and off the sound daemon and restarting 

please if anyone can help me troubleshoot this problem 

i have a creative sb live

more detail as requested if you need any detail that i have left out just reply with a walkthru on how i can go about getting you the info you need to trouble shoot

---

### Post by kyphi on 2007-07-25
The first thing to do is to check that you have your volume turned high enough.  Click on the loudspeaker symbol near the right of the top panel and move the slider.

Next go to System -> Preferences -> Sound and then enable the two boxes at the top.  At the bottom of that screen it should state 'Dell Soundblaster Live'.

To check that your soundcard is recognised, type in a terminal ```
aplay -l
```

The Creative SB Live should work perfectly.

Can you play a CD?

---

### Post by erealz on 2007-07-26
well of course i made sure my speakers volume is turn all the way up their not muted . 

> as for my soundcard being recognised

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [SB Live 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 2: Live [SB Live 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Live [SB Live 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

so thats a yes i belive. im at my wits end with this stupid problem?!?!

---

### Post by kyphi on 2007-07-26
Good, your SB Live is recognised by Ubuntu.

Did you check the loudspeaker icon on the top panel?  You can also do this in a terminal:

```
alsamixer
```

and that should show a screen with a volume control on the left.  If you move the slider on your loudspeaker icon on the top panel, the slider on the alsamixer panel will also move.

It looks like your computer has onboard sound as well as the SB Live.  The onboard sound should be disabled.  You can do that in your BIOS.

Did you enable the system sounds as I mentioned before and at the bottom of that screen does it say SB Live or something like it?

---

### Post by erealz on 2007-07-26
Hey man thnx alot for the help so far i really do appreciate it. anyways up to this point  i have done what you said and disable the onboard sound device soim just useing my creativ sound blaster card.

oddly enough, when i rebooted back into linux my sound didnt start . so I revisted my services in administration ,. sound deamon was clicked off?! i so i turn it back on. tested an mp3 and b00m!  I GOT SOUND. im going to reboot to see if  the settings stay like they are, working.

ill reboot and let you know how it gos....


ps: if their anthing else i should check let me know...

---

### Post by kyphi on 2007-07-27
> ill reboot and let you know how it gos....


Can I assume that your sound problems have been resolved?

---

