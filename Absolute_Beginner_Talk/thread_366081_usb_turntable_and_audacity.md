---
title: "usb turntable and audacity"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rhr on 2007-02-20
I have a NForce2 (soundstorm) motherboard with an Athlon XP 3200. Xine, youtube videos, etc all play fine. I received a USB turntable (plays those analog flat vinyl music things) and I would like to do the conversion from LP to my media library on my "edgy" box. I am using the Nvidia sound drivers in order to take advantage of the optical audio out ports. That means OSS for sound. If I do a "lsusb", I can see the USB audio controller in the turntable. If I go into the Sound manager and set everything to autodetect, the test button works for everything EXCEPT audio conferenceing. If I set audio conferenceing to USB, the first time I click "test", I hear a brief bit of sound from the turntable.
Within audacity, the only sound source is /dev/dsp, and it seems I cannot change that. Ideally I would like to use the USB turntable for the source and the vnidia chipset for playback. Does anyone have any ideas on how to get audacity to use the USB turntable as an input?

Thanks,

rhr

---

### Post by NewOldTimer on 2007-02-20
Your sound source/input selector is often greyed out as there is only one audio route {from device to pc via usb} control of input is at the device end which audacity has no control.

Sorry that's about all I know but here is a link that matches you to more specific area's hope it helps

[http://audacityteam.org/forum/forum/16](http://audacityteam.org/forum/forum/16)

---

### Post by rhr on 2007-02-20
Today I booted my machine with the turntable connected and powered up. When I went into audacity, There was a new option of /dev/dsp1 for a recording source. I selected that and VOILA! IT WORKS!!!!!

I'm starting to like this stuff!:grin:

---

### Post by Flamekebab on 2007-06-03
Excellent!
So if I build a MythTV box I should be able to integrate a USB turntable into it?

---

