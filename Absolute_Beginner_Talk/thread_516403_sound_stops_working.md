---
title: "sound stops working"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by z3phyr on 2007-08-03
hey there
i have a giga-byte ac'97 sound card? the sound works fine most of the time but it keeps turning off from time to time. for example i would be streaming a movie. then i would pause and watch some youtube then after when i get back to the movie all the sound stops working. i would try playing some movies in mplayer it would give me the error cant initialise sound device... when i try testing the card in sound preferences i would get the error audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available. usually a restart solves the problem but this is getting annoying.

any suggestions appreciated
cheers

---

### Post by hoges on 2007-08-03
It sounds like it can only use one sound source at a time, and it's interfering with on another. Does it happen if you play the movies on their own ie instead of pausing, exiting the program and then go to youtube?

Also, check the sound properties. I've seen in the past that mine sometimes likes to change the sound device, and as such tries to play them through a different output.

---

### Post by z3phyr on 2007-08-03
i dnt exactly remember wat the circumstances were when it happens but i'm sure i'm able to play like avi files n streaming movies etc at the same time without a problem. remember the first couple of times it happened i would mess around with the sound properties in mplayer and volume control. it shows two devices in there. sis7012 (alsa mixer) and realtek alc655 rev 0 (oss mixer). is that normal? anyway i would mess with them and eventually sound came back. not sure what it was exactly because i probably did the same thing over and over, changing the sound devices.

---

### Post by atomkarinca on 2007-08-03
when that happens try typing these in the terminal:

```
sudo killall alsa
sudo killall osd
sudo killall esd
```

---

