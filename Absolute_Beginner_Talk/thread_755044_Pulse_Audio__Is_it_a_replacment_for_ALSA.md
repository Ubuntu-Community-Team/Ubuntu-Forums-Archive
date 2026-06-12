---
title: "Pulse Audio?  Is it a replacment for ALSA?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-04-14
I have an older laptop, a Dell Lattidue 300DXT running Xubuntu.  The sounds does not work and has not since day one.  I was in the middle of tryig to get it to work whenI got a diffrent computer that did have sound that worked and I could do a Ubuntu instal, so I did.  I was thinking though that the older laptop would be good for a music player in my room (or some such endevour).  I know Hardy is coming out with Pulse Audio and I was wondering if Pulse is going to be replacing ALSA (which does not support the sound board in this old machine) or is it going to be a pain in the buntu to get it working still?

---

### Post by disturbedite on 2008-04-14
according to wikipedia:
In a typical installation scenario under Linux, the user configures [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") to use a virtual device provided by PulseAudio. Thus, applications using ALSA will output sound to PulseAudio, which then uses ALSA itself to access the real sound card. PulseAudio also provides its own native interface to applications that want to support PulseAudio directly, as well as a legacy interface for ESD applications, making it suitable as a drop-in replacement for ESD.

---

### Post by OZFive on 2008-04-14
So in other works I am in for trouble and some work to get the sound operational.  Not quite the outcome I was hoping for but, it is what it is.  Thanks

---

