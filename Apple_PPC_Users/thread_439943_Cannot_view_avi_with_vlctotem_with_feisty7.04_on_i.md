---
title: "Cannot view avi with vlc/totem with feisty/7.04 on ibook G3"
date: 2007-05-11
forum: Apple PPC Users
---

### Post by ds9 on 2007-05-11
Hi,

I just reinstalled my ibook G3 (iBook 2 rev. 2) running previously dapper.
With feisty I cannot view any avi files (not only divx ones) with vlc or totem/gstreamer.
(though I've installed the codecs/plug-ins as proposed)

With vlc a window starts appearing and then vanishes (vlc cores dumps)
 VLC media player 0.8.6 Janus
Instruction illégale (core dumped)

Am I the only one ? :confused:

---

### Post by ds9 on 2007-05-13
> **ds9 said:**
> Hi,

I just reinstalled my ibook G3 (iBook 2 rev. 2) running previously dapper.
With feisty I cannot view any avi files (not only divx ones) with vlc or totem/gstreamer.
(though I've installed the codecs/plug-ins as proposed)

With vlc a window starts appearing and then vanishes (vlc cores dumps)
 VLC media player 0.8.6 Janus
Instruction illégale (core dumped)

Am I the only one ? :confused:


I think that the issue is in libavcodec.so.0d .
Can anybody confirm some avi/divx viewing issues ?

I compiled vlc (from official tarball) with debug and faced the samed issues.

[00000275] fb video output error: cannot get terminal mode (Invalid argument)
Instruction illégale (core dumped)


gdb told me :

```
Program terminated with signal 4, Illegal instruction.
#0  0x0f389258 in ff_er_frame_end () from /usr/lib/libavcodec.so.0d
(gdb) bt
#0  0x0f389258 in ff_er_frame_end () from /usr/lib/libavcodec.so.0d
#1  0x0f3b8f88 in ff_h263_decode_frame () from /usr/lib/libavcodec.so.0d
#2  0x0f27de88 in avcodec_decode_video () from /usr/lib/libavcodec.so.0d
#3  0x0f7f6b88 in DecodeVideo__0_8_6 (p_dec=0x101b3390, pp_block=<value optimized out>) at video.c:518
#4  0x10078d40 in DecoderDecode (p_dec=0x101b3390, p_block=0x102894e8) at input/decoder.c:721
#5  0x10078f84 in DecoderThread (p_dec=0x101bed80) at input/decoder.c:494
#6  0x0ffa37e4 in start_thread () from /lib/libpthread.so.0
#7  0x0fe26124 in clone () from /lib/libc.so.6
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
```

---

### Post by trash on 2007-05-13
same here, i've been able to get avi's playing with gxine using the xine-ffmpeg plugin.

avi's won't play in mplayer and totem either, yet dvd's play fine.

---

### Post by siman on 2007-05-21
same here, vlc and totem just crash after opening - does anybody know how to file / search for a related bug?

---

