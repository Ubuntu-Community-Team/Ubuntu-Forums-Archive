---
title: "Help recording internet streams"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by tylerjroach on 2007-05-30
I want to record internet streams using Audacity but my sound card is not configured correctly and I do not know how to fix this problem. It used to work but I don't remember when it quit and it was probably during an upgrade. When I go to preferences and the recording tab there are many choices but none will work. I know it is not just Audacity and other programs do not work either. Would someone please walk me through this. Thank you

---

### Post by Crafty Kisses on 2007-05-30
This happened to me too, have you tried the "Vol" option on Audactiy. When you select that as your recording device it should work then, let us know.

---

### Post by tylerjroach on 2007-05-30
my choices are:

ALSA: card0
ALSA; front
ALSA: Intel ICH6: Intel ICH6 - ADC2 (hw:0,3)
ALSA: Intel ICH6: Intel ICH6 - MIC ADC (hw:0,1)
ALSA: Intel ICH6: Intel ICH6 - MIC2 ADC (hw:0,2)
ALSA: Intel ICH6: Intel ICH6 (hw:0,0)
OSS: /dev/dsp

Every single one of these displays an error message saying:

Error while opening sound device. Please check the input device settings and the project sample rate.

---

### Post by tylerjroach on 2007-05-30
I've also noticed that if i try to use the sound recorder built in ubuntu that it says record from input with a drop down box but there are no choices to chose from so I need to configure something?

---

### Post by Crafty Kisses on 2007-05-30
> **tylerjroach said:**
> my choices are:

ALSA: card0
ALSA; front
ALSA: Intel ICH6: Intel ICH6 - ADC2 (hw:0,3)
ALSA: Intel ICH6: Intel ICH6 - MIC ADC (hw:0,1)
ALSA: Intel ICH6: Intel ICH6 - MIC2 ADC (hw:0,2)
ALSA: Intel ICH6: Intel ICH6 (hw:0,0)
OSS: /dev/dsp

Every single one of these displays an error message saying:

Error while opening sound device. Please check the input device settings and the project sample rate.

That's really weird could be a sound card issue. Have you installed the codecs?

---

### Post by tylerjroach on 2007-05-31
What do you mean by codecs. I have all the multimedia codecs installed on my system and it must be a sound card issue because i just reinstalled ubuntu and I still have the same problem. Does anyone know any possible way to fix this?

---

