---
title: "Sound card not working - Ubuntu Edgy 6.10"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Sarcasticus on 2007-10-31
Hey Y'all,

I just installed Ubuntu Edgy, installed the latest updates, but my sound card isn't working. Here's my aplay -l;

**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I added "snd_ens1371" to my /etc/modules but that didn't work.
I had Edgy installed awhile ago, and there was some jazz about typing 
"sudo modprobe snd_ens1371
modprobe es1371"
before logging in, but I forget the exact details.

Any help would be greatly appreciated.
Thanks!

---

### Post by bks on 2007-10-31
Try upgrading to 7.04 or 7.10. I just went to Gusty and a lot of driver issues were resolved.

---

