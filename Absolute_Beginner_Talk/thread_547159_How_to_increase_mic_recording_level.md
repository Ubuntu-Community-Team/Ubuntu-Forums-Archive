---
title: "How to increase mic recording level?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-09-09
I've increased microphone level to max and checked Mic Boost, but my recording level is still way too level (checked with Audacity and playback).  How do I increase mic recording further?

---

### Post by Majorix on 2007-09-09
You mean volume?
```
alsamixer
```

---

### Post by AncientPC on 2007-09-09
No, I mean microphone recording level.  It is already maxed out in the mixer.

---

### Post by tgalati4 on 2007-09-09
Many pc microphones expect a 5VDC drive signal to come from the microphone port.  If you are using something other than a cheapo pc headset microphone, then it may not be wired to accept a 5VDC driver signal.  Without the 5VDC drive or using a microphone without a built-in preamp, you may never get enough microphone signal.

If you are using an XLR microphone, then it will usually need a preamp, (with or without phantom power) to get a decent recording level.

Cheap microphones with an 1/8" mini stereo jack usually accept a 5VDC drive signal.  Radio Shack mics with a 1/8" mono jack (only tip and sleeve) won't accept a 5VDC drive signal.

In that case you will need a preamp and then run it through the Line-in port or the microphone port (with boost off).

---

