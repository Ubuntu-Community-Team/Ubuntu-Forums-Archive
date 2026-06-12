---
title: "SoundJuicer problem ripping to mp3"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by sagibson on 2006-07-13
I'm getting the following error when I try to extract CD-Audio to mp3 using Sound Juicer under Breezy.

The error is Sound Juicer could not extract this CD.  Reason: Could not create GStreamer encoders for mp3.   

I have followed the documentation at [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping) and have gstreamer0.8-lame and gstreamer0.8-mad installed.  

Gstreamer pipeline is set to "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux".  

I am able to rip to an *.ogg format with no problems.

Any ideas?

TIA

---

