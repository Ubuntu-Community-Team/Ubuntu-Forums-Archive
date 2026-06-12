---
title: "New install = no sound (iMac G4)"
date: 2009-04-20
forum: Apple Hardware Users
---

### Post by Hascal1022 on 2009-04-20
I am a brand new Ubuntu user and I finally got the OS (8.10) installed. I cannot get sound to work.

When I click on the volume control, it tells me: No volume control GStreamer plugins and/or devices found.

Thoughts?

---

### Post by tiresia on 2009-04-20
Have you tried loading the snd_powermac module - though it should already be there...```
modprobe snd_powermac
```

---

### Post by Hascal1022 on 2009-04-20
I tried that and this is the error message I got: 

FATAL: Error inserting snd_powermac (/lib/modules/2.6.25-2-powerpc/kernel/sound/ppc/snd-powermac.ko): Operation not permitted

I new at Ubuntu/Linux so I am a bit lost.

---

### Post by Hascal1022 on 2009-04-20
Some more info...

modinfo gave me this:

filename:       /lib/modules/2.6.25-2-powerpc/kernel/sound/ppc/snd-powermac.ko
license:        GPL
description:    PowerMac
srcversion:     E061EBA0F8E083868F944DC
depends:        snd-pcm,snd
vermagic:       2.6.25-2-powerpc mod_unload 
parm:           index:Index value for PMac soundchip. (int)
parm:           id:ID string for PMac soundchip. (charp)
parm:           enable_beep:Enable beep using PCM. (bool)

---

### Post by Hascal1022 on 2009-04-20
This is what "speaker-test -t sine" gave me:

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_BE, 1 channels
Sine wave rate is 440.0000Hz
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

Unable to set hw params for playback: Input/output error
Setting of hwparams failed: Input/output error

---

### Post by tiresia on 2009-04-20
Sorry, you should use modprobe with sudo ```
sudo modprobe snd_powermac
```

---

### Post by Hascal1022 on 2009-04-20
I tried that and there is still no sound.

---

### Post by Hascal1022 on 2009-04-20
Does shaking it violently help?

---

### Post by Hascal1022 on 2009-04-25
Anyone else have any other thoughts on the annoying problem?

Thanks
:confused:

---

### Post by roym4 on 2009-04-29
try adding snd-powermac to the /etc/modules file

---

### Post by stream303 on 2009-04-30
Try snd-powermac with the hyphen rather than the underscore.

In 9.04, /etc/modules lists it both ways. :)

---

