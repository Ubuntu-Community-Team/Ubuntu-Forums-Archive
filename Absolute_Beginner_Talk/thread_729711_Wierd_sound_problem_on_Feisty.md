---
title: "Wierd sound problem on Feisty"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by shone zlo on 2008-03-20
I've got a Maxdata laptop with Intel 82801 chipset. The sound basicly works, BUT it's crappy. By crappy I mean it's not coming out the way it should. It's distorted as if my speakers aren't working (whitch is not the case, since the same thing is going on with my earphones, and on windows it all works fine).

Here's the output of 'aplay -l':
```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

If anyone can thik of anythig, I'd be more than glad to hear it.

---

### Post by Arthur Archnix on 2008-03-20
Let's drop into alsamixer and reduce the sound output from max. In a terminal type:
```
alsamixer
```
Now drop everything down about 3 bars from maximum, so you're either just in the red or else in the max green. Press 'esc' to exit. And to save these changes type:
```
sudo alsactl store
```
If that doesn't work, just do it again, but turn the volume up this time, to undo the changes. No point in having the volume down some if it doesn't help.

---

### Post by shone zlo on 2008-03-23
It seems that pcm was set to too loud...Tnx man :)

---

### Post by Arthur Archnix on 2008-03-24
cheers

---

