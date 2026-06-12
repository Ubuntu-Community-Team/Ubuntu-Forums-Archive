---
title: "My audio sucks"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-06-01
Okay, so I just got done installing VLC media player (which comes with all the codecs I need), but whenever I play an mp3, it sounds really crappy. It sounds like the equalizer is on some crappy setting, and there's this annoying staticy type popping sound (I don't know how to explain it). What can I do to resolve this problem?

I'm also running Xubuntu 7.04 if that helps at all.

---

### Post by brooksbp on 2007-06-01
You should post your hardware specs and what sound driver/interface you're using (ALSA/OSS/etc...). I had a similar problem on an old laptop and found out that my audio processing was being offloaded to the CPU which was in turn producing horrible sound.

---

### Post by Exershio on 2007-06-01
My hardware specs:

Intel p4 2.0ghz processor
256mb ram
Xubuntu 7.04
onboard video
onboard sound

I don't know what sound driver I have. On Windows XP, I used SoundMAX Audio.

---

### Post by brooksbp on 2007-06-01
System -> Preferences -> Sound

If it's on autodetect, manually select a driver (most likely ALSA or OSS) and test them to see which ones work and produce the horrible sound.

---

### Post by Exershio on 2007-06-01
I found a solution in this thread: [http://ubuntuforums.org/showthread.php?t=431284](http://ubuntuforums.org/showthread.php?t=431284)

Thanks a ton for helping, I appreciate it.

---

