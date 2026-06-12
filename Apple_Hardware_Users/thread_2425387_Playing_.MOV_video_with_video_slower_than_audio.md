---
title: "Playing .MOV video with video slower than audio"
date: 2019-08-25
forum: Apple Hardware Users
---

### Post by davide3 on 2019-08-25
Hi all,
 I'm playing a .MOV video on my ubuntu computer.
If I watch the video (no matter with which palyer) I found I'm listening to a regular audio stream, but the video streaming is very slow!

Video details:
```

General
Complete name                            : 15Take.MOV
Format                                   : MPEG-4
Format profile                           : QuickTime
Codec ID                                 : qt   0000.00 (qt  )
File size                                : 5.47 GiB
Duration                                 : 3 min 48 s
Overall bit rate                         : 206 Mb/s
Movie_More                               : FUJIFILM DIGITAL CAMERA X-T3
Encoded date                             : UTC 2019-08-23 11:48:40
Tagged date                              : UTC 2019-08-23 11:48:40
Origin                                   : Digital Camera

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L5.1
Format settings                          : CABAC / 1 Ref Frames
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 1 frame
Format settings, GOP                     : M=1, N=25
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 3 min 48 s
Bit rate                                 : 204 Mb/s
Width                                    : 3 840 pixels
Height                                   : 2 160 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 25.000 FPS
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.982
Stream size                              : 5.40 GiB (99%)
Language                                 : English
Encoded date                             : UTC 2019-08-23 11:48:40
Tagged date                              : UTC 2019-08-23 11:48:40
Color range                              : Full
Color primaries                          : BT.709
Transfer characteristics                 : BT.601
Matrix coefficients                      : BT.601

Audio
ID                                       : 2
Format                                   : PCM
Format settings                          : Little / Signed
Codec ID                                 : lpcm
Duration                                 : 3 min 48 s
Bit rate mode                            : Constant
Bit rate                                 : 2 304 kb/s
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 kHz
Bit depth                                : 24 bits
Stream size                              : 62.6 MiB (1%)
Language                                 : English
Encoded date                             : UTC 2019-08-23 11:48:40
Tagged date                              : UTC 2019-08-23 11:48:40

Other
ID                                       : 3
Type                                     : Time code
Format                                   : QuickTime TC
Duration                                 : 3 min 48 s
Time code of first frame                 : 04:24:24:03
Time code, striped                       : Yes
Language                                 : English
Encoded date                             : UTC 2019-08-23 11:48:40
Tagged date                              : UTC 2019-08-23 11:48:40
Bit rate mode                            : CBR

```

Please, help!

---

### Post by Autodave on 2019-08-25
What version of 'buntu are you using?  Can you give us some specs on your equipment please?

---

### Post by Yellow Pasque on 2019-08-25
```
Movie_More                               : FUJIFILM DIGITAL CAMERA X-T3
```

I'd make sure to have the latest firmware
[https://www.fujifilm.com/support/digital_cameras/software/firmware/x/xt3/download.html](https://www.fujifilm.com/support/digital_cameras/software/firmware/x/xt3/download.html)

---

### Post by Autodave on 2019-08-25
Yellow Pasque: not sure what you are asking or looking for, but this doesn't seem to have anything to do with what the thread started about.  Please start a new thread or explain how your reply fits in with the original.

---

### Post by Yellow Pasque on 2019-08-25
> **Autodave said:**
> Yellow Pasque: not sure what you are asking or looking for, but this doesn't seem to have anything to do with what the thread started about.  Please start a new thread or explain how your reply fits in with the original.

It looks like the OP is trying to play video from a camera, and I'm telling the OP to make sure camera's firmware is up to date.

---

### Post by davide3 on 2019-08-26
> **Autodave said:**
> What version of 'buntu are you using?  Can you give us some specs on your equipment please?

I'm on an early 2008 macbook with:
4.15.0-58-lowlatency #64-Ubuntu SMP PREEMPT
Intel Pentium T8100 dual core duo.
Intel GMA X3100

```
lsb_release -crid
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic

```

Should I convert between Mov and Mp4?

---

### Post by QIII on 2019-08-26
Moved to Apple Hardware Users for a more appropriate fit.

---

