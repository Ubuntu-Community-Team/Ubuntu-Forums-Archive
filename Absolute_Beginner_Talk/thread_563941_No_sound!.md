---
title: "No sound!?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2007-09-30
hi 
i recently came arcross the problem of having NO SOUND ive had it for a very long time now and suddenly one day whne i restarted i had no sound i can evan plug a head set in and use that im not sure if its a hardware problme or just something go updated or unistalled :confused:
it would be a great help 
thanks

---

### Post by linuxwizard on 2007-09-30
You didn't post any info on your computer /sound card. If you are using Feisty and have installed all the latest Ubuntu updates their seems to be issues with no sound after install. You might want to check Launchpad for bug reported on kernel. Could be a fix or work around for your issue.

---

### Post by fdrake on 2007-09-30
just an obvious question:did u check alsamixer controls?

---

### Post by Malibu Illusion on 2007-09-30
Posting the output of this would be a good start:

```
aplay -l
```

---

### Post by yimmmy on 2007-09-30
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


sory guys im not thiking this sound thing is realy throwing me off 
yes i tryed the alsa sound,  i   tryed ever one i could find

---

### Post by ambar.amarelo on 2007-09-30
Try to see this Sound Troubleshooting:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

