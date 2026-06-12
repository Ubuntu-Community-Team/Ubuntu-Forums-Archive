---
title: "No sound capture / input"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Jalke on 2008-02-07
Hi, I've got  a problem with my sound input.  I can't seem to record anything (using sound recorder) or speak to anyone using skype.  Has anyone got any ideas for me?  

I've tried fiddling with the volume controls but am not too sure what they all are.  Same goes for alsamixer - not too sure what the settings should be.  Sound output is no problem.  I can hear people on skype and can play music off the laptop.  

Any help would be much appreciated.  I've just spent 3 nights fixing my wireless internet problem... now this.  I'm going to bed.

---

### Post by kpkeerthi on 2008-02-07
In alsamixer, the controls will be clearly marked in text. When a mixer control is turned off, M (mute) appears below the volume bar. When it's turned on, O in green appears instead. You can toggle the switch using 'm' key. Make sure Master, Master Mono, Headphone, PCM, Line and CD are not Muted and the sliders raised enough depending on the volume level you need.

---

### Post by Jalke on 2008-02-08
Thanks for the advice.  They're all turned on.

I think it happened after I installed a whole bunch of automatic updates.  Everything was working before then.  So I'm not sure what happened.  Any further tips would be greatly appreciated.

---

### Post by Jalke on 2008-02-08
When I go to Sound Preferences dialog box and select OSS for the Sound Capture box and then press *test* I get an error message stating:

*gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Unable to open device /dev/dsp for recording: Device or resource busy*

When I have it on Alsa and press *test*, the sound box pops up (as if it were playing) but I don't hear anything. Hmmmm....

---

### Post by Jalke on 2008-02-11
Please help... <bump>

---

