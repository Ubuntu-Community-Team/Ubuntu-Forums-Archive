---
title: "mencoder and qtvideo"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-04-03
Hi!
I'm trying to use mencoder and the qtvideo codec. It isn't working. Here is what I'm executing:

```
mencoder test.ogg -ovc qtvideo -oac mp3lame -o test_new_encoding.avi
```

and here is the output:

```

MEncoder 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x19c1f53d
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1280x976  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1280x976  fps:15.00  ftime:=0.0667
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 499.8 kbit/35.42% (ratio: 62477->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
QuickTime6.3 DLLs found
QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
WARNING! Invalid Ptr handle!

### Searching for QuickTime plugins (*.qtx) at /usr/lib/win32...
### FindNext: AvidQTAVUICodec.qtx
### FindNext: QuickTimeInternetExtras.qtx
### FindNext: BeHereiVideo.qtx
### FindNext: QuickTimeEssentials.qtx
theQuickTimeDispatcher catched -> 0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x87ed738]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1280 x 976 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.31:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 5 -> 4

SwScaler: BICUBIC scaler, from yuv420p to yuyv422 using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
SwScaler: 1280x976 -> 1280x976
Cannot find requested component
FATAL: Cannot initialize video driver.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x6F656874.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...
```


Any ideas?

---

### Post by markekeller on 2008-04-03
It looks as if you are missing a codec that either your input or output file uses.  Do you have ffmpeg installed?

---

### Post by Nutopia on 2008-04-03
Yes, I have ffmpeg installed.

---

