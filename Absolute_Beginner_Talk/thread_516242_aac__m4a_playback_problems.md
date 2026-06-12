---
title: "aac / m4a playback problems"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by nimajiman on 2007-08-02
Hi,

I am having real trouble getting aac / m4a playback to work in ubuntu feisty. I have a few of my movies ripped with aac audio, and some cds also ripped as m4a files, all done through feisty, but i can't get any of them to play back. I have checked, and have "GStreamer plugins for aac, xvid, mpeg2, faad" installed in Add/Remove Applications, and have also checked in synaptic and have gstreamer0.8-faac and gstreamer0.8-faad installed, as well as gstreamer0.10-plugins-bad-multiverse. All of these are there, and aac encoding works fine, but I just can't get anything to play them back. I've tried Amarok, Banshee, and Rhythmbox for audio files and still nothing.

Any ideas? Is there something simple i'm missing?

---

### Post by nimajiman on 2007-08-02
I should add i'm not talking about DRM protected files here - nothing from itunes or anything like that, these are just files I ripped myself through feisty

---

### Post by Alexander2007 on 2007-08-03
> **nimajiman said:**
> Hi,

I am having real trouble getting aac / m4a playback to work in ubuntu feisty. I have a few of my movies ripped with aac audio, and some cds also ripped as m4a files, all done through feisty, but i can't get any of them to play back. I have checked, and have "GStreamer plugins for aac, xvid, mpeg2, faad" installed in Add/Remove Applications, and have also checked in synaptic and have gstreamer0.8-faac and gstreamer0.8-faad installed, as well as gstreamer0.10-plugins-bad-multiverse. All of these are there, and aac encoding works fine, but I just can't get anything to play them back. I've tried Amarok, Banshee, and Rhythmbox for audio files and still nothing.

Any ideas? Is there something simple i'm missing?

AAC encoding in gstreamer0.10 I believe is buggy at the moment (cause I have the same problem), so the files that you encoded are possibly not good. Use another encoder like MP3.

---

### Post by nimajiman on 2007-08-03
> **Alexander2007 said:**
> AAC encoding in gstreamer0.10 I believe is buggy at the moment (cause I have the same problem), so the files that you encoded are possibly not good. Use another encoder like MP3.

Yeah, i thought that may be the case, however the same files that i can't play through ubuntu are readable elsewhere (eg windows). 

Could there be any other reasons?

---

### Post by apb1991 on 2007-08-10
VLC media player will play any unprotected media file.

---

### Post by MenZa on 2007-08-10
> **Alexander2007 said:**
> Use another encoder like MP3.

Or *oggenc*.

---

### Post by logos34 on 2007-08-10
amarok using the xine engine should be able to play just about anything you throw at it.

---

