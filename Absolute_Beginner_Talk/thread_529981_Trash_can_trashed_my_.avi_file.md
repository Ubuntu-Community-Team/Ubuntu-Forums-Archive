---
title: "Trash can trashed my .avi file"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-19
I mistakenly threw my .avi file in the trash. I went to the trash can, restored the file to it's original location, but when I try to play it now kaffeine tells me it does not have the appropriate plug in to play this file. All my other .avi files work fine, and so did this one before it went to the trash. Has this ever happened  to you? Do You Have Any ideas how I can fix it. Any help would be appreciated. Thanks.  :confused:

---

### Post by wolfen69 on 2007-08-19
did you try and play it in any other media player?

---

### Post by Hobo Joe on 2007-08-20
Try running it in VLC.

---

### Post by swoll1980 on 2007-08-20
Tried different player. No luck. Tried to play it in the terminal and this was the output I got.

nolan@nolan-desktop:~$ mplayer /home/nolan/jedi.avi
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.60GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/nolan/jedi.avi.
libavformat file format detected.
[tiertexseq @ 0x8817808]Could not find codec parameters (Video: tiertexseqvideo, 256x128)
VIDEO:  []  256x128  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 256 x 128 (preferred colorspace: Packed YUY2)
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 256x128 => 256x128 Packed YUY2
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
A:   0.0 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0

Exiting... (End of file)

---

