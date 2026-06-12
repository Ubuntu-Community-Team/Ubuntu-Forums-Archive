---
title: "Mplayer could not open audio device..."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by staib on 2007-05-13
If anyone can point me in the right direction I would be very grateful.

Am now running Ubuntu 7.04 fine (with a splash of Beryl every now and then!) but my generic soundblaster compatible sound card is being a pain to set up properly.

These things do work:  start-up and system sounds, playing back music (in Rythmbox and Kaffeine), playing YouTube and Google vids.

But I cannot get sound to work with MPlayer - which reports 'Could not open/initialize audio device - no sound.'

Any help appreciated!   Nick

---

### Post by mejy on 2007-05-13
Do you get any strange output when running it from the terminal?  Also, in your mplayer preferences, make sure alsa is selected on the sound tab.  You could also try selecting OSS instead, which is more likely to work but will cut off sound from other applications when playing.

---

