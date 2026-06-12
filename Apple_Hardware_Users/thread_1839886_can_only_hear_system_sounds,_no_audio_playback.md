---
title: "can only hear system sounds, no audio playback"
date: 2011-09-06
forum: Apple Hardware Users
---

### Post by montchr on 2011-09-06
I just installed Maverick on my MacBook Pro 6-2 yesterday (so I am very new to Ubuntu). I don't think I had this problem when I first installed, but now I can't hear any audio from YouTube videos or music through VLC, for example. However, I do hear Ubuntu's system alert sounds (like the login sound). I even get an audio response when I change the volume with the keyboard buttons. But no audio from media.

I've gone through the whole alsamixer thing, and I've also added

```
options snd-hda-intel model=mbp55
```to alsa-base.conf

What to do?

---

### Post by montchr on 2011-09-06
Ahh nevermind. I installed PulseAudio and that made it clearer.

---

