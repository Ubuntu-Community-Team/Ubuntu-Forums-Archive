---
title: "Microphone not Working"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by achernar on 2007-06-05
An absolute newbie to Linux, I recently installed Ubuntu v7.04. The system, however, doesn't seem to be detecting my microphone!

I have Windows XP Professional installed on another partition of my hard-disk, where the microphone is working just fine, and where I've never encountered any problems using it, so I doubt there's anything wrong with my hardware.

I've had no problems with audio output, it's just input that seems a bit bungled.

Any help would be most greatly appreciated.

---

### Post by Pragmatist on 2007-06-05
Type this in a terminal:
```
alsamixer
```Using the left and right arrows, move to the column called Mic and make sure it isn't muted and the volume is up.  If there is an "MM" on the bottom, press 'm'.  Now there should be "00" where there was "MM".  To increase the volume just usethe up arrow.  When your all done, hit the ESC key.

---

### Post by achernar on 2007-06-05
Thanks for the help, but the settings there seem to be exactly as you say they ought to be. Could anything else be the problem?

---

### Post by sailor2001 on 2007-06-05
If you have your mic plugged into the front of your box, it's MIC 2  . .right click your sound icon and preferences and tick mic select

---

### Post by achernar on 2007-06-05
Brilliant! Worked perfectly. Many thanks.

---

