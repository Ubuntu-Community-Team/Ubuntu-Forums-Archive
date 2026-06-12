---
title: "mencoder problem"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by s.victor on 2007-11-12
I have a problem with mencoder since I installed Gutsy.
I try to record from my TV tuner with the following command, but I get some error. It worked great in Feisty.

```
sevic@sevic-desktop:~$ mencoder tv:// -tv driver=v4l2:input=0:norm=pal:alsa:amode=1:width=640:height=480:outfmt=yuy2:device=/dev/video0 -vf crop=620:460,scale=640:480,pp=lb,pp=de/tn:1:2:3 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2500:keyint=25 -oac mp3lame -lameopts abr:br=96:mode=1 -o /home/sevic/Videos/TV-captures/capture-1.avi
MEncoder 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) 2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Philips Tiger reference design
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = SECAM-DK; 7 = SECAM-L; 8 = SECAM-Lc; 9 = PAL-M; 10 = PAL-Nc; 11 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : STEREO
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
Error opening audio: Device or resource busy
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
Error opening audio: Device or resource busy
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
Error opening audio: Device or resource busy
v4l2: 0 frames successfully processed, 0 frames dropped.
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```

Any help appreciated.

---

### Post by s.victor on 2007-11-14
Bump.

---

### Post by s.victor on 2007-11-27
Bump.

---

### Post by guneza on 2007-11-28
> **s.victor said:**
> Bump.

Hello,

I don't know if this is related to this matter, but i've experienced problems with ALSA due to a bug where pulseaudio locks the sound device.

I found a workaround with Tollef Fog Heen which is as simple as killing pulseaudio with kill or pkill.

Hope this helps!

gustavo

---

