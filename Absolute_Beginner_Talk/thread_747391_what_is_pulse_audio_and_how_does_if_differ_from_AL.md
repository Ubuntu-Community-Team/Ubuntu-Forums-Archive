---
title: "what is pulse audio and how does if differ from ALSA?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-04-06
Hi
I read that 8.4 will come with pulse audio, is it a different sound engine?

does it means that ALSA and OSS will go away when we update our 7.10 to 8.4 the old sound system and configuration will vanish?

Thanks

---

### Post by Frak on 2008-04-06
Alsa and Alsa-Oss will still be there. Pulse Audio uses ALSA to configure itself. As I learned, anything going through Alsa will most likely be routed over to pulse audio to be played.

---

### Post by Martje_001 on 2008-04-06
You can read more about it here:
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

