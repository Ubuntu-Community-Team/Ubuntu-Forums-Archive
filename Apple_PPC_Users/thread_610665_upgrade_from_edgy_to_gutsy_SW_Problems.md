---
title: "upgrade from edgy to gutsy: SW Problems:"
date: 2007-11-12
forum: Apple PPC Users
---

### Post by TeeJunki on 2007-11-12
Hi there,

I upgraded from edgy to feisty and then to gutsy with update-manager. 
Since then, my mouse cursor looks wierd, like the offset for displaying the image of the cursor is set wrong and mplayer won't work anymore.

here is the output from mplayer, when trying to play a normal divX video file:
> 
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
AltiVec found
CPU: PowerPC
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Die Hard 4.0 (Live Free Or Die Hard) DVD Quality [ENG] Carisma99/Die Hard 4.0  (Live Free Or Die Hard) DVD Quality [ENG] [US] By Carisma.mp4.
ISO: File Type Major Brand: ISO/IEC 14496-1 (MPEG-4 system) v2
Quicktime/MOV file format detected.
VIDEO:  [avc1]  720x304  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16be, 102.7 kbit/7.28% (ratio: 12839->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16be (2 bytes per sample)
Starting playback...
[h264 @ 0x10774cf0]AVC: Consumed only 10 bytes instead of 22
[h264 @ 0x10774cf0]AVC: nal size 0
VDec: vo config request - 720 x 304 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x304 => 720x304 Planar YV12 
Illegal instruction

when trying to play an mpeg file the output of mplayer is:

> MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
AltiVec found
CPU: PowerPC
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Road Runner/Road Runner & Wile E Coyote - 11 - Zoom And Bored.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x240  (aspect 12)  29.970 fps  1150.0 kbps (143.8 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16be, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16be (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x240 => 352x270 Planar YV12 
A:   0.3 V:   0.2 A-V:  0.173 ct:  0.003   2/  2 ??% ??% ??,?% 0 0 

MPlayer interrupted by signal 4 in module: decode_video
- MPlayer crashed by an 'Illegal Instruction'.
  It may be a bug in our new runtime CPU-detection code...
  Please read DOCS/HTML/en/bugreports.html.
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


I already tried to purge the config files with apt-get --purge remove mplayer and reinstall mplayer with apt-get install mplayer.


aterm is not transparent either anymore :-(

 aterm -tr +sb -tint blue produces the following output:


> aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x220001A
aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x220001A
aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x220001A
aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x220001A
aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x220001A
aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x220001A


thank you very very much for you help.

---

