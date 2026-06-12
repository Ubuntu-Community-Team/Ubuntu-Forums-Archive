---
title: "Audcaity error while opening sound device"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by alphasurfari on 2007-11-27
I am running into problems with Audacity. I have a number of choices for audio input device and output device.
input:
ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - IEC958 (hw:0,4)
ALSA: default
ALSA: iec958
ALSA: spdif
ALSA: dmix

output:
OSS: /dev/dsp
ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 (hw:0,0)
ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - MIC ADC (hw:0,1)
ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - MIC2 ADC (hw:0,2)
ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - ADC2 (hw:0,3)
ALSA: default
ALSA: front

any combination of the above with the 'Software Playthrough' box checked either gives the 'Error opening sound device dialog' or crashes Audacity when trying to record. Same thing in either Audacity 1.2.6 or 1.3.3. 

I have no idea how audio is handled on linux so I am completely lost. Are there any guides which might explain what these various audio devices are and how I can configure them to fix this? Or does anyone have a quick fix solution for me?

---

### Post by Pumalite on 2007-11-27
[http://audacity.sourceforge.net/manual-1.2/tutorial_basics_4.html](http://audacity.sourceforge.net/manual-1.2/tutorial_basics_4.html)
[http://www.pcplus.co.uk/tutorials/creativity/recording_with_audacity](http://www.pcplus.co.uk/tutorials/creativity/recording_with_audacity)
[http://lwn.net/Articles/202851/](http://lwn.net/Articles/202851/)

---

