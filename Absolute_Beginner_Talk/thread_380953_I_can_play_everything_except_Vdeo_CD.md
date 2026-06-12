---
title: "I can play everything except Vdeo CD"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by medya on 2007-03-10
I have installed all codecs using Automatix2 , I can play everytihng but I cant play any Video CD, 
niether Totem no VLC play them... what should I do ?

---

### Post by Delvien on 2007-03-10
> **medya said:**
> I have installed all codecs using Automatix2 , I can play everytihng but I cant play any Video CD, 
niether Totem no VLC play them... what should I do ?

DO NOT use Automatix to install anything, it can break your system.

What kind of Video cd? SVCD?

---

### Post by medya on 2007-03-10
no a nomral Video CD , it didnt work before installing automatix either...
-I upgrdaded from dapper to edgy-

---

### Post by Delvien on 2007-03-10
Ok not quite sure i understood you.. 

A Video CD has to be in some kind of format, SVCD, MPEG.

Or did you mean a DVD


saying "Video cd" unfortunately doesnt tell us anything.

More info pls.

---

### Post by tgone on 2007-03-10
> **Delvien said:**
> Ok not quite sure i understood you.. 

A Video CD has to be in some kind of format, SVCD, MPEG.

Or did you mean a DVD


saying "Video cd" unfortunately doesnt tell us anything.

More info pls.

I think I'm having a similar problem...

I have a CD with a SVCD video. I can't figure out how to play it though. Do I need to convert it to AVI? Any ideas?

---

### Post by Toadmund on 2007-03-10
Get VLC, I did, and it works.

---

### Post by tagra123 on 2007-03-10
install vlc and in a terminal type:
[B]
/usr/bin/vlc vcd://[/B]


if you want them to auto play use your gconf editor.

From a terminal type:

gconf-editor

then click on ***desktop, gnome, volume_manager***

look for

**autoplay_vcd_command**

and change the value to:

[B]/usr/bin/vlc vcd://
[/B]

---

### Post by tgone on 2007-03-10
> **Toadmund said:**
> Get VLC, I did, and it works.

I installed VLC. My SVCD has three directories:

ext  
mpeg2
svcd

I've tried using VLC to open the files inside but nothing happens. Is there a certain procedure?

---

### Post by Toadmund on 2007-03-11
Drag and drop file onto the VLC console, I was wondering if you'd have trouble with that.
I did once.

---

### Post by medya on 2007-03-11
I did that I have VLC I play everything with VLC , my video CD is old type Video CDs .
still I it doesnt play none of my Video CDs.

I should mention I have a DVD-ROM and a CD-RW , I put the CD in both of them , none o fthem works.

it reads the files but when I try to play , it wont play .

---

### Post by medya on 2007-03-12
so what should I do?

---

### Post by tagra123 on 2007-03-12
Did you try typing this in a terminal?

```
/usr/bin/vlc vcd://
```

if using a dvd


```
/usr/bin/vlc dvd://
```

---

### Post by tagra123 on 2007-03-12
Post any  output the terminal gives if it doesn't play.

---

### Post by medya on 2007-03-12
> **tagra123 said:**
> Post any  output the terminal gives if it doesn't play.
```

shevin@shevin-desktop:~$ /usr/bin/vlc vcd://
VLC media player 0.8.6 Janus
[00000292] vcd access error: could not read TOCHDR
[00000292] vcd access error: no movie tracks found
[00000289] main input error: no suitable access module for `vcd://'
[00000280] main playlist: nothing to play
[00000302] vcd access error: could not read TOCHDR
[00000302] vcd access error: no movie tracks found
[00000300] main input error: no suitable access module for `vcd://'
[00000280] main playlist: nothing to play
[00000280] main playlist: stopping playback
```

and here is the rsult for the second one
```
shevin@shevin-desktop:~$ /usr/bin/vlc dvd://
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/shevin/.dvdnav/.map'
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000291] dvdread demuxer error: DVDRead cannot open source: /dev/hdc
[00000289] main input error: no suitable access module for `dvd://'
[00000280] main playlist: nothing to play
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/shevin/.dvdnav/.map'
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000303] dvdread demuxer error: DVDRead cannot open source: /dev/hdc
[00000302] main input error: no suitable access module for `dvd://'
[00000280] main playlist: nothing to play

```

---

### Post by tagra123 on 2007-03-12
Looks like vlc isn't recognizing the VCD structure or is unable to read it. 

Is the cd in good condition -- not dirty or badly scratched?

Could it be the cd/dvd player itself?

I wonder if a program like vcdgear could convert the files.

If it does then you could burn a new vcd that might work.

Do you have any videos you could burn onto a new vcd and see if the new vcd works? If the newly created vcd works then you could eliminate the drive as the problem.

Some links that may be helpful.

[http://linuxhelp.blogspot.com/2005/10/how-to-play-vcd-dat-files-using.html](http://linuxhelp.blogspot.com/2005/10/how-to-play-vcd-dat-files-using.html)

[http://linux.about.com/od/linux101/a/desktop06e.htm](http://linux.about.com/od/linux101/a/desktop06e.htm)

[http://bbs.archlinux.org/viewtopic.php?pid=232181](http://bbs.archlinux.org/viewtopic.php?pid=232181)  (Post #4)

[http://www.linuxforums.org/forum/ubuntu-help/70760-still-cant-play-vcds.html](http://www.linuxforums.org/forum/ubuntu-help/70760-still-cant-play-vcds.html)

---

### Post by medya on 2007-03-12
my CDs are all new , and recently been burnt by my laptop .
they work well in windows. I will try ur links....

+ the totem says there is no Plugin to read VCD.

---

### Post by tagra123 on 2007-03-12
In synaptic look and see if

libvcdinfo0 

has been installed, if not try installing that.

Actually, you might try completely unstalling vlc.

Then reinstall vlc

It looks like a library may be missing

Are you using dapper?

---

### Post by Jonam on 2007-03-14
The only VCD player that works for me is gxine _but_ I can't get sound to work (yet). I will probably have to do some investigating as to why not as sound works in the other software that I have running. 

I have Dapper on a Pentium III 866MHz and there are no issues with replay speed or libraries (I have libvcdinfo0 installed). I have only tried standard VCDs but not SVCDs. I have tried all the standard players supplied with Ubuntu (totem etc) and they do not work for one reason or another. 

Hope this helps.

Jonam

---

### Post by panch0 on 2007-03-14
What you need is MPlayer. Install it from multiverse, then run

mplayer vcd://

If you find any problem, run

mplayer -v vcd://

from the console and post the output that gives you.

For a nice MPlayer GUI try KPlayer, it handles video CDs quite nicely.

---

### Post by medya on 2007-03-14
> **tagra123 said:**
> In synaptic look and see if

libvcdinfo0 

has been installed, if not try installing that.

Actually, you might try completely unstalling vlc.

Then reinstall vlc

It looks like a library may be missing

Are you using dapper?

I re-installed libvcd and VLC and in installed mplayer too, still I cant read Video CDs
mplayer says failed to seek.

---

### Post by medya on 2007-03-14
> **Jonam said:**
> The only VCD player that works for me is gxine _but_ I can't get sound to work (yet). I will probably have to do some investigating as to why not as sound works in the other software that I have running. 

I have Dapper on a Pentium III 866MHz and there are no issues with replay speed or libraries (I have libvcdinfo0 installed). I have only tried standard VCDs but not SVCDs. I have tried all the standard players supplied with Ubuntu (totem etc) and they do not work for one reason or another. 

Hope this helps.

Jonam
Hey Jonam Thanks it works !  in installed GXine and it works ...

so so strange, I used to see VCD with totem and VLC even in breezy , and now on a fresh edgy (upgraded from dapper) I just can see VCD from Gxine...why is that ?

---

### Post by Jonam on 2007-03-14
I don't know why only gxine works. When I run Win98, all I have to do is find the .dat file on the VCD and get any player to load it and I can watch VCDs. Some even load the VCD direct similar to gxine. 

In Dapper, pointing to the .dat file using totem or mplayer results in a string of error messages. Anyway, your post has got me interested. I will investigate further and see what I can find.

Jonam

---

### Post by tagra123 on 2007-03-14
Please followup when you find out.

---

### Post by Jonam on 2007-03-14
> **tagra123 said:**
> Please followup when you find out.
No problem -will do though it might be a week or so.

Jonam

---

### Post by panch0 on 2007-03-15
I would like to see the output of

mplayer -v vcd://

---

### Post by medya on 2007-03-16
> **panch0 said:**
> I would like to see the output of

mplayer -v vcd://

here is the result

```
shevin@shevin-desktop:~$ mplayer -v vcd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:                 Intel(R) Celeron(R) CPU 2.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/shevin/.mplayer/codecs.conf'
Reading /home/shevin/.mplayer/codecs.conf: Can't open '/home/shevin/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' 'vcd://'
init_freetype
get_path('font/font.desc') -> '/home/shevin/.mplayer/font/font.desc'
font: can't open file: /home/shevin/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/shevin/.mplayer/input.conf'
Can't open input config file /home/shevin/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 60 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('.conf') -> '/home/shevin/.mplayer/.conf'

Playing vcd://.
get_path('sub/') -> '/home/shevin/.mplayer/sub/'
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:18:59  mode: 3
VCD start byte position: 0x551B8  end: 0x31F714
STREAM: [vcd] vcd://
STREAM: Description: Video CD
STREAM: Author: Albeu
STREAM: Comment: based on the code from ???
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename vcd:// ext: (null)
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
header block 1 size: 0
stream_seek: WARNING! Can't seek to 0x4 !
AVS: avs_check_file - attempting to open file vcd://
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
THIS DOESN'T LOOK LIKE AN MPEG-TS FILE!
TRIED UP TO POSITION 404313, FOUND 0, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=-8
LMLM4 Stream Format not found
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 386  p101: 313 p1B6: 0 p12x: 21 sli: 313 a: 128 b: 13 c: 0 idr: 0 sps: 0 pps: 2 PES: 15  MP3: 923, synced: 0
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 385  p101: 313 p1B6: 0 p12x: 21 sli: 313 a: 128 b: 13 c: 0 idr: 0 sps: 0 pps: 2 PES: 15  MP3: 923, synced: 0
Checking for DV
RAWDV file format detected.
demux_open_rawdv() end_pos 3274516
stream_seek: WARNING! Can't seek to 0x0 !
==> Found video stream: 0
demux_open_rawdv() frame_size: 120000 w: 720 h: 480 dif_seq: 10 system: 1
demux_open_rawdv() seek to 0, size: 120000, dv_dec->frame_size: 120000
==> Found audio stream: 0
demux_open_rawdv() chan: 0 samplerate: 0
stream_seek: WARNING! Can't seek to 0x0 !
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:22  fourcc:0x44535644  size:720x480  fps:29.97  ftime:=0.0334
get_path('sub/') -> '/home/shevin/.mplayer/sub/'
==========================================================================
Opening audio decoder: [libdv] Raw DV Audio Decoder
dec_audio: Allocating 15552 + 65536 = 81088 bytes for output buffer.
Unknown/missing audio format -> no sound
Uninit audio: libdv
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.
FFmpeg's libavcodec audio codec
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x0101fe).
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
get_path('registry') -> '/home/shevin/.mplayer/registry'
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
Trying filter chain: vo
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (720x480->720x480,flags=0,'MPlayer',0x32595559)
VO: [xv] 720x480 => 720x480 Packed YUY2 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 93 for hw scaling
[xv] dx: 0 dy: 0 dw: 720 dh: 512
INFO: Win32/DShow video codec init OK.
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
stream_seek: WARNING! Can't seek to 0x0 !
ds_fill_buffer: EOF reached (stream: video)  
[xv] dx: 0 dy: 0 dw: 720 dh: 512
EOF code: 1    0 ??% ??% ??,?% 0 0 

Uninit video: dshow
Successfully enabled DPMS
vo: uninit ...

Exiting... (End of file)

```

---

### Post by Jonam on 2007-03-16
Here are my results for running a VCD under Ubuntu (see below).

In summary Gxine works the best, Mplayer works but spits out error messages and has to be manually made to show the various .dat files.

Jonam
===========
VCD playback tests in Ubuntu

All players running under Gnome on a PIII 866MHz, Ubuntu Dapper using a commerical movie VCD (works OK in Win98SE and on a regular DVD/ VCD player):

1. Gxine

- Works everytime from the Applications menu. Sound problem was solved by loading libxine-extracodecs. Engine log (messages) is:

```
200 frames delivered, 2 frames skipped, 2 frames discarded
video_out: throwing away image with pts 1241802 because it's too old (diff : 4104).
video_out: throwing away image with pts 1238202 because it's too old (diff : 7704).
xine: found demuxer plugin: DVD/VOB demux plugin
xine: found input plugin  : Video CD plugin with PBC and support for: (X)VCD, (X)SVCD, HQVCD, CVD ... 
xine: found demuxer plugin: Elementary MPEG stream demux plugin
xine: found input plugin  : file input plugin
```

2. Xine

2.1 Working from Apps menu
- Never works when started from the Applications menu. Always comes up with an error message that says it could not find the demuxer for the file type.

2.1 Starting from the command line
$ xine -V xv --verbose vcd://

- Xine recognises the VCD but does not play it. Everytime I press the play button on the gui, I get the following messages:

```
gui_xine_open_and_play():
        mrl: 'file:/usr/share/xine/skins/xine-ui_logo.mpv',
        sub 'NONE',
        start_pos 0, start_time 0, av_offset 0, spu_offset 0.
xine: found input plugin  : file input plugin
ebml: invalid EBML ID size (0x0) at position 1
ebml: invalid master element
xine: found demuxer plugin: Elementary MPEG stream demux plugin
av_offset=0 pts
spu_offset=0 pts
```

The screen briefly flashes a 00:00:00 timecode and then stops. Don't know what to do to fix it.

3. Totem

3.1. Totem (Gstreamer based) running from command line
$ totem vcd://
- Does not read VCD but displays error message:

```
Totem could not play 'vcd://'.
No URI handler implemented for "vcd".
```

3.2. Totem (Xine based) running from command line
$ totem vcd://
- Finds VCD but does not play (grey screen) and eventually crashes

4. Mplayer

4.1. From the Applications menu
- Displays error message:

```
ioctl dif1: Invalid argument
```

Plays the intro copyright sequence (track 1) and then stops. You have to press the track skip key to get the movie running (track 2). Works fine but again displays error message at start.

4.2. From command line
$ mplayer vcd://

- Starts up and exits before a single frame is shown
- A very long output file as medya above has listed

==========

---

### Post by panch0 on 2007-03-16
> **medya said:**
> here is the result

OK, it seems it can read the VCD, you just need to tell it to play track number 2. Try this:

mplayer -v -identify vcd://2

and post the output you get.

> **Jonam said:**
> $ mplayer vcd://

- Starts up and exits before a single frame is shown
- A very long output file as medya above has listed

Post your output also, but give -v and -identify options to MPlayer.

---

### Post by medya on 2007-03-16
by the way , jonam is your drive a DVD-ROM or a CD-ROM ?
mine is DVD-ROM ASUS  , I suspect it be because of my Drive.... because it doesnt read many DVDs ...too . (the dvd are well burnt and are ok , it just doesnt read some kind of DVDs....)

---

### Post by medya on 2007-03-16
> **panch0 said:**
> OK, it seems it can read the VCD, you just need to tell it to play track number 2. Try this:

mplayer -v -identify vcd://2
.

hey panch  it works , but it is too annoying , that each time we type it in terminal, isnt it?

---

### Post by Jonam on 2007-03-16
Well, I tried mplayer -v -identify vcd://2 and all I got was the intro copyright track running. I am using CD-RW (Creative) and CD-ROM (Sony) drives in my PC to do the playback. Here is the output of the above command:

```
$ mplayer -v -identify vcd://2
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/mvr/.mplayer/codecs.conf'
Reading /home/mvr/.mplayer/codecs.conf: Can't open '/home/mvr/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: 91 audio & 204 video codecs
CommandLine: '-v' '-identify' 'vcd://2'
init_freetype
get_path('font/font.desc') -> '/home/mvr/.mplayer/font/font.desc'
font: can't open file: /home/mvr/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/mvr/.mplayer/input.conf'
Can't open input config file /home/mvr/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 59 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('2.conf') -> '/home/mvr/.mplayer/2.conf'
Playing vcd://2.
get_path('sub/') -> '/home/mvr/.mplayer/sub/'
ID_VCD_START_TRACK=1
ID_VCD_END_TRACK=3
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 32
track 02:  adr=1  ctrl=4  format=2  00:27:00  mode: 32
ID_VCD_TRACK_1_MSF=00:25:00
track 03:  adr=1  ctrl=4  format=2  01:12:30  mode: 32
ID_VCD_TRACK_2_MSF=00:45:30
ID_VCD_TRACK_3_MSF=71:52:20
VCD start byte position: 0x47CF34  end: 0xC08E38
STREAM: [vcd] vcd://2
STREAM: Description: Video CD
STREAM: Author: Albeu
STREAM: Comment: based on the code from ???
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename vcd://2 ext: (null)
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
header block 1 size: 0
stream_seek: WARNING! Can't seek to 0x4 !
AVS: avs_check_file - attempting to open file vcd://2
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
THIS DOESN'T LOOK LIKE AN MPEG-TS FILE!
TRIED UP TO POSITION 0, FOUND 0, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=-8
LMLM4 Stream Format not found
system stream synced at 0x48DF97 (4775831)!
==> Found audio stream: 0
ID_AUDIO_ID=0
==> Found video stream: 0
ID_VIDEO_ID=0
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1140.0 kbps (142.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000001  size:352x288  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/mvr/.mplayer/sub/'
get_path('default.sub') -> '/home/mvr/.mplayer/default.sub'
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: made decode tables with MMX optimization
mp3lib: using MMX optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 1.0, Layer II, 44100 Hz 224 kbit Stereo, BPF: 731
Channels: 2, copyright: No, original: No, CRC: No, emphasis: 1
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
ID_FILENAME=vcd://2
ID_DEMUXER=mpegps
ID_VIDEO_FORMAT=0x10000001
ID_VIDEO_BITRATE=1140000
ID_VIDEO_WIDTH=352
ID_VIDEO_HEIGHT=288
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=1.3333
ID_AUDIO_CODEC=mp3
ID_AUDIO_FORMAT=80
ID_AUDIO_BITRATE=224000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
ID_LENGTH=55.53
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x0101fe).
[xv common] Maximum source image dimensions: 1024x1024
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
ID_VIDEO_CODEC=mpeg12
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
alsa-init: requested format: 44100 Hz, 2 channels, 9
alsa-init: compiled for ALSA-1.0.10
alsa-init: setup for 1/2 channel(s)
alsa-init: 1 soundcard found, using: default
alsa-init: pcm opend in block-mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Starting playback...
alsa-space: free space = 65536, prepared --
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (352x288->384x288,flags=0,'MPlayer',0x32315659)
VO: [xv] 352x288 => 384x288 Planar YV12
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 73 for hw scaling
[xv] dx: 0 dy: 0 dw: 384 dh: 308
*** [vo] Allocating mp_image_t, 352x288x12bpp YUV planar, 152064 bytes
[xv] dx: 0 dy: 0 dw: 384 dh: 308
alsa-play: xrun of at least 57.188 msecs. resetting stream?,?% 0 0
*** [vo] Allocating mp_image_t, 352x288x12bpp YUV planar, 152064 bytes
get_path('subfont.ttf') -> '/home/mvr/.mplayer/subfont.ttf',?% 1 0
Unicode font: 255 glyphs.
*** [vo] Allocating mp_image_t, 352x288x12bpp YUV planar, 152064 bytes
MPEG Stream reached EOF-0.002 ct:  0.130 1046/1046  5%  1% 20.3% 19 0
ds_fill_buffer: EOF reached (stream: audio)
alsa-play: xrun of at least 3.576 msecs. resetting stream
alsa-space: xrun of at least 20.354 msecs. resetting stream21.0% 19 0
alsa-space: free space = 0, xrun --
alsa-space: free space = 65536, prepared --49/1049  5%  1% 21.0% 19 0
alsa-space: free space = 65536, prepared --50/1050  5%  1% 21.0% 19 0
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
EOF code: 1  42.7 A-V:  0.174 ct:  0.150 1050/1050  5%  1% 21.0% 19 0

Uninit audio filters...
[libaf] Removing filter dummy
uninit audio: mp3lib
uninit video: libmpeg2
Successfully enabled DPMS
alsa-uninit: pcm closed
vo: uninit ...

Exiting... (End of file)

```

I am also surprised that gxine works but xine doesn't.

Jonam

---

### Post by medya on 2007-03-17
I have a DVD-ROM and a CD-RW , 
the last time which I had tried ubuntu, it was breezy , or dapper, VCD used to work well, but at that  itme I didnt have my new CD-RW. so a new CD-RW is the only thing which changed since I had tried ubuntu.

I suspect it is because now I have Two things . (DVD-ROM and CD-RW)

---

### Post by medya on 2007-03-17
Jonam can u unplug one of ur devices and then try it?

---

### Post by Jonam on 2007-03-17
> **medya said:**
> Jonam can u unplug one of ur devices and then try it?

I'm not that game :) My PC is quite old and works so I will just let it work. Maybe sometime in the future when I get a DVD-RW I will have a try.

My machine dual-boots into Win98SE and Ubuntu and VCDs have worked reliably under Windows for many years, it is only under Ubuntu that I appear to be having some problems.

Jonam

---

### Post by panch0 on 2007-03-19
> **Jonam said:**
> Well, I tried mplayer -v -identify vcd://2 and all I got was the intro copyright track running.

Your video is track 3, so run:

mplayer vcd://3

and it will play it.

If you load a VCD in KPlayer, it will show you all the tracks and their lengths in the library, then you'll be able to see the longest track which is the actual video.

---

### Post by Jonam on 2007-03-20
Got it to work but there are only two tracks on the disc. I would have thought selecting track 2 would get the movie going and track 1 the intro.

---

### Post by Jonam on 2007-03-30
An update. I did some major surgery on my PC today as I got hold of a DVD-RW drive. As expected, this caused some major headaches but I found out how to get things working well in the end. Here is what happened step by step:

1. Original install - one CD-ROM (Sony CDU5211) as slave and CD-RW (Creative RW1210E) as master on one IDE bus using 40 way cable. The other bus has two hard-disks using 80 way cable.

2. Switched off PC and removed CD-RW and replaced with DVD-RW (Pioneer 112D) changing the 40 way cable to an 80 way at the same time.

3. Fired up Ubuntu and found that both drives appeared to mount OK. Tried to load an audio CD in the DVD-RW. It would not run in Soundjuicer and with some difficulty, got working in GXine. However, the sound was terrible - very choppy and echoing. Same result in the remaining CD-ROM drive. VCDs or DVDs would not play.

4. Tried to change /etc/fstab to create a new entry for the DVD-RW but on re-booting, PC would not see any CDs inserted into the drive. Booted into Win98 and it would not see the DVD-RW at all.

5. Checked PC-BIOS settings - found CD-RW had UDMA mode set to 2 and DVD-RW set to 4. Tried to force BIOS to set DVD-RW to 2 but it would automatically revert to 4 due to the 80-way cable.

6. Removed the DVD-RW from the IDE cable so only the CD-ROM was running. Same problem with terrible choppy sound.

7. Decided to replace the 80 way cable with the old 40 way cable with the penalty of a slower DVD-RW. Checked BIOS on reboot and found both CD-ROM and DVD-RW were set to UDMA mode 2.

8. System booted with an audio disc in CD-ROM. File-system check seemed to show some errors in this drive. I suspect a dirty lens, otherwise all went OK.

9. Tried to play VCD, DVD and CD and all played OK in the DVD-RW using any player (Mplayer, GXine, Xine). Audio CDs would play simultaneously from the CD-ROM using Soundjuicer. As usual, totem player failed and VLC would not play anything. VCDs play intermittently in the CD-ROM and this might be a dirty lens problem.

In summary, it appears that to be able to play CDs,VCDs and DVDs on a two drive system with a CD-ROM and DVD, both drives have to be run in the same UDMA mode (2) and this is only possible with a 40 way cable.

Jonam

---

