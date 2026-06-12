---
title: "[SOLVED] Mini Core Solo Hardy microphone input issue"
date: 2008-08-30
forum: Apple Hardware Users
---

### Post by gastur on 2008-08-30
Good day!

I'm having the following issue with my early Intel-based MacMini:
no input from external microphone.

System: 8.04.1 with all recent updates (single boot).
Device Intel HDA (SigmaTel STAC 9221 A1).

I have tried all "model=" parameters for this chip on Macs from
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
with virtually no results. Anything except "model= intel-mac-v3" (or no parameters at all) yields no output and no input - no matter what alsamixer settings are. Even "model=macmini" which theoretically is equivalent to "intel-mac-v3" is of no use.

With "model= intel-mac-v3" or no parameters there is slight microphone input (nearly undistinguishable from noise) when input source is set ... to "line" instead of "mic".

Tips, tricks and suggestions will be greatly appreciated :)

---

### Post by cyberdork33 on 2008-08-31
run 'alsmixer' in a terminal, then switch to the capture section by pressing [tab], then make sure the level for you mic and capture channel are turned up.

---

### Post by gastur on 2008-08-31
> **gastur said:**
> no matter what alsamixer settings are

Sigh.

---

### Post by entangled on 2008-08-31
Mini solo microphone input is expecting line level. Unless your microphone signal is boosted to that level the mini won't cope with it. I've just used USB handset (for skype use) and that works OK for input and output.

---

### Post by gastur on 2008-08-31
Thanks, I'll try!

---

### Post by gastur on 2008-08-31
Hundred thanks to you, **entangled**!

Tomorrow I'm leaving home for long and very far, and wanted my family to be able to communicate with me using skype.

Following your advice I took USB webcam with builtin microfone (my friends in local PC shop allowed me to test it at home before bying), set the input source in skype to "USB camera" - and voila!

Thank you very much!

---

### Post by cyberdork33 on 2008-08-31
> **gastur said:**
> Sigh.
Yes, I saw that, but since you do not give any details as to what alsamixer settings actually exist or that you adjusted, I can't assume that you have tried the _right_ settings.

Did you go to the recording page instead of just the output page (which can also have a mic level)?

---

### Post by gastur on 2008-08-31
Sure, I tried different input settings, switched input sources, changed input levels etc. Also I did it for different "model" settings for snd-hda-intel in /etc/modprobe.d/alsa-base (of course, those settings that suite my chip - STAC9221 A1).

Sorry, but - no result.

Anyway, thank you for trying to help!

---

