---
title: "No audio - mcop error"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-06-07
Once again - I got no audio

After I installed wine audio seems to be gone.
I tryied to run an mp3 file with mplayer from terminal, and I get this error:

```
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa-init: playback open error: No such file or directory
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/user/.kde/socket-Comp.
**can't create mcop directory**

```

I tryied to "completely remove" wine from sunaptic, but audio still dont work..

---

### Post by J-Gaming on 2006-06-07
Bump :)

---

### Post by J-Gaming on 2006-06-07
After installind KDE (readed somewhere that this helped someone) I get this message:

```
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
mcop warning: user defined signal handler found for SIG_PIPE, overriding
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
[AO SDL] Unable to open audio: No available audio device
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
[AO ESD] esd_open_sound failed: Connection reset by peer
mcop warning: user defined signal handler found for SIG_PIPE, overriding
[AO ARTS] can't connect to aRts soundserver
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)

```

---

