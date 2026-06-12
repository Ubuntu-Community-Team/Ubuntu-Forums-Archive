---
title: "sound only coming out of headphones"
date: 2011-09-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by h2z on 2011-09-18
Just installed ubuntu natty, the sounds are only coming out of the front headphones, nothing from the rear speakers. In windows sounds works on both devices. These are the devices in the system according to aplay:

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The HDMI card is disabled as it's on the graphics card and I have no use for it right now.

When I open 'Sound Preference->Hardware', Internal Audio only shows 1 output, 1 input. No Idea how to fix this and make sound work on both speakers and headphone. Any help would be appreciated.


EDIT: using motherboard M4A785-M, ubuntu natty with gnome instead of unity.

---

### Post by vikrant82 on 2011-09-20
Its the other way round here. I have sound from my internal speakers but not from the audio jack.

That's on G74sx, on oneric.

EDIT:
However, I reinstalled, alsa related packages and the linux kernel which seemed to fix it for now.

---

