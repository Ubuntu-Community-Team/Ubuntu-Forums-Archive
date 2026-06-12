---
title: "Ubuntu not playing DVDs, playing Youtube videos in slo-mo, not recognizing VCDs"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-04
My laptop is 10 GB HD, celeron 433 mhz chip, RAM 288 MB [at 100 mhz], and I use Ubuntu 7.04

I have downloaded EVERYTHING I could find to enable Ubuntu 7.04 to be able to play VCDs and DVDs:

MPlayer
VLC media player
"Ubuntu restricted extras"
libdvdcss2, libdvdplay, libdvdnav, and libdvdread
w32 codecs

Ubuntu 7.04 recognizes DVDs fine, although it does not play them properly. And when I go to Youtube on the web, it plays back videos in slo-motion only. The sound is normal, but the videos play haltingly and only selecting certain frames, skipping many to go to the next frame.

As for VCD's, Ubuntu doesn't even see that there is a disc in the drive.

I know my computer is capable of handling video in both DVD and VCD form, because  both run fine in Win 98 which I have as a dual boot.

Any suggestions? I've been struggling with this for over a month, and quite frankly am sick of the problem. Do you think it may be something related with the fact that my chip is an older, slower one (celeron 433), or do I still have a hitch in the software. Maybe I should just delete ALL the video files I have including the applications and the codecs, and try loading it all over again. What do you think? Or is it that I am still missing some critical codec that I could load and everything will be proper???

---

### Post by pay on 2007-06-04
Try playing it with mplayer in the command line and see if it comes up with an error. ```
mplayer dvd://*<track>* [-dvd-device *<device>*]
```example```
mplayer dvd://1 -dvd-device /dev/hdc
```

---

### Post by orange2k on 2007-06-04
You might try to install the video and audio codecs via Automatix2.
Thats how I did it - and Automatix installs quite a few codecs all in one step...

(I know that it is not officially supported and all, but I speak from my own experience - it simply works...)

---

### Post by viciouslime on 2007-06-04
I think this is almost certainly a hardware issue. I am VERY surprised that that hardware works fine under windows. A 433MHz processor is pretty slow for playing back DVDs anyway, but a Celeron too...

Unless you have some sort of video card in the laptop that is doing the work for you under windows but the linux driver can't use the hardware acceleration available?

---

### Post by swarup on 2007-06-04
> **viciouslime said:**
> I think this is almost certainly a hardware issue. I am VERY surprised that that hardware works fine under windows. A 433MHz processor is pretty slow for playing back DVDs anyway, but a Celeron too...

Unless you have some sort of video card in the laptop that is doing the work for you under windows but the linux driver can't use the hardware acceleration available?

I don't have any sort of hardware acceleration. When I boot up to Win 98, I just play everything with no problem. For example, I have a set of 30 VCDs that I use to study Sanskrit with. They are videos, and they play beautifully in Win 98 using the DVD player it has. But Ubuntu doesn't even recognize the VCD in the drive.

---

### Post by viciouslime on 2007-06-04
> **swarup said:**
> I don't have any sort of hardware acceleration. When I boot up to Win 98, I just play everything with no problem. For example, I have a set of 30 VCDs that I use to study Sanskrit with. They are videos, and they play beautifully in Win 98 using the DVD player it has. But Ubuntu doesn't even recognize the VCD in the drive.

Ah, well VCDs would be different, much lower bitrate and so much less power required. It does seem odd that they aren't even recognised though. They should at least playback but stutter if it was just that your system wasn't powerful enough...

Normally I would just recommend VLC, failing that mplayer... but you've tried both of those. I'm really not sure :(

---

### Post by swarup on 2007-06-04
> **viciouslime said:**
> Ah, well VCDs would be different, much lower bitrate and so much less power required. It does seem odd that they aren't even recognised though. They should at least playback but stutter if it was just that your system wasn't powerful enough...

Normally I would just recommend VLC, failing that mplayer... but you've tried both of those. I'm really not sure :(

I can also play DVDs in my Win 98. There is sometimes a hint of a stutter or a slight blurring of a screen, but for the most part they do fine. 

Whereas in Ubuntu, the DVDs don't play, the VCD's aren't recognized, and Youtube plays in slow motion. It seems to me that something about the software isn't set up right. ...more than just a symptom of a slow chip. But what can be done to diagnose the problem? Can I delete all my video software and codecs (listed in my 1st posting) and reload them? Do people think that would be the best approach?

---

### Post by viciouslime on 2007-06-04
> **swarup said:**
> I can also play DVDs in my Win 98. There is sometimes a hint of a stutter or a slight blurring of a screen, but for the most part they do fine. 

Whereas in Ubuntu, the DVDs don't play, the VCD's aren't recognized, and Youtube plays in slow motion. It seems to me that something about the software isn't set up right. ...more than just a symptom of a slow chip. But what can be done to diagnose the problem? Can I delete all my video software and codecs (listed in my 1st posting) and reload them? Do people think that would be the best approach?

Perhaps the win98 software being used is simply more efficient? Still doesn't explain the VCDs though...

---

### Post by viciouslime on 2007-06-04
Just found this:

[http://ubuntuforums.org/showthread.php?t=442539]("http://ubuntuforums.org/showthread.php?t=442539")

---

### Post by swarup on 2007-06-04
> **viciouslime said:**
> Just found this:

[http://ubuntuforums.org/showthread.php?t=442539&highlight=vcds&page=2]("http://ubuntuforums.org/showthread.php?t=442539&highlight=vcds&page=2")

I clicked on the link, but it just brought me to the Ubuntu forums directory page. How do I get to the page you had in mind?

---

### Post by viciouslime on 2007-06-04
> **swarup said:**
> I clicked on the link, but it just brought me to the Ubuntu forums directory page. How do I get to the page you had in mind?

Try it now :)

---

### Post by swarup on 2007-06-04
> **viciouslime said:**
> Just found this:

[http://ubuntuforums.org/showthread.php?t=442539]("http://ubuntuforums.org/showthread.php?t=442539")

The above link is to the below instruction for getting Ubuntu to recognize a VCD and Mplayer to play it:

> **Kingsley said:**
> Open up your terminal and type
```
mplayer -zoom vcd://2
```

You may need to replace vcd://2 with vcd:// or vcd://1

I am also having the same problem--my Ubuntu 7.04 does not recognize any VCD in the drive. It recognizes DVDs, but not VCDs.  I have Totem, Mplayer, and VLC, but none will even attempt to play a VCD because as far as the computer is concerned there is no media in the drive. 

I tried the above command, three times as per your instructions: once ending in "2", once ending in "1", and once ending in nothing (just vcd://). It opened the mPlayer screen when I used "2", but wouldn't play anything. With the other two options the Mplayer screen briefly flashed open and then closed. Here below is the terminal readout from each of the three tries. Can someone tell me what it all means, and what I should do to get VCDs playing. Thanks!
------------------------------------------------------------------------------------------------------------------

terminal printput from typing "mplayer -zoom vcd://2"

swarup@swarup-laptop:~$ mplayer -zoom vcd://2
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron A Mendocino/Pentium II Dixon (Family: 6, Model: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://2.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:18:67  mode: 3
track 03:  adr=1  ctrl=4  format=2  28:06:15  mode: 3
MPEG-PS file format detected.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1150.0 kbps (143.8 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
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
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x288 => 376x288 Planar YV12  [zoom]
A:   0.7 V:   0.9 A-V: -0.150 ct:  0.022  15/ 15 168% 77% 44.4% 5 0 


----------------------------------------------------------------------
terminal printput from typing "mplayer -zoom vcd://"

swarup@swarup-laptop:~$ mplayer -zoom vcd://
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron A Mendocino/Pentium II Dixon (Family: 6, Model: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:18:67  mode: 3
track 03:  adr=1  ctrl=4  format=2  28:06:15  mode: 3
libavformat file format detected.
LAVF_header: av_open_input_stream() failed
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Creating new registry
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2  [zoom]
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)

--------------------------------------------------------------------------------------------

terminal printout with typing "mplayer -zoom vcd://1"

swarup@swarup-laptop:~$ mplayer -zoom vcd://1
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron A Mendocino/Pentium II Dixon (Family: 6, Model: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://1.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:18:67  mode: 3
track 03:  adr=1  ctrl=4  format=2  28:06:15  mode: 3
libavformat file format detected.
LAVF_header: av_open_input_stream() failed
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2  [zoom]
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)

---

