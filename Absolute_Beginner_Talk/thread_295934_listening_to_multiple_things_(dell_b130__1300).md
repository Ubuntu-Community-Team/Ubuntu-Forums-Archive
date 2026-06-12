---
title: "listening to multiple things (dell b130 / 1300)"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by econobeing on 2006-11-08
I can only listen to one thing at a time(one channel?) say for instance I'm listening to some music in amaroK, if I go to youtube, there's no audio. The audio won't play if I pause the music or stop it, I have to close down any video/audio program i currently have running. 

Is there anyway to be able to listen to more than one thing at a time?

---

### Post by MasterOfDisaster on 2006-11-08
This would be from the use of OSS instead of ALSA.  OSS doesn't support sound mixing, while ALSA does.

Not sure if this works, but worth a try?

Right click on the little sound icon in your upper right corner toolbar, and choose preferences.  It should come up with a dialog that shows 'Select the Device and Track to Control', so choose the one that uses ALSA mixer instead.

Hope that helps.

---

### Post by econobeing on 2006-11-08
hmmm it gives me these options:

HDA Intel (Alsa mixer)
SigmaTel STAC9200 (OSS Mixer)

the HDA Intel one has these:
Master
PCM
Capture
Capture Mux
Capture Mux

the SigmaTel has:
Volume
In-gain

it was already on the alsa one :/ still only one channel though.

---

### Post by MasterOfDisaster on 2006-11-08
Sorry then, man.  Never had a problem with my sound, so not sure what to do:(

---

