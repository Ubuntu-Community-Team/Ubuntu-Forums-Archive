---
title: "Convert .ogg to mpeg using mencoder?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Ki11ah on 2007-05-28
I am using GTKrecordmydesktop for making screen casts but need to convert the files to 
mpeg to use on youtube.

I need the little script line for running mencoder in terminal, does anyone have/know it?

Hope that makes sense :)

---

### Post by Ki11ah on 2007-05-28
Just run mencoder help and got this list

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

I am guessing I can't convert to mpeg because the mpeg codec option isn't there?
How do I get the required codecs?

---

### Post by Ki11ah on 2007-05-28
Ok, ran the following in terminal after installing w32 codecs and upgrading sources list...

 mencoder out.ogg -o out.avi -ovc lavc -oac lavc
MEncoder 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x1e3505
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1024x768  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1024x768  fps:15.00  ftime:=0.0667
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 36.7 kbit/5.20% (ratio: 4583->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x887fcb8]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1024 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1024x768 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
[mp2 @ 0x887fcb8]bitrate 224 is not allowed in mp2
Couldn't open codec mp2, br=224.

Exiting...


Why is this failing, what am I missing?

---

### Post by Ki11ah on 2007-05-29
bump

anyone got an answer for this? :)

---

### Post by JeevesBond on 2007-06-25
Did you ever solve the problem? Am seeing the same message when trying to convert from ogg/theora to avi using mencoder.

Unfortunately my installation of ffmpeg can't seem to do this either.

---

### Post by JeevesBond on 2007-06-25
Huzzah! Fixed it. :)

Just add: 
```
-lavcopts abitrate=160
```
to your mencoder command line invocation and all will be well. For instance mine is now:
```
mencoder inputfile.ogg -oac lavc -ovc lavc -lavcopts abitrate=160 -o outputfile.avi
```

Hope this helps you, or someone, in the future. :)

---

### Post by lifeempowered.com on 2007-08-08
Thanks alot!  I needed this!

---

