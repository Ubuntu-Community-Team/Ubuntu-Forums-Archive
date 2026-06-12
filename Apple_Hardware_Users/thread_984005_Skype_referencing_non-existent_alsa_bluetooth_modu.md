---
title: "Skype referencing non-existent alsa bluetooth module"
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by rickbsgu on 2008-11-16
White MacBook 2.0ghz, Core 2 duo, 2ghz.
Ubuntu amd64 8.10 upgraded from 8.04

Skype audio trying to read Alsa bluetooth module.

get the following errors when running from the CL:

  => ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so

(presumably for each device trying to access.)

I've tried:

  . resetting the Skype devices to something else.

  . re-installing the alsa bt package (it says it's installed.)

I haven't tried setting up BT, but I opened the CP and it seems to be there and working - it saw several devices.

So, getting sound to work with Skype seems to be a deal-breaker, for me.

Any tips?

rickb

---

### Post by volanin on 2008-11-16
> **rickbsgu said:**
> So, getting sound to work with Skype seems to be a deal-breaker, for me.

I also get these messages.
And while I have not tried sound via bluetooth devices...
... normal sound via the speakers + built-in microphones works perfectly.

In the Sound Devices configuration tab, I use:

**Sound In:** HDA Intel (hw:Intel,0)
**Sound Out:** pulse
**Ringing:** pulse

---

