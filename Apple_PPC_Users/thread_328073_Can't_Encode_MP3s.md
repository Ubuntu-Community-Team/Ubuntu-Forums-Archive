---
title: "Can't Encode MP3s"
date: 2006-12-30
forum: Apple PPC Users
---

### Post by Uta on 2006-12-30
I have Dapper installed on my G4 power mac, this Ubuntu install seems very stable but I am not able to encode mp3 via Sound Juicer. Where and what encoders do I need?
I set up a profile in SJ with the following info:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux

Could someone tell me "exactly" what gstreamer plugin I need, where to get it and where to check to see if I have it installed. Thanks!

---

### Post by studiesrule on 2006-12-30
can you play mp3?
get the gstreamer-ugly package to play.
I'm not 100% sure about encoding though. Check out ogg vorbis though. It's has pretty wide support and is miles ahead of mp3 (take the sound test).

---

### Post by Uta on 2006-12-30
Yes I can play mp3s and have already installed the "ugly package".
The reason I want the mp3 encoding option is due to my old iPod that only loads mp3s.

---

### Post by ivelasco on 2006-12-30
Give a try to grip it is a very good choice

---

### Post by Uta on 2006-12-30
Ok, I installed grip, but where is the "lame encoder"
Where do you get the encoder? Thanks.

---

### Post by 3rdalbum on 2006-12-30
```
sudo apt-get install lame
```

Once you do that, and assuming that gstreamer0.8-lame is installed, your Gstreamer pipeline should work.

---

### Post by Uta on 2006-12-31
First thanks for the help, but the encoded files produced by Sound Juicer are not playable.
This is GStreamer pipe setting I am using:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux
This does produce a MP3 file but it's not playable.
My Edgy install can play MP3s. I have copied an mp3 off my iPod and the system plays it without issue, but the mp3 files I create from SJ do not play?
Am I using the wrong GStreamer pipe setting in my perferences?
Thanks!

---

