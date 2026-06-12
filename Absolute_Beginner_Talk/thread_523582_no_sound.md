---
title: "no sound"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Fuzzman on 2007-08-12
first off im going to say im very new to linux/ubuntu (take it easy on me) .i have an onboard intel sound card.  i  cannot get it to play any sound. i have updated all my alsa drivers and utilitys. i have tried many things all to fail. please help a noob.

---

### Post by undertakingyou on 2007-08-12
This post: [http://ubuntuforums.org/showthread.php?t=461405](http://ubuntuforums.org/showthread.php?t=461405) talks about a guy that has an intel sound in his motherboard.  I don't know that it resolves very well but you could try what he was told.

---

### Post by AlexenderReez on 2007-08-12
this howto help me once :)

> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by ddrichardson on 2007-08-12
There are an awful lot of threads on sound problems relating to Intel-snd-hda - any chance we can sticky one of the better one mods?

---

### Post by Fuzzman on 2007-08-12
Ill get some hardware info up when i get home.. This problem is really frustrating me and making my first linux experience very  bad. Thanks for all the info.

---

### Post by Fuzzman on 2007-08-13
Here is some hardware info. tell me what other additional info would help out.

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Fuzzman on 2007-08-13
please help im a complete noob....

---

### Post by Fuzzman on 2007-08-15
help?

---

### Post by scholzilla on 2007-08-15
there are loads of sound issues and i long for the day when they are resolved. The only way I was able to cure my woes was to reinstall feisty and refuse to accept any kernel updates (other updates are fine). I don't know if this will fix your problem, but it works for me.

---

### Post by ddrichardson on 2007-08-15
Try having a look through [this]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/113644") bug report (it's the first hit on google ;-))

It suggests to mute 'Headphone Jack Sense' and 'Line Jack Sense' - probably available if you right click the sound control, select open volume control and edit preferences to get all the switches displayed.

---

