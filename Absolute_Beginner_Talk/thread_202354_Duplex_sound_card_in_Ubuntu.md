---
title: "Duplex sound card in Ubuntu?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by mister_p_1998 on 2006-06-23
Ive got a Soundblaster Ensoniq audiopci sound card that records and plays back at the same time: eg recording internet audio streams. It works fine in XP, but in Ubuntu Dapper, when I try to play an audio stream and record it with audacity, audacity says there is no sound device available. Is it audacity that wont duplex?

---

### Post by pellgarlic on 2006-06-26
you need to check out "jack" if you havn't already:

[http://jackaudio.org/](http://jackaudio.org/)

it's in the repos i think. it basically acts as a "sound server", giving you more control over where the audio signals go. (you should also get "qjackctl" - a gui for jack. very handy - click on the "connect" button once you get it running, and it'll show all available ins and outs of devices and programs that are currently open. )

as it is, those ensoniq's don't seem to play very nice with linux, although some success can be had. think it's just a case of finding the right combination of settings.

home-recording is still a bit of a "starving artist" in the linux world, although there are dedicated groups working hard on it as we speak - check out [http://ubuntustudio.com](http://ubuntustudio.com) and their forum here: [http://ubuntuforums.org/forumdisplay.php?f=128](http://ubuntuforums.org/forumdisplay.php?f=128) 

there are also several music-recording-and-production-oriented linux distros kicking about, like dynebolic, demudi, and so on.

you could also go here: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix) and read up about your card a bit. (alsa comes by default with dapper)

---

