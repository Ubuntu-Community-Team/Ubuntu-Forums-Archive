---
title: "[SOLVED] program specific mp3 playback problems"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2008-01-12
Suddenly my amarok and totem cannot play mp3s as they could before. Interestingly, Audacity can play mp3s and other audio (eg podcasts via icepodder) isn't giving me any problems. I notice when I launch amarok, I can hear an audible click over my speakers, as if they are being unplugged. 

I'm not sure what info would be helpful...I'm using ALSA mixer...This problem may be related to the installation of upgrades recommended by update manager yesterday. Unfortunately, I can't remember how to retrieve the list of upgrades. Help is greatly appreciated.

---

### Post by nikoPSK on 2008-01-12
alsa update cause problems? have you got the codecs from gstreamer?

---

### Post by scholzilla on 2008-01-12
yes, in fact I reinstalled gstreamer codecs just to test that. As for alsa updates, I don't remember how to check which updates I have done recently. I know there is a file, I just can't remember its name.

---

### Post by nikoPSK on 2008-01-12
Well, then it's most likely ALSA... :[

---

### Post by scholzilla on 2008-01-12
Yep, you're right. I went under System-->Preferences-->Sound and changed my playback settings from Autodetect to ALSA. All seems to be well now. Thanks!

---

### Post by nikoPSK on 2008-01-12
No problem!

---

