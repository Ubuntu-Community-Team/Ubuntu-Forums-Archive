---
title: "CD Sound very quiet"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by dbusse on 2007-05-27
I'm running Ubuntu 7.04.  I tried playing a CD using Rhythmbox.  Playback is very very quiet.  Sound sliders set at high.  I followed the instructions on the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") but after installing Ubuntu Restricted Extras, playback is still quiet.

I started up ALSAMIXER.  Master shows only a small rectangle with 00.  PCM shows a tall rectangle with white, yellow and red squares flowing to the top and a value of 100.  CD has no rectangle above it and no value showing.

Any help would be appreciated.

---

### Post by yabbadabbadont on 2007-05-27
If Master is at 00, then the master volume is at zero.  (which you probably already knew :D)  In alsamixer, use the up arrow to increase it to around 50% or so and see if it helps.

---

### Post by dbusse on 2007-05-27
This is what is odd.  Up arrow does not work on the Master.  It only works on the PCM, MIC and CAPTURE.  I can not get Master or CD to change.

---

### Post by dbusse on 2007-05-28
This morning when I booted up, Ubuntu popped up a dialog stating that there were updates for the system.  I applied the updates and re-booted.  Sound has worked since then.  

To the Canonical Fiesty Fawn support group - great job guys!  I came from the software support world so I know of what I speak.  You guys are great!

This issue is solved.

---

