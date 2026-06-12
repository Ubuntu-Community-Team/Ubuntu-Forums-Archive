---
title: "WMV on feisty"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by phelixnyc on 2007-04-19
I just installed feisty and am having problems viewing wmv files online as well as dvd's. I used automatix2 for feisty to install codec's. I did not have this problem with edgy. Where do I start to fix this problem?

---

### Post by igknighted on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Although it hurts me to aid a mets fan :)

---

### Post by phelixnyc on 2007-04-19
Thanx. Let's go Mets!!!!

---

### Post by s9am_me on 2007-04-19
I installed VLC player and it played WMV, MP3's, WAV's, AVI's, ect out of the box

---

### Post by phelixnyc on 2007-04-19
Thanx. I have as well (installed VLC) but when I visit sites with wmv videos I cant play them.

---

### Post by s9am_me on 2007-04-19
I had the same problem before too.. I found there's a extention for firefox that you can launch VLC when it detects video files.. worked for me..[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
give it a try and if it works

---

### Post by Topper_H on 2007-04-20
I confirm there's a problem with some wmv files in Feisty. I upgraded yesterday and now some files play crippled in Kaffeine. 
I have everything up to date even with the medibuntu repo.
I think it's a Xine backend problem because those files play fine in Mplayer though, but not in Kaffeine and Codeine. The video thumbnails generation which depends on Xine is crippled too. :( :( :(

---

### Post by sojyujai on 2007-04-21
I've been having similar problems getting wmv files to play in Totem and think I found a fix - at least it seems to be working for me, hopefully this will help someone else...

It does seem to be a problem with the xine backend.  Using synaptic I switched from totem-xine to totem-gstreamer.  

This allowed my wmv files to play but horribly messed up the colour of all video playback - this seems to be a common problem with totem-gstreamer.  To fix the colour issue I opened /usr/bin/gstreamer-properties - and switched the video default output plugin to 'X Windows System (No Xv)'.  This seemed to fix it - wmv's now playback and the colour is correct.

One final problem I haven't fixed yet - now when I double-click wmv files in Nautilus, Totem will open and immediately crash.  If I open Totem first and drag & drop the wmv into it, it will play fine.
______
edit: the double-click problem seems to have cleared itself up with a reboot.

---

### Post by Topper_H on 2007-04-21
For those concerned : [https://bugs.launchpad.net/xine-lib/+bug/108453](https://bugs.launchpad.net/xine-lib/+bug/108453)

---

### Post by Topper_H on 2007-05-07
Ok it seems that since Feisty, the Xine backend uses ffmpeg to natively decode WMV. However ffmpeg is too slow or buggy and drops a lot of frames.
So I installed w32codecs and edited ~/.xine/config to prioritize w32codec over ffmpeg :

engine.decoder_priorities.win32a:5
engine.decoder_priorities.win32v:5

Kaffeine plays wmv fine now, my wmv thumbnails are fine too  !

---

### Post by schorsch on 2007-05-10
> **Topper_H said:**
> Ok it seems that since Feisty, the Xine backend uses ffmpeg to natively decode WMV. However ffmpeg is too slow or buggy and drops a lot of frames.
So I installed w32codecs and edited ~/.xine/config to prioritize w32codec over ffmpeg :

engine.decoder_priorities.win32a:5
engine.decoder_priorities.win32v:5

Kaffeine plays wmv fine now, my wmv thumbnails are fine too  !

For those people using kaffeine: The file to edit is ~/.kde/share/apps/kaffeine/xine-config ...... but this solution works fine for me, too!

---

