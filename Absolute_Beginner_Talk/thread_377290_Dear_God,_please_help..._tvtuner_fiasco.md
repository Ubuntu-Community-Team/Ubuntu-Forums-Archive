---
title: "Dear God, please help... tvtuner fiasco"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by AbyssNOLF on 2007-03-05
I've spent some 20 or so hours on this problem and its driving me insane.  I've searched googles and forums and found various leads but nothing solid and I'm looking for any advice or insight.  

I have a Hauppage WinTV-Go Plus tv tuner installed into my Ubuntu system.  Ubuntu appears to recognize it just swell, but tvtime and xawtv show absolutely nothing.  There is some output below from what I get when loading the bttv modules.  Even getting one channel would make my week.  Thanks in advance for anyone that comments.

dmesg | grep bttv
[17181579.932000] bttv: driver version 0.9.16 loaded
[17181579.932000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17181579.932000] bttv: Bt8xx card found (0).
[17181579.932000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 201, latency: 32, mmio: 0xf6085000
[17181579.932000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17181579.932000] bttv0: using: Hauppauge (bt878) [card=10,insmod option]
[17181579.932000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17181579.936000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17181580.112000] bttv0: Hauppauge eeprom indicates model#44981
[17181580.112000] bttv0: using tuner=50
[17181580.112000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17181580.116000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17181580.120000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17181580.132000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17181580.188000] bttv0: registered device video0
[17181580.188000] bttv0: registered device vbi0
[17181580.188000] bttv0: PLL: 28636363 => 35468950 .. ok


dmesg | grep tuner
[17180263.972000] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[17180263.972000] bttv0: using tuner=50
[17180263.972000] tuner 0-0061: type set to 50 (TCL 2002N)

---

### Post by SurR3AL on 2007-03-06
why don't you try MythTv....check [this]("http://parker1.co.uk/mythtv_ubuntu.php") out :)

---

### Post by AbyssNOLF on 2007-03-06
I've read that MythTv shouldn't be attempted until I can at least get video in tvtime or xawtv, because if it works in those simpler programs it will also work in MythTv without much trouble. However, MythTv is my end goal, and I hope I make it there.

---

### Post by Hendrixski on 2007-03-06
While I don't know the details behind MythTV, I do know that there is a lot of literature in  MythTV project pages that describe how to install and configure tv tuners, and more importantly  a list of which tuners work on Linux, and which ones don't.

---

### Post by AbyssNOLF on 2007-03-06
The Hauppage Wintv Go Plus is based on the bttv modules and is detected correctly automatically.  I have seen that other people have had success with this card and cards very similar to it, so I'm approximately 99% sure it /can/ work, just not sure that I can /make/ it work. 

Thanks for the comments.  Any other advice?

---

### Post by superm1 on 2007-03-07
> **AbyssNOLF said:**
> The Hauppage Wintv Go Plus is based on the bttv modules and is detected correctly automatically.  I have seen that other people have had success with this card and cards very similar to it, so I'm approximately 99% sure it /can/ work, just not sure that I can /make/ it work. 

Thanks for the comments.  Any other advice?
Well first thing, permissions?  Are you able to read from the device?
Check the permissions on it 
```
ls -l /dev/video*
```

---

### Post by AbyssNOLF on 2007-03-07
When I check permissions, this is what I get:

ls -l /dev/video*
lrwxrwxrwx 1 root  root      6 2007-03-05 21:54 /dev/video -> video0
crw-rw---- 1 abyss abyss 81, 0 2007-03-05 21:54 /dev/video0


Originally /dev/video0 said root:root, but it didn't matter when I changed it.  I've also run tvtime as sudo , still nothing.

Now, when I disconnect the coax from the card, tvtime reports 'No signal', but stops reporting that when I plug the coax back in.  Also, when there is a channel I know I don't get (channel 1), it says "no signal" again.  

Please keep the suggestions coming, if you would.

---

### Post by superm1 on 2007-03-07
Well so as to rule out a problem with tvtime, you can try using VLC.  It does have V4L support.

---

### Post by Bagnaj97 on 2007-03-07
Try using kdetv from the repositories. Whilst the picture quality isn't as good as tvtime I find it a much easier program to use.

---

### Post by AbyssNOLF on 2007-03-07
I tried VLC and it appeared to open the video stream but did not display any video window.  I also installed kdetv and it seemed to scan and locate channels, but did not show a video and gave a heck of a lot of errors.

The main kdetv was the following:
Unable to grab video.
Video display is not possible with the current plugin configuration.  Try playing with the configuration options of the V4L2 plugin.

Here's a sample of the command line output:
detv: WARNING: IO error - requeuing buffer
kdetv: WARNING: V4L2Dev::enqueueBuffer(): buffer already queued: 0
kdetv: WARNING: V4L2Dev: VIDIOC_DQBUF failed: Input/output error
kdetv: WARNING: IO error - requeuing buffer
kdetv: WARNING: V4L2Dev::enqueueBuffer(): buffer already queued: 0
Too many errors. Ending V4L2 grabbing.


I don't have any idea what that means.  I looked at the V4L2 plugin and it didn't have that many options, and I tried a different set with the same results.  

On a side note, I looked on the v4l wiki and mailing list archive and I know that some people have gotten this to work for at least one channel and several channels for most.  Only thing is that they might have all been in Europe, and I'm definitely in Missouri.

Thoughts?

---

### Post by panch0 on 2007-03-07
I would try with MPlayer, there is a bunch of options to play with. If it doesn't work, post the MPlayer output. The -v option will give even more information.

---

### Post by AbyssNOLF on 2007-03-07
I tested the mplayer with options in a config file that were copied out of the man pages for mplayer.  The config file options are below.

oac=pcm=yes
ovc=lavc=yes
lavcopts=vcodec=mjpeg
tv=driver=v4l2:input=1:width=640:height=480:device=/dev/video0:audiorate=48000



Here is the output from the mplayer trial run...

[email]abyss@Cyberia:~/.mpla[/email]yer$ mplayer tv://4 -v
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 28, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Warning unknown option oac at line 2
Warning unknown option ovc at line 3
Warning unknown option lavcopts at line 4
get_path('codecs.conf') -> '/home/abyss/.mplayer/codecs.conf'
Reading /home/abyss/.mplayer/codecs.conf: Can't open '/home/abyss/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: 'tv://4' '-v'
init_freetype
get_path('font/font.desc') -> '/home/abyss/.mplayer/font/font.desc'
font: can't open file: /home/abyss/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/abyss/.mplayer/input.conf'
Can't open input config file /home/abyss/.mplayer/input.conf: No such file or directory
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
get_path('4.conf') -> '/home/abyss/.mplayer/4.conf'

Playing tv://4.
get_path('sub/') -> '/home/abyss/.mplayer/sub/'
STREAM: [null] tv://4
STREAM: Description: Null stream
STREAM: Author: Albeu
STREAM: Comment: 
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: BT878 video (Hauppauge (bt878))
 Tuner cap:
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = NTSC; 2 = SECAM; 3 = PAL-Nc; 4 = PAL-M; 5 = PAL-N; 6 = NTSC-JP; 7 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video; 3 = Composite3;
 Current input: 1
 Format GREY   ( 8 bits, 8 bpp, gray): Planar Y800
 Format HI240  ( 8 bits, 8 bpp, dithered color): Unknown
 Format RGB555 (16 bits, 15 bpp RGB, le): BGR 15-bit
 Format RGB555X (16 bits, 15 bpp RGB, be): Unknown
 Format RGB565 (16 bits, 16 bpp RGB, le): BGR 16-bit
 Format RGB565X (16 bits, 16 bpp RGB, be): Unknown
 Format BGR24  (24 bits, 24 bpp RGB, le): BGR 24-bit
 Format BGR32  (32 bits, 32 bpp RGB, le): BGRA
 Format RGB32  (32 bits, 32 bpp RGB, be): RGBA
 Format YUYV   (16 bits, 4:2:2, packed, YUYV): Packed YUY2
 Format YUYV   (16 bits, 4:2:2, packed, YUYV): Packed YUY2
 Format UYVY   (16 bits, 4:2:2, packed, UYVY): Packed UYVY
 Format YUV422P (16 bits, 4:2:2, planar, Y-Cb-Cr): Planar 422P
 Format YUV420 (12 bits, 4:2:0, planar, Y-Cb-Cr): Planar I420
 Format YVU420 (12 bits, 4:2:0, planar, Y-Cr-Cb): Planar YV12
 Format YUV411P (16 bits, 4:1:1, planar, Y-Cb-Cr): Planar 411P
 Format YUV410 ( 9 bits, 4:1:0, planar, Y-Cb-Cr): Planar IF09
 Format YVU410 ( 9 bits, 4:1:0, planar, Y-Cr-Cb): Planar YVU9
 Current format: YVU420
v4l2: current audio mode is : MONO
v4l2: set format: YVU420
v4l2: set input: 1
Selected norm: pal
v4l2: set norm: PAL
v4l2: set width: 640
v4l2: set height: 480
Selected channel list: europe-east (including 133 channels)
Requested channel: 4
Current frequency: 0 (0.000)
==> Found video stream: 0
v4l2: get format: YVU420
v4l2: get fps: 25.000000
v4l2: get width: 640
v4l2: get height: 480
Using a ring buffer for maximum 2 frames, 0 MB total size.
v4l2: set Brightness: 32768 [0, 65535]
v4l2: set Hue: 32768 [0, 65535]
v4l2: set Saturation: 32768 [0, 65535]
v4l2: set Contrast: 32768 [0, 65535]
[V] filefmt:9  fourcc:0x32315659  size:640x480  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/abyss/.mplayer/sub/'
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
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x000821).
[xv common] Maximum source image dimensions: 1920x1200
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (640x480->640x480,flags=0,'MPlayer',0x32315659)
VO: [xv] 640x480 => 640x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x434d5658 (XVMC) planar
Xvideo image format: 0x35315652 (RV15) packed
Xvideo image format: 0x36315652 (RV16) packed
Xvideo image format: 0x32335652 (RV32) packed
using Xvideo port 68 for hw scaling
[xv] dx: 0 dy: 0 dw: 640 dh: 512
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
v4l2: going to capture
v4l2: ioctl dequeue buffer failed: Input/output error, idx = 0
v4l2: ioctl dequeue buffer failed: Input/output error, idx = 0
v4l2: ioctl dequeue buffer failed: Input/output error, idx = 0
v4l2: ioctl dequeue buffer failed: Input/output error, idx = 0
*** [vo] Exporting mp_image_t, 640x480x12bpp YUV planar, 460800 bytes
[xv] dx: 0 dy: 0 dw: 640 dh: 512
v4l2: ioctl dequeue buffer failed: Input/output error, idx = 0
v4l2: ioctl dequeue buffer failed: Input/output error, idx = 0
Uninit video: raw??% ??% ??,?% 0 0 
v4l2: ioctl dequeue buffer failed: Input/output error, idx = 0
v4l2: 0 frames successfully processed, 1 frames dropped.
v4l2: up to 0 video frames buffered.
vo: uninit ...


I don't know what any of that means, but it looks like it might be bad with the whole dequeue buffer failed thing going on.  That also happened about every half a seconf, which seems like another bad sign.  

Any clues from the gurus?

---

### Post by AbyssNOLF on 2007-03-07
I also tried the v4l driver instead of the v4l2 driver and I didn't get the error every half second but I also didn't get anything but a green screen.  Here's the output again, just to make the page longer.



MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 28, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Warning unknown option oac at line 2
Warning unknown option ovc at line 3
Warning unknown option lavcopts at line 4
get_path('codecs.conf') -> '/home/abyss/.mplayer/codecs.conf'
Reading /home/abyss/.mplayer/codecs.conf: Can't open '/home/abyss/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: 'tv://4' '-v'
init_freetype
get_path('font/font.desc') -> '/home/abyss/.mplayer/font/font.desc'
font: can't open file: /home/abyss/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using Linux hardware RTC timing (1024Hz).
get_path('input.conf') -> '/home/abyss/.mplayer/input.conf'
Can't open input config file /home/abyss/.mplayer/input.conf: No such file or directory
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
get_path('4.conf') -> '/home/abyss/.mplayer/4.conf'

Playing tv://4.
get_path('sub/') -> '/home/abyss/.mplayer/sub/'
STREAM: [null] tv://4
STREAM: Description: Null stream
STREAM: Author: Albeu
STREAM: Comment: 
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: BT878 video (Hauppauge (bt878))
 Capabilites: capture tuner overlay clipping scales 
 Device type: 171
 Supported sizes: 48x32 => 924x576
 Inputs: 4
  0: Television: tuner audio tv camera  (tuner:1, norm:pal)
  1: Composite1: audio camera  (tuner:0, norm:pal)
  2: S-Video: audio camera  (tuner:0, norm:pal)
  3: Composite3: audio camera  (tuner:0, norm:pal)
mbuf: size=17039360, frames=8
 Audio devices: 1
Video capture card reports the audio setup as follows:
  0: Television: muted=no vol=0 bass=0 treble=0 balance=0 mode=mono chan=1
Using input 'Composite1'
Selected norm: pal
Requested width: 640
Requested height: 480
Selected input hasn't got a tuner!
==> Found video stream: 0
Output format: Planar YV12
Picture values:
 Depth: 12, Palette: yuv420p (Format: Planar YV12)
 Brightness: 32768, Hue: 32768, Colour: 32768, Contrast: 32768
Using a ring buffer for maximum 2 frames, 0 MB total size.
Enabling tv audio. Requested setup is:
id=0 vol=0 bass=0 treble=0 balance=0 mode=mono chan=1
[V] filefmt:9  fourcc:0x32315659  size:640x480  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/abyss/.mplayer/sub/'
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such device.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x000821).
[xv common] Maximum source image dimensions: 1920x1200
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (640x480->640x480,flags=0,'MPlayer',0x32315659)
VO: [xv] 640x480 => 640x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x434d5658 (XVMC) planar
Xvideo image format: 0x35315652 (RV15) packed
Xvideo image format: 0x36315652 (RV16) packed
Xvideo image format: 0x32335652 (RV32) packed
using Xvideo port 68 for hw scaling
[xv] dx: 0 dy: 0 dw: 640 dh: 512
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
*** [vo] Exporting mp_image_t, 640x480x12bpp YUV planar, 460800 bytes
...

---

### Post by AbyssNOLF on 2007-03-08
Well, I tested the tuner in a windows machine and I managed to see video and all that jazz, so it seems that the tv tuner does indeed work.  However, I still get nothing in Ubuntu.  

I really need some help here, so anyone who has any suggestion, no matter how wild and crazy, feel free to throw it forth.

---

### Post by Drakkor on 2007-03-08
I have a Haupaugge WinTv card , a pretty old one and tvtime works flawlessly, how did you get output with ```
dmesg | grep bttv
```  maybe compare the two ?

---

### Post by AbyssNOLF on 2007-03-08
dmesg | grep bttv

[17187339.572000] bttv: driver version 0.9.16 loaded
[17187339.572000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17187339.572000] bttv: Bt8xx card found (0).
[17187339.572000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 201, latency: 32, mmio: 0xf6085000
[17187339.572000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17187339.572000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17187339.572000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17187339.576000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17187339.740000] bttv0: Hauppauge eeprom indicates model#44981
[17187339.740000] bttv0: using tuner=50
[17187339.744000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17187339.744000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17187339.752000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17187339.764000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17187339.776000] bttv0: registered device video0
[17187339.776000] bttv0: registered device vbi0
[17187339.776000] bttv0: PLL: 28636363 => 35468950 .. ok

---

### Post by Drakkor on 2007-03-08
Hmm..... I get no output

---

### Post by Drakkor on 2007-03-08
Nevermind, Beryl was running and maybe screwed it up, I rebooted to normal and got this:

drakkor@Ubuntu-Edgy:~$ dmesg | grep bttv
[17179593.576000] bttv: driver version 0.9.16 loaded
[17179593.576000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179593.576000] bttv: Bt8xx card found (0).
[17179593.576000] bttv0: Bt878 (rev 17) at 0000:02:0b.0, irq: 185, latency: 32, mmio: 0xee800000
[17179593.576000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179593.576000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179593.576000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17179593.580000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179593.676000] bttv0: Hauppauge eeprom indicates model#44371
[17179593.676000] bttv0: using tuner=2
[17179593.676000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17179593.736000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179593.736000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179593.784000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179593.860000] bttv0: registered device video0
[17179593.860000] bttv0: registered device vbi0
[17179593.860000] bttv0: registered device radio0
[17179593.896000] bttv0: PLL: 28636363 => 35468950 .. ok
drakkor@Ubuntu-Edgy:~$

---

### Post by superm1 on 2007-03-09
> **Drakkor said:**
> Nevermind, Beryl was running and maybe screwed it up, I rebooted to normal and got this:

drakkor@Ubuntu-Edgy:~$ dmesg | grep bttv
[17179593.576000] bttv: driver version 0.9.16 loaded
[17179593.576000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179593.576000] bttv: Bt8xx card found (0).
[17179593.576000] bttv0: Bt878 (rev 17) at 0000:02:0b.0, irq: 185, latency: 32, mmio: 0xee800000
[17179593.576000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179593.576000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179593.576000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17179593.580000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179593.676000] bttv0: Hauppauge eeprom indicates model#44371
[17179593.676000] bttv0: using tuner=2
[17179593.676000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17179593.736000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179593.736000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179593.784000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179593.860000] bttv0: registered device video0
[17179593.860000] bttv0: registered device vbi0
[17179593.860000] bttv0: registered device radio0
[17179593.896000] bttv0: PLL: 28636363 => 35468950 .. ok
drakkor@Ubuntu-Edgy:~$
Beryl was running during all these failed playback attempts too?

---

### Post by kvonb on 2007-03-09
Are you running Feisty (7.xx) or Edgy (6.10)?

It looks like Feisty to me, as I don't think v4l2 is included in Edgy, although I could be completely wrong!

If you are using Feisty, I would suggest trashing it and installing Edgy instead as Feisty is no way near ready at the mo!

However, on a more positive note:

Go to this page and find the number of your card:

[http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV](http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV)

Then follow this guide: (which is for a different card, but has some relevant info)

[http://web.missouri.edu/~datcnc/htpc_single.html](http://web.missouri.edu/~datcnc/htpc_single.html)

When you have that working, you can then install a "video recorder", see my thread here:

[http://ubuntuforums.org/showthread.php?t=249850](http://ubuntuforums.org/showthread.php?t=249850)

I have a Winfast card which seems to work some days and not others, it appears to be the antenna, they are a bit sensitive.  They seem to need a very strong signal.

If you are trying to get a feed from cable, the problem could be that you need to select that as the source, not "antenna".

Best of luck, Kev :)

---

### Post by AbyssNOLF on 2007-03-09
I'm using Edgy right now with the v4l and v4l2 plugins, and without beryl.

I followed the guide at [http://web.missouri.edu/~datcnc/htpc_single.html](http://web.missouri.edu/~datcnc/htpc_single.html), and I know that my card is number 10, but the guide didn't come up with any difference.  The card fails to show a picture.  It still shows black in xawtv and blue in tvtime.

Is it time to break this card over my knee yet?

Thanks for the help and posts guys.

---

### Post by easyease on 2007-03-09
forget all that crap...just install kaffeine-xine and its dependencies from the repo's and you will be watching tv on your pc within half an hour.

---

### Post by Drakkor on 2007-03-09
Gotta give you an A for trying, as stated before , we have similar cards, and I don't see any reason why it shouldn't work !!  Back to basics in tvtime , did you set the proper frequency table and cable mode ,right-click on the blue screen, hit channel management,and play around with the settings, remember channel one may not be veiwable, hit the up arrow to go to upper channels.

---

### Post by AbyssNOLF on 2007-03-11
Alright, so here's something promising.  Sort of.  

I have sound.  

Sound works perfectly, crystal clear, like I'm watching tv.  Except I'm not, because their is no video.

I tested different settings with the channel management in tvtime, and I still got nothing.  When the cable is unplugged, it shows no signal, and when it is plugged in, the 'no signal' message goes away, so it seems like it's detecting everything correctly, but there's no video.  

I scanned channels and I each were removed from the active list.

I saw a test somewhere that was like below, so I tried it and got...
abyss$ cat /dev/video0 > test.mpg
cat: /dev/video0: Input/output error

Everything else still looks like it always has, which is correct.  Also, I'm already tired of listening to commercials.

So...  any ideas?

---

### Post by AbyssNOLF on 2007-03-11
Also, while testing in VLC from the command line, I get the following rubbish...

VLC media player 0.8.6 Janus
[00000293] v4l demuxer error: failed syncing new frame
[00000293] v4l demuxer error: failed syncing new frame
[00000293] v4l demuxer error: failed capturing new frame
[00000293] v4l demuxer error: failed capturing new frame
[00000293] v4l demuxer error: failed capturing new frame


and so on...


So, I'm guessing that the video stream isn't working correctly.  I'm still all ears.

---

### Post by kvonb on 2007-03-12
Just to confuse you even more:  try installing "xawtv", use synaptic to search for it.

That seems to work better for me than TVtime on some occasions.

It will create a .xawtv file on first use, I've found it easier to edit the file myself, here is mine if it helps at all:
(copy betwen the ===== lines and paste as a new file called .xawtv in your home folder /home/username/.xawtv)
===========================================================
[global]
ratio = 4:3
freqtab = australia
pixsize = 128 x 96
pixcols = 1
jpeg-quality = 75
keypad-ntsc = no
keypad-partial = yes
osd = yes
osd-position = 30 , 20
use-wm-fullscreen = yes

# [Station name]
# capture = overlay | grabdisplay | on | off
# input = Television | Composite1 | S-Video | ...
# norm = PAL | NTSC | SECAM | ... 
# channel = #
# fine = # (-128..+127)
# key = keysym | modifier+keysym
# color = #
# bright = #
# hue = #
# contrast = #

[defaults]
group = main
norm = PAL
input = Television
capture = over

[SBS]
channel = 42
key = 1
capture = on

[WIN]
channel = 45
key = 9
capture = on

[GWN]
channel = 48
key = 7
capture = on

[ABC]
channel = 51
key = 2
capture = on
===========================================================

Of course you will have to change it for your region, and the channels won't work for you.

---

### Post by kvonb on 2007-03-12
Aha!!!

I just ran xawtv from the terminal and it gave me the following errors:

```
This is xawtv-3.95, running on Linux/i686 (2.6.17-11-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65
```

Now xawtv has always worked perfectly for me.

I'm wondering if this is a video driver issue, I looked up the errors and XF86DGANoDirectVideoMode seems to be a problem in the X subsystem, and also the video driver.

My copy of tvtime still works (on it's one lonely channel!), but xawtv apparently uses a different method to display it on the screen.

What video driver are you using?  Maybe post your xorg.conf if you don't know.

Regards, KEv :)

---

### Post by Drakkor on 2007-03-12
The only other thing I can think of is have you installed the correct drivers for your video card ? Just found this on digg : [http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)

---

### Post by AbyssNOLF on 2007-03-12
Xawtv shows nothing but a big old black screen and doesn't output anything to the command line that looks interesting.  It still has sound though.

As far as a video driver goes, I'm running off of the board's integrated graphics (S3 chrome? or something) and am not using ATI or nvidia.  

I'm thinking it's more a problem of the video stream being accessed than having the cable settings in the green.  I haven't tried the RCA input, but I'm betting it does the same thing.  I'll see if I can find something with RCA output and test what happens tomorrow.

---

### Post by AbyssNOLF on 2007-03-15
Surely there are some veterans out there that might have some idea.  Sound but no video, i/o errors, everything auto-detected.  Sounds like something I should be able to look up but can't.

If I can't solve the problem in the life of this thread, then I'm afraid I must admit defeat.

---

### Post by cac67 on 2007-06-02
I started working on this problem this afternoon while migrating my niece to mepis 6.5.02.  After much googling and poking and prodding, I managed to get kdetv to load up all the channels and tune from channel to channel.  The picture quality was not the best, but I could change the channels.  I did the following as root to get this:

```
rmmod bttv
```

```
modprobe bttv tuner=10
```

Then I loaded up kdetv and it scanned the channels.  Then I added

```
bttv tuner=10
```

to etc/modules, rebooted, and fired up kdetv again.  It was still displaying the last channel tuned, but couldnt change the channel.  I'm no expert on linux, and I haven't used mepis in a long time, so I think the line I added to etc/modules is wrong.  Still, it's progress.

---

### Post by mgmiller on 2007-06-10
I have been researching this for a while and I have compiled a lot of info from many sources around the web.  You need to really know which card you have and which tuner chip it uses.
You should also be running the most up to date kernel from Ubuntu, (currently the 2.6.20 series).  If you have an older kernel, it may not have support for your card (possible) or for your tuner chip (very likely).

I suspect you have the wrong tuner type specified, or you have a tuner type not supported by your kernel.  You are showing tuner type=50, which is a TCL 2002N
You are showing card type=10 which is a Hauppauge (bt878 card.

Examine the card itself to determine the tuner type.

The tuner should be marked with the brand name, and you can look at the crystals (little aluminum cans) on the board to see if you have an NTSC or a PAL tuner. For PAL, the crystal is marked 28.xxxMHz (where xxx are three digits). For NTSC, the canister should say 35.xxxMHz. Once you have identified your tuner, select the value of n from the following list for the 2.6.20 kernel:

tuner=n        type of tuner chip
  --------------------------------------------------------------
  tuner=0      Temic PAL (4002 FH5)
  tuner=1      Philips PAL_I (FI1246 and compatibles)
  tuner=2      Philips NTSC (FI1236,FM1236 and compatibles)
  tuner=3      Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF)
  tuner=4      NoTuner
  tuner=5      Philips PAL_BG (FI1216 and compatibles)
  tuner=6      Temic NTSC (4032 FY5)
  tuner=7      Temic PAL_I (4062 FY5)
  tuner=8      Temic NTSC (4036 FY5)
  tuner=9      Alps HSBH1
  tuner=10     Alps TSBE1
  tuner=11     Alps TSBB5
  tuner=12     Alps TSBE5
  tuner=13     Alps TSBC5
  tuner=14     Temic PAL_BG (4006FH5)
  tuner=15     Alps TSCH6
  tuner=16     Temic PAL_DK (4016 FY5)
  tuner=17     Philips NTSC_M (MK2)
  tuner=18     Temic PAL_I (4066 FY5)
  tuner=19     Temic PAL* auto (4006 FN5)
  tuner=20     Temic PAL_BG (4009 FR5) or PAL_I (4069 FR5)
  tuner=21     Temic NTSC (4039 FR5)
  tuner=22     Temic PAL/SECAM multi (4046 FM5)
  tuner=23     Philips PAL_DK (FI1256 and compatibles)
  tuner=24     Philips PAL/SECAM multi (FQ1216ME)
  tuner=25     LG PAL_I+FM (TAPC-I001D)
  tuner=26     LG PAL_I (TAPC-I701D)
  tuner=27     LG NTSC+FM (TPI8NSR01F)
  tuner=28     LG PAL_BG+FM (TPI8PSB01D)
  tuner=29     LG PAL_BG (TPI8PSB11D)
  tuner=30     Temic PAL* auto + FM (4009 FN5)
  tuner=31     SHARP NTSC_JP (2U5JF5540)
  tuner=32     Samsung PAL TCPM9091PD27
  tuner=33     MT20xx universal
  tuner=34     Temic PAL_BG (4106 FH5)
  tuner=35     Temic PAL_DK/SECAM_L (4012 FY5)
  tuner=36     Temic NTSC (4136 FY5)
  tuner=37     LG PAL (newer TAPC series)
  tuner=38     Philips PAL/SECAM multi (FM1216ME MK3)
  tuner=39     LG NTSC (newer TAPC series)
  tuner=40     HITACHI V7-J180AT
  tuner=41     Philips PAL_MK (FI1216 MK)
  tuner=42     Philips 1236D ATSC/NTSC 
  tuner=43     Philips NTSC MK3 (FM1236MK3 or FM1236/F)
  tuner=44     Philips 4 in 1 (ATI TV Wonder Pro/Conexant)
  tuner=45     Microtune 4049 FM5
  tuner=46 - Panasonic VP27s/ENGE4324D
  tuner=47 - LG NTSC (TAPE series)
  tuner=48 - Tenna TNF 8831 BGFF)
  tuner=49 - Microtune 4042 FI5 ATSC/NTSC dual in
  tuner=50 - TCL 2002N
  tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)
  tuner=52 - Thomson DTT 7610 (ATSC/NTSC)
  tuner=53 - Philips FQ1286
  tuner=54 - tda8290+75
  tuner=55 - TCL 2002MB
  tuner=56 - Philips PAL/SECAM multi (FQ1216AME MK4)
  tuner=57 - Philips FQ1236A MK4
  tuner=58 - Ymec TVision TVF-8531MF/8831MF/8731MF
  tuner=59 - Ymec TVision TVF-5533MF
  tuner=60 - Thomson DTT 761X (ATSC/NTSC)
  tuner=61 - Tena TNF9533-D/IF/TNF9533-B/DF
  tuner=62 - Philips TEA5767HN FM Radio
  tuner=63 - Philips FMD1216ME MK3 Hybrid Tuner
  tuner=64 - LG TDVS-H06xF
  tuner=65 - Ymec TVF66T5-B/DFF
  tuner=66 - LG TALN series
  tuner=67 - Philips TD1316 Hybrid Tuner
  tuner=68 - Philips TUV1236D ATSC/NTSC dual in
  tuner=69 - Tena TNF 5335 and similar models
  tuner=70 - Samsung TCPN 2121P30A
  tuner=71 - Xceive xc3028
  tuner=72 - Thomson FE6600
  tuner=73 - Samsung TCPG 6121P30A

Pick your card type from this list:

    0 ->  *** UNKNOWN/GENERIC ***
  1 -> MIRO PCTV
  2 -> Hauppauge (bt848
  3 -> STB, Gateway P/N 6000699 (bt848
  4 -> Intel Create and Share PCI/ Smart Video Recorder III
  5 -> Diamond DTV2000
  6 -> AVerMedia TVPhone
  7 -> MATRIX-Vision MV-Delta
  8 -> Lifeview FlyVideo II (Bt848 LR26 / MAXI TV Video PCI2 LR26
  9 -> IMS/IXmicro TurboTV
 10 -> Hauppauge (bt878                                   
 11 -> MIRO PCTV pro
 12 -> ADS Technologies Channel Surfer TV (bt848
 13 -> AVerMedia TVCapture 98                              
 14 -> Aimslab Video Highway Xtreme (VHX)
 15 -> Zoltrix TV-Max                                     
 16 -> Prolink Pixelview PlayTV (bt878
 17 -> Leadtek WinView 601
 18 -> AVEC Intercapture
 19 -> Lifeview FlyVideo II EZ /FlyKit LR38 Bt848 (capture only)
 20 -> CEI Raffles Card
 21 -> Lifeview FlyVideo 98/ Lucky Star Image World ConferenceTV LR50
 22 -> Askey CPH050/ Phoebe Tv Master + FM    
 23 -> Modular Technology MM201/MM202/MM205/MM210/MM215 PCTV, bt878 
 24 -> Askey CPH05X/06X (bt878 [many vendors]             
 25 -> Terratec TerraTV+ Version 1.0 (Bt848/ Terra TValue Version 1.0/ Vobis TV-Boostar
26 -> Hauppauge WinCam newer (bt878
 27 -> Lifeview FlyVideo 98/ MAXI TV Video PCI2 LR50
 28 -> Terratec TerraTV+ Version 1.1 (bt878
 29 -> Imagenation PXC200             
 30 -> Lifeview FlyVideo 98 LR50         
 31 -> Formac iProTV, Formac ProTV I (bt848
 32 -> Intel Create and Share PCI/ Smart Video Recorder III
 33 -> Terratec TerraTValue Version Bt878                  [153b:1117,153b:1118,153b:1119,153b:111a,153b:1134,153b:5018]
 34 -> Leadtek WinFast 2000/ WinFast 2000 XP               [107d:6606,107d:6609,6606:217d,f6ff:fff6]
 35 -> Lifeview FlyVideo 98 LR50 / Chronos Video Shuttle II [1851:1850,1851:a050]
 36 -> Lifeview FlyVideo 98FM LR50 / Typhoon TView TV/FM Tuner [1852:1852]
 37 -> Prolink PixelView PlayTV pro
 38 -> Askey CPH06X TView99                                [144f:3000,144f:a005,a04f:a0fc]
 39 -> Pinnacle PCTV Studio/Rave                           [11bd:0012,bd11:1200,bd11:ff00,11bd:ff12]
 40 -> STB TV PCI FM, Gateway P/N 6000704 (bt878, 3Dfx VoodooTV 100 [10b4:2636,10b4:2645,121a:3060]
 41 -> AVerMedia TVPhone 98                                [1461:0001,1461:0003]
 42 -> ProVideo PV951                                      [aa0c:146c]
 43 -> Little OnAir TV
 44 -> Sigma TVII-FM
 45 -> MATRIX-Vision MV-Delta 2
 46 -> Zoltrix Genie TV/FM                                 [15b0:4000,15b0:400a,15b0:400d,15b0:4010,15b0:4016]
 47 -> Terratec TV/Radio+                                  [153b:1123]
 48 -> Askey CPH03x/ Dynalink Magic TView
 49 -> IODATA GV-BCTV3/PCI                                 [10fc:4020]
 50 -> Prolink PV-BT878P+4E / PixelView PlayTV PAK / Lenco MXTV-9578 CP
 51 -> Eagle Wireless Capricorn2 (bt878A)
 52 -> Pinnacle PCTV Studio Pro
 53 -> Typhoon TView RDS + FM Stereo / KNC1 TV Station RDS
 54 -> Lifeview FlyVideo 2000 /FlyVideo A2/ Lifetec LT 9415 TV [LR90]
 55 -> Askey CPH031/ BESTBUY Easy TV
 56 -> Lifeview FlyVideo 98FM LR50                         [a051:41a0]
 57 -> GrandTec 'Grand Video Capture' (Bt848              [4344:4142]
 58 -> Askey CPH060/ Phoebe TV Master Only (No FM)
 59 -> Askey CPH03x TV Capturer
 60 -> Modular Technology MM100PCTV
 61 -> AG Electronics GMV1                                 [15cb:0101]
 62 -> Askey CPH061/ BESTBUY Easy TV (bt878
 63 -> ATI TV-Wonder                                       [1002:0001]
 64 -> ATI TV-Wonder VE                                    [1002:0003]
 65 -> Lifeview FlyVideo 2000S LR90
 66 -> Terratec TValueRadio                                [153b:1135,153b:ff3b]
 67 -> IODATA GV-BCTV4/PCI                                 [10fc:4050]
 68 -> 3Dfx VoodooTV FM (Euro), VoodooTV 200 (USA)         [121a:3000,10b4:2637]
 69 -> Active Imaging AIMMS
 70 -> Prolink Pixelview PV-BT878P+ (Rev.4C,8E)
71 -> Lifeview FlyVideo 98EZ (capture only) LR51          [1851:1851]
 72 -> Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [1554:4011]
 73 -> Sensoray 311                                        [6000:0311]
 74 -> RemoteVision MX (RV605)
 75 -> Powercolor MTV878/ MTV878R/ MTV878F
 76 -> Canopus WinDVR PCI (COMPAQ Presario 3524JP, 5112JP) [0e11:0079]
 77 -> GrandTec Multi Capture Card (Bt878
 78 -> Jetway TV/Capture JW-TV878-FBK, Kworld KW-TV878RF   [0a01:17de]
 79 -> DSP Design TCVIDEO
 80 -> Hauppauge WinTV PVR                                 [0070:4500]
 81 -> IODATA GV-BCTV5/PCI                                 [10fc:4070,10fc:d018]
 82 -> Osprey 100/150 (878                                [0070:ff00]
 83 -> Osprey 100/150 (848
 84 -> Osprey 101 (848
 85 -> Osprey 101/151
 86 -> Osprey 101/151 w/ svid
 87 -> Osprey 200/201/250/251
 88 -> Osprey 200/250                                      [0070:ff01]
 89 -> Osprey 210/220
 90 -> Osprey 500                                          [0070:ff02]
 91 -> Osprey 540                                          [0070:ff04]
 92 -> Osprey 2000                                         [0070:ff03]
 93 -> IDS Eagle
 94 -> Pinnacle PCTV Sat                                   [11bd:001c]
 95 -> Formac ProTV II (bt878
 96 -> MachTV
 97 -> Euresys Picolo
 98 -> ProVideo PV150                                      [aa00:1460,aa01:1461,aa02:1462,aa03:1463,aa04:1464,aa05:1465,aa06:1466,aa07:1467]
 99 -> AD-TVK503
100 -> Hercules Smart TV Stereo
101 -> Pace TV & Radio Card
102 -> IVC-200                                             [0000:a155,0001:a155,0002:a155,0003:a155,0100:a155,0101:a155,0102:a155,0103:a155]
103 -> Grand X-Guard / Trust 814PCI                        [0304:0102]
104 -> Nebula Electronics DigiTV                           [0071:0101]
105 -> ProVideo PV143                                      [aa00:1430,aa00:1431,aa00:1432,aa00:1433,aa03:1433]
106 -> PHYTEC VD-009-X1 MiniDIN (bt878
107 -> PHYTEC VD-009-X1 Combi (bt878
108 -> PHYTEC VD-009 MiniDIN (bt878
109 -> PHYTEC VD-009 Combi (bt878
110 -> IVC-100                                             [ff00:a132]
111 -> IVC-120G                                            [ff00:a182,ff01:a182,ff02:a182,ff03:a182,ff04:a182,ff05:a182,ff06:a182,ff07:a182,ff08:a182,ff09:a182,ff0a:a182,ff0b:a182,ff0c:a182,ff0d:a182,ff0e:a182,ff0f:a182]
112 -> pcHDTV HD-2000 TV                                   [7063:2000]
113 -> Twinhan DST + clones                                [11bd:0026,1822:0001,270f:fc00]
114 -> Winfast VC100                                       [107d:6607]
115 -> Teppro TEV-560/InterVision IV-560
116 -> SIMUS GVC1100                                       [aa6a:82b2]
117 -> NGS NGSTV+
118 -> LMLBT4
119 -> Tekram M205 PRO
120 -> Conceptronic CONTVFMi
121 -> Euresys Picolo Tetra                                [1805:0105,1805:0106,1805:0107,1805:0108]
122 -> Spirit TV Tuner
123 -> AVerMedia AVerTV DVB-T 771                          [1461:0771]
124 -> AverMedia AverTV DVB-T 761                          [1461:0761]
125 -> MATRIX Vision Sigma-SQ
126 -> MATRIX Vision Sigma-SLC
127 -> APAC Viewcomp 878(AMAX)
128 -> DViCO FusionHDTV DVB-T Lite                         [18ac:db10]
129 -> V-Gear MyVCD
130 -> Super TV Tuner
131 -> Tibet Systems 'Progress DVR' CS16
132 -> Kodicom 4400R (master)
133 -> Kodicom 4400R (slave)
134 -> Adlink RTV24
135 -> DViCO FusionHDTV 5 Lite                             [18ac:d500]
136 -> Acorp Y878F                                         [9511:1540]
137 -> Conceptronic CTVFMi v2
138 -> Prolink Pixelview PV-BT878P+ (Rev.2E)
139 -> Prolink PixelView PlayTV MPEG2 PV-M4900
140 -> Osprey 440                                          [0070:ff07]
141 -> Asound Skyeye PCTV
142 -> Sabrent TV-FM (bttv version)
143 -> Hauppauge ImpactVCB (bt878                         [0070:13eb]
144 -> MagicTV

Once you have the tuner chip and the card type unload the current bttv driver and tuner types:

```
sudo rmmod bttv
sudo rmmod tuner
```

Next, load the correct types, substituting the numbers from the lists for x and y:
(Your card was card=10)
(If you have a Phillips NTSC tuner it would be tuner=2)

```
sudo modprobe bttv card=X tuner=Y
```

You may also have luck loading them as 2 separate commands:

```
 sudo modprobe bttv card=x
 sudo modprobe tuner type=y
```

Much information can be found here:  [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv")
Hope this helps...

---

### Post by hall2000 on 2007-07-10
ok maybe its just me but....why dont u watch tv like other do on tv i have 53in plma tx why would i want to watch it on a computer

---

### Post by amoore on 2007-07-10
> **hall2000 said:**
> ok maybe its just me but....why dont u watch tv like other do on tv i have 53in plma tx why would i want to watch it on a computer

Because MythtV is the best!!!! I also can't wait for Elisa!!!!

---

### Post by cac67 on 2007-07-10
> **hall2000 said:**
> ok maybe its just me but....why dont u watch tv like other do on tv i have 53in plma tx why would i want to watch it on a computer

Evidently you don't want to watch it on a computer.  For a young person living in a college dorm room, it's a nice alternative to having two bulky pieces of equipment in a small room.  Same goes for military personnel living in a barracks, or a young person just starting out on her own who can't afford a large screen tv and her computer.

Personally, I don't know where I'd keep a 53" plasma tv.  Seems a little bulky and obtrusive.  I don't watch enough tv to need something like that.  When I do want a bigger picture than my 21" computer monitor, I plug in my projector and go with a 60" image.

---

### Post by DaveAK on 2007-08-02
> **mgmiller said:**
> I have been researching this for a while and I have compiled a lot of info from many sources around the web.  You need to really know which card you have and which tuner chip it uses.
You should also be running the most up to date kernel from Ubuntu, (currently the 2.6.20 series).  If you have an older kernel, it may not have support for your card (possible) or for your tuner chip (very likely).

I suspect you have the wrong tuner type specified, or you have a tuner type not supported by your kernel.  You are showing tuner type=50, which is a TCL 2002N
You are showing card type=10 which is a Hauppauge (bt878 card.

Examine the card itself to determine the tuner type.

The tuner should be marked with the brand name, and you can look at the crystals (little aluminum cans) on the board to see if you have an NTSC or a PAL tuner. For PAL, the crystal is marked 28.xxxMHz (where xxx are three digits). For NTSC, the canister should say 35.xxxMHz. Once you have identified your tuner, select the value of n from the following list for the 2.6.20 kernel:

tuner=n        type of tuner chip
  --------------------------------------------------------------
  tuner=0      Temic PAL (4002 FH5)
  tuner=1      Philips PAL_I (FI1246 and compatibles)
.
.
.
  tuner=71 - Xceive xc3028
  tuner=72 - Thomson FE6600
  tuner=73 - Samsung TCPG 6121P30A

Pick your card type from this list:

  0 ->  *** UNKNOWN/GENERIC ***
  1 -> MIRO PCTV
  2 -> Hauppauge (bt848
.
.
.
142 -> Sabrent TV-FM (bttv version)
143 -> Hauppauge ImpactVCB (bt878                         [0070:13eb]
144 -> MagicTV

Once you have the tuner chip and the card type unload the current bttv driver and tuner types:

```
sudo rmmod bttv
sudo rmmod tuner
```

Next, load the correct types, substituting the numbers from the lists for x and y:
(Your card was card=10)
(If you have a Phillips NTSC tuner it would be tuner=2)

```
sudo modprobe bttv card=X tuner=Y
```

You may also have luck loading them as 2 separate commands:

```
 sudo modprobe bttv card=x
 sudo modprobe tuner type=y
```

Much information can be found here:  [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv")
Hope this helps...
This is exactly what I need to get my card working!!  I found the card type but needed the tuner number too.  Now it works just great.  Thanks!

---

### Post by Kent84 on 2007-08-31
Yes! Choosing the tuner type and card type from the list worked for me too! Now all I gotta do is to get sound going and mythtv...

---

### Post by bluntz on 2007-09-19
Try pasting this into console:
xawtv -device /dev/video0

---

