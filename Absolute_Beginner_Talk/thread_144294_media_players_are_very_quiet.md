---
title: "media players are very quiet"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by beej101 on 2006-03-14
I have the following media players installed for ubuntu:

music player, no atun, vlc for gtk+, totem and xmms.  problem is when i load mp3 files or video (i.e. avi) files, the files play but there is no sound.  in the case of avi's there is video but no audio.  is there some driver software or codec i am missing?

sorry if i have too many questions im just excited about ubuntu.
thanks btw

---

### Post by Sutekh on 2006-03-14
MP3 is not a 'free' format so to get support to play them requires a bit of work.

Check out

[Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats)

To get what you need setup.

---

### Post by celloandy on 2006-03-14
Since the files seem to be playing, and you aren't getting complaints of missing codecs, my guess is that the problem isn't that you don't have mp3 support properly configured, though, if you don't, that'll obviously need to be the first step.  After that, run "alsamixer" in a terminal and make sure that important channels ("Master," "PCM," etc.) aren't muted or set to really low volumes.  Can you hear any sound from the machine at all?

Andrew

---

### Post by therunnyman on 2006-03-14
Hi All,

I wonder, beej101, do you have multiple sound devices, like onboard sound and a soundcard?  Make sure you have the proper sound device selected:

>In the GUI, double click the little speaker icon up by the time and date.
>In the Volume Control window, Click File-->Change Device.
>See if the proper device is selected.

Then check the main and device volumes, same way (slider bars moving up and down in the Volume Control window).

If that doesn't do anything, check the volume in your app.  There's a speaker icon in those GUIs as well.

Hope that helps some.

therunnyman

---

