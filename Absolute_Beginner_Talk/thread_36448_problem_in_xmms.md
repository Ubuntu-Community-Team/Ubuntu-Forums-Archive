---
title: "problem in xmms"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by animesh on 2005-05-23
hi 
  i am recieving following error on trying to play a song(mp3) in xmms
   
  arts_init error: loading the aRts backend "/usr/lib/libartscbackend.la" failed

please help me

---

### Post by JonahRowley on 2005-05-23
It's trying to use arts as backend.  If you're running gnome, this is probably not what you want.  Change **Options -> Preference -> Output Plugin** to either eSound or ALSA.  If you have a hardware mixer on your sound card, ALSA would be the better choice, else use eSound.  OSS will also work, but since ALSA does the OSS emulation, it's not very useful.

---

