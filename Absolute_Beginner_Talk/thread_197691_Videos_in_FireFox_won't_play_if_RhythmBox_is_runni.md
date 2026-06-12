---
title: "Videos in FireFox won't play if RhythmBox is running"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-16
It gets sorta annoying too. I'll be browsing forums or other sites, and when I get a link to Google Video or YouTube that I want to see, I can't hear anything. If I stop my music and close RhythmBox all together it still doesn't work.

---

### Post by Simon Parzer on 2006-06-16
This is a bug in Firefox. If it would use the ALSA device, it wouldn't block the audio device (if there is an ALSA app using the audio device, Firefox can't use it). It could also be the fault of the Macromedia Flash plugin (Google Video and YouTube! use it for video playback).

---

### Post by Amablue on 2006-06-16
So there's nothing I can do about it?

---

