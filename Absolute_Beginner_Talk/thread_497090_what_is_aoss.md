---
title: "what is aoss?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by forsberg on 2007-07-09
Laptop: Acer Aspire 3610
Running: Ubuntu 7.04

Problem: Realplayer choppy when playing rmvb files

Solution: Had to install alsa-oss and then modify the config to run "aoss realplay"

So ... what magic does alsa-oss do to get videos running smoothly?

---

### Post by KIAaze on 2007-07-09
I guess it improved the sound decoding and rendering, thereby improving the video.

ALSA is the Advanced Linux Sound Architecture:
OSS is the free version of the Open Sound System.

So both are just for sound theoretically. But if the video has sound it might make sense.

---

### Post by ramjet_1953 on 2007-07-09
A lot of applications are still built around the OSS sound architecture.

However, most distributions now us ALSA.

alsa-oss is a wrapper that gives OSS applications full functionality under ALSA.

Regards,
Roger 8)

---

