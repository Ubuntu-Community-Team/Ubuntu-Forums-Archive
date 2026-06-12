---
title: "Amsn sound doesn't work"
date: 2008-05-23
forum: Apple Hardware Users
---

### Post by dustynus on 2008-05-23
I got the isight up and working on hardy amd64, macbook 2,1. Sound works fine as well.

Question is, I've installed Amsn, and going through video and voice, the video works by default. Choosing an Output device, I've tried both devices in the options list:
/dev/dsp
/dev/audio
Both when I try the play test file give:

An error occured when trying to play the sound: Could not access /dev/dsp for writing.


How can I get this workin?
Thanks
:guitar:

---

### Post by josephdaniel on 2008-06-01
exactly same problem here on hardy 32-bit... any solutions?

---

### Post by chucleskill on 2008-07-01
This will help go to aMSN and go to Account>Preferences>Others> and there where it says Sound Server select "Use a different program" and write "aplay $sound" if this doesnt work it could be a ubuntu sound problem :guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:
XD Good Luck

---

### Post by hardyn on 2008-07-01
amsn uses the OSS sound driver, not ALSA... check your mixer settings.

---

### Post by Bleezy on 2009-02-17
I have this same problem. And my system was set with: aplay $sound already there and it was giving me the problem.  Any ideas how to see what sound devices my OS is using? because it can play sounds just fine...

---

