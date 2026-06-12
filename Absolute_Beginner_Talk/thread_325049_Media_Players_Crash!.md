---
title: "Media Players Crash!"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by ishift on 2006-12-24
i seem to be running into a lot of hiccups lately.

here's one of them...

i'm trying to run a dvix avi file. i've tried mplayer and vlc. both crash. here's mplayer's output:

```
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Model: 8, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /home/shift/transformers.480p.divx.avi.
AVI file format detected.
VIDEO:  [DX50]  720x304  24bpp  23.976 fps  1297.4 kbps (158.4 kbyte/s)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
alsa-init: using device default
alsa-lib: confmisc.c:560:(snd_determine_driver) could not open control for card 0
alsa-lib: conf.c:3477:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
alsa-lib: conf.c:3477:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
alsa-lib: confmisc.c:955:(snd_func_refer) error evaluating name
alsa-lib: conf.c:3477:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
alsa-lib: conf.c:3946:(snd_config_expand) Evaluate error: No such file or directory
alsa-lib: pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
alsa-init: playback open error: No such file or directory
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
alsa-init: using device default
alsa-lib: confmisc.c:560:(snd_determine_driver) could not open control for card 0
alsa-lib: conf.c:3477:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
alsa-lib: conf.c:3477:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
alsa-lib: confmisc.c:955:(snd_func_refer) error evaluating name
alsa-lib: conf.c:3477:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
alsa-lib: conf.c:3946:(snd_config_expand) Evaluate error: No such file or directory
alsa-lib: pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
alsa-init: playback open error: No such file or directory
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/shift/.kde/socket-shift-laptop.
can't create mcop directory

```

here's vlc's output:

```
VLC media player 0.8.6 Janus
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3477:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3477:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3477:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3946:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
[00000345] oss audio output error: cannot open audio device (/dev/dsp)
Creating link /home/shift/.kde/socket-shift-laptop.
can't create mcop directory

```

what seems to be the problem? thanks in advance.

---

### Post by MkfIbK7a on 2006-12-24
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
> Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
try to get this codec
otherwise completelt remove mplayer then reinstall it in synaptic

---

### Post by myddewji13 on 2008-02-07
i got the same prrob...no matter what i i do...including reinstall divx causes a crash in anythin i try to us..

---

