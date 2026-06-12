---
title: "Ubuntu sound level too low"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by JBA2337 on 2008-04-15
I recently ditched Windows XP Media Center edition, and installed Ubuntu 7.10 on my Toshiba Satellite A105 laptop.So far, I love Ubuntu! 

But  there is one problem that I can't figure out. If I play music with Rhythmbox or Exaile, and also, if I play a video with Totem Movie Player, the sound level from the built-in laptop speakers is extremely low, as compared with Windows XP. The music or voice sound can just barely be heard, even though the master Ubuntu volume control is set at 100%, and the volume controls in the above applications is at 100%.

Does anyone have any idea how I can get some sound out of my laptop speakers?

Thanks!

---

### Post by Inxsible on 2008-04-15
Open a terminal and type in```
alsamixer
```Increase all the volumes to max. The ones that say MM are at mute, so just increase them all to max and see if that works.

---

### Post by JBA2337 on 2008-04-16
Thanks for your suggestion, but that did not help. In Terminal the Alsamixer shows the following icons:

Master current setting: 00   cannot increase
PCM current setting: 100%  can change this setting
MIC current setting:  100%  can change this setting
Caller I current setting: 00   cannot change
Off-Hook current setting: MM cannot change

Any other ideas?

Thanks.

JBA2337

---

### Post by Tom--d on 2008-04-16
Type this in terminal:

```
gnome-volume-control
```

see if there is anything muted in there..

---

### Post by JBA2337 on 2008-04-16
Nope, nothing is muted in gnome-volume-control. All of the sliders are at 100% volume.

Any other ideas?

THank you.

JBA2337

---

