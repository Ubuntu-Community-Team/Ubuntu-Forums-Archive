---
title: "Sound Card Issues"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Mular on 2007-12-23
Hey Guys,

Heres the deal I have a Creative Labs SB Audigy LS and onboard sound.

By setting the system > preferences > sound to the SB audigy system sound works great..

The only issues I been having is with wine, for whatever reason it refuses to use my Creative lab card.. I can disable to onboard sound in bios and that fixes the issue but see I also use skype. I like having the second soundcard just for use with skype. Any ideas how to fix this issue with wine?

---

### Post by Xzallion on 2008-01-01
configuring WINE to use the other card should work.

run ```
winecfg
``` and select the audio tab, and tell it to use the sound system that you set your main sound preference to (ALSA, OSS, Jack, Pulse, etc)

Hope that helps.

---

