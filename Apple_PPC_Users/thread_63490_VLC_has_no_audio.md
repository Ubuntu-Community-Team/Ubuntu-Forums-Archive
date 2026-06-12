---
title: "VLC has no audio"
date: 2005-09-08
forum: Apple PPC Users
---

### Post by enupnia on 2005-09-08
hi there!

I have a G3 ibook with ubuntu 5.0.4.
everthing seems to work, except fot VLC audio. The video is wonderful, but it has no audio. I tried withe alsa and asd plugins... nothing.

here is the problem it gets:

[00000238] mpeg_audio packetizer: MPGA channels:2 samplerate:44100 bitrate:128
[00000239] mpeg_audio decoder: MPGA channels:2 samplerate:44100 bitrate:128
[00000240] oss audio output error: cannot open audio device (/dev/dsp)
/dev/dsp: Dispositivo o risorsa occupata
[00000240] esd audio output error: cannot open esound socket (format 0x00001021 at 44100 Hz)

---

### Post by enupnia on 2005-09-08
here the answer : 

[http://ubuntuforums.org/showthread.php?t=61386&highlight=vlc+sound](http://ubuntuforums.org/showthread.php?t=61386&highlight=vlc+sound)

---

