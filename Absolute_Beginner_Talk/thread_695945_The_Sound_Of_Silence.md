---
title: "The Sound Of Silence"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by BigRon on 2008-02-13
When I first installed Ubuntu 6.10 the sound worked perfectly, could listen to CDs etc easily, however I couldn't get on the internet (I had one of those awkward modems).

A friend came round and got me online, but now since getting the modem to work I haven't heard one sound from the PC. Even the little jingle when you start up/shut down is gone. 

Before you ask, the volume slider in the top right hand corner is at max and is definately NOT on mute (I read someone made that mistake earlier).

I typed aplay -l into the terminal and got:

**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I was listening to cds on the day of install and now the pc is completely silent. It's odd, I can't think what could have happened between now and then. It's baffling.

I typed in alsamixer and it indicated that the master sound is on and at max level. Any help on this would be fantastic because I am one very confused newbie.  :confused:

---

### Post by Jewfro_Macabbi on 2008-02-13
what device is it using for sound? 

from the audo controls look under file, change device?

Make sure it isn't trying to use the modem for audio?

---

### Post by BigRon on 2008-02-15
Thanks to all for showing an interest. I have fixed the problem now by turning up the pcm level in alsamixer and then going into edit preferences in the sound settings and allowing surround.

Different bars turned up and all was fixed.

---

