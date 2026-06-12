---
title: "Can't play WMA?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by SonicChao on 2006-09-10
Why can't I play wma? I could a few days ago. I noticed w32codecs wasn't installed, so I installed it BUT STILL can't play .wma ](*,)

---

### Post by rowanparker on 2006-09-10
See [this]("https://help.ubuntu.com/community/RestrictedFormats").


Did you install/remove anything that is audio related?

---

### Post by SonicChao on 2006-09-10
> **rowanparker said:**
> See [this]("https://help.ubuntu.com/community/RestrictedFormats").


Did you install/remove anything that is audio related?

I've seen that wiki page a lot, and installing w32codecs as I said, did nothing.

As for installing/removing audio stuff, I've only installed the k3b MP3 library.

---

### Post by rowanparker on 2006-09-10
That shouldn't break anything.

Try running this from command line:
```
mplayer *filename.wma*
```

What happens now?

---

### Post by SonicChao on 2006-09-10
I heard no sound, but this is what happened:

```

sonicchao@sonicchao-laptop:~/Shared$ mplayer 08\ The\ Call\ of\ Ktulu.wma
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

91 audio & 204 video codecs
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
Playing 08 The Call of Ktulu.wma.
ASF file format detected.
Clip info:
 name: The Call of Ktulu
 author: Metallica
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16002->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...
A:   3.8 (03.7) of 534.0 (08:54.0)  0.8%
alsa-uninit: pcm closed

Exiting... (End of file)
sonicchao@sonicchao-laptop:~/Shared$
```

---

### Post by rowanparker on 2006-09-10
And you heard nothing?

And I like you, you like Metallica ;)

---

### Post by Najand on 2006-09-10
Hmm, almost all the time WMA is a problem because it is a close source codec by microsoft and it is not fully supported in Linux.

---

