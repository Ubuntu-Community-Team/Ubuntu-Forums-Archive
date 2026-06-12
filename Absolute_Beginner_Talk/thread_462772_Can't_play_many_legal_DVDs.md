---
title: "Can't play many legal DVDs"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-06-03
Hello,

I have problem with playback of legal DVDs, many of them don't work at all. Can anyone tell me where can I download the newest libdvdcss2 to be able to watch these movies? 

Thanks in advance.

---

### Post by jonward0690 on 2007-06-03
Well here is the link.  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by pappapump on 2007-06-03
kudos jonward0690

---

### Post by O-pos on 2007-06-03
Thanks, I installed this one:  1.2.9/  11-Jul-2005 20:42
 the DVDs I had problem with still do not work. here is the output:

```
 $ mplayer dvd://
MPlayer dev-SVN-r22974-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.50GHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
There are 13 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000139
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00021308
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00021346
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0003a9db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003a7c24
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (stereo) language: unknown aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
A:   0.4 V:   0.3 A-V:  0.085 ct:  0.008   2/  2 ??% ??% ??,?% 0 0 

Exiting... (End of file)
 
```

---

### Post by hyper_ch on 2007-06-03
You miss a few codecs it seems...

Run this from the terminal:

```

sudo aptitude install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

```

---

### Post by pappapump on 2007-06-03
Read their step by step guide.
Also look at the faq section, mine are playing fine.

---

### Post by O-pos on 2007-06-03
they just say to install libdvdcss2. I reinstalled it as they describe step-by-step but nothing changed.

---

### Post by hyper_ch on 2007-06-03
```

The selected video_out device is incompatible with this codec.

```

---

### Post by O-pos on 2007-06-03
So what's the solution?

---

### Post by O-pos on 2007-06-03
it seems like a copy protection problem, because vob files copied with vobcopy can be played, but wiht audio problems, video is ok. from the dvd directly there is no playback at all.

---

### Post by hyper_ch on 2007-06-03
You can delete the mplayer from my code but why do you want to isntall mplayer from CVS instead from the repositories???

---

### Post by O-pos on 2007-06-03
> **hyper_ch said:**
> You can delete the mplayer from my code but why do you want to isntall mplayer from CVS instead from the repositories???

Because Mplayer from repositories has audio-video dissociation problems in flv files. Now, I tried this again, but notging did change. However, the files copied by vobcopy are played well. So what should be the reason? both mplayer and vobcopy use the same libdvdcss2, as far as I know.

---

### Post by andrew.46 on 2007-10-19
Hi,

 Saw your dvd troubles:

> **O-pos said:**
> Because Mplayer from repositories has audio-video dissociation problems in flv files. Now, I tried this again, but notging did change. However, the files copied by vobcopy are played well. So what should be the reason? both mplayer and vobcopy use the same libdvdcss2, as far as I know.

 It was my impression that the svn mplayer does *not* need an external libdvdcss or dvd read.

                           Andrew

---

### Post by joe.turion64x2 on 2007-10-19
Assuming everything is in place with the codecs, are there some legal DVDs that can be actually played? or are all of them rejected?

Several months ago I had problems playing an MGM DVD, and since it is the only MGM DVD I have I can not say more. But the laptop can play most of them quite well.

---

### Post by AMDBuntu on 2007-10-19
Or just go to the package manager and install VLC. That program plays DVDs right off the bat.

---

