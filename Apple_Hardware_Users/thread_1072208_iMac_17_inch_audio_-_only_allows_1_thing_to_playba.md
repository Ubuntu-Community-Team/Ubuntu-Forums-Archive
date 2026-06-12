---
title: "iMac 17 inch audio - only allows 1 thing to playback at a time"
date: 2009-02-17
forum: Apple Hardware Users
---

### Post by prands on 2009-02-17
Hi Guys

I need a bit of help please.

I am running Ubuntu 8.10 and running it on my early 2006 17" iMac with 1.83 GHz Intel Duo.

The playback worked from install once I selected the OSS - Open Sound System and the SigmaTel audio mixer. However I can only play one sound at a time, ie. I can't play a song in Rhythm Box at the same time as playing audio from a game or video.

Can anyone suggest a way to get this to change please? I have tried other sound devices listed, but can't get the ALSA devices to work at all, only OSS.

Thanks in advance

Paul

---

### Post by cyberdork33 on 2009-02-17
> **prands said:**
> Hi Guys

I need a bit of help please.

I am running Ubuntu 8.10 and running it on my early 2006 17" iMac with 1.83 GHz Intel Duo.

The playback worked from install once I selected the OSS - Open Sound System and the SigmaTel audio mixer. However I can only play one sound at a time, ie. I can't play a song in Rhythm Box at the same time as playing audio from a game or video.

Can anyone suggest a way to get this to change please? I have tried other sound devices listed, but can't get the ALSA devices to work at all, only OSS.

Thanks in advance

Paul
I am pretty sure that you need to get ALSA working over OSS for everything to work properly. Select the ALSA device and run:
```
alsamixer -c 0
```
and make sure that all the channels are unmuted.

---

