---
title: "Playing DVDs without VLC?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by marie-p on 2008-03-01
How can I watch DVDs on my computer without using VLC? 

I tried VLC and it tends to crash in the middle of movies. 

I tried this here: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_DVD_playback_capability) 
but it didn't work.

---

### Post by Crafty Kisses on 2008-03-01
> **marie-p said:**
> How can I watch DVDs on my computer without using VLC? 

I tried VLC and it tends to crash in the middle of movies. 

I tried this here: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_DVD_playback_capability) 
but it didn't work.

Have you tried Totem?

---

### Post by Jose Catre-Vandis on 2008-03-01
Use mplayer

Some useful commands:```
Quickstart DVD playing:
       mplayer dvd://1

       Play in Japanese with English subtitles:
       mplayer dvd://1 -alang ja -slang en

       Play only chapters 5, 6, 7:
       mplayer dvd://1 -chapter 5-7

       Play only titles 5, 6, 7:
       mplayer dvd://5-7

       Play a multiangle DVD:
       mplayer dvd://1 -dvdangle 2

       Play from a different DVD device:
       mplayer dvd://1 -dvd-device /dev/dvd2

       Play DVD video from a directory with VOB files:
       mplayer dvd://1 -dvd-device /path/to/directory/
```

---

