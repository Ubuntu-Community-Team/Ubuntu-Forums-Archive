---
title: "Codec problems (I think)"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Fungal Fractoids on 2007-12-14
Whenever I watch an .avi file all of the colour is whacked out, peoples skin looks blue and the sky pink for instance. I've tried downloading a few different codecs and media players but it doesn't help at all. On totem I'm able to adjust the hue and saturation which makes a difference, but it is seemingly impossible to get natural looking colours. Does anyone know how to get around this? It is the sort of problem that would drive me back to Windows :(

---

### Post by RomeReactor on 2007-12-14
Hi. Can you tell us which media player are you using? have you tried the avi file in other players? which codec libraries have you installed?

---

### Post by Fungal Fractoids on 2007-12-14
I started using the default player (totem, I think), it did an automatic codec update the first time I ran it. Then i downloaded Mplayer and got the same effect, except I couldn't change the hue and saturation. I'm not sure about the codec libraries, is there any wayI can find out what I have installed? I know I downloaded a couple of codecs from the package manager but they didn't seem to do anything.

---

### Post by Schalken on 2007-12-14
i get problems like these when using the w32codecs. i recommend you remove them ```
sudo aptitude remove w32codecs
``` (w64codecs if your on 64bit) and try the free ffmpeg codecs ```
sudo aptitude install ffmpeg gstreamer0.10-ffmpeg libxine1-ffmpeg
``` i've found the ffmpeg codecs work very well for most formats except WMA9 (no output). to see if there are any problems with video playback, i also recommend you install mplayer ```
sudo aptitude install mplayer-nogui
``` and try to play the file in the terminal using ```
mplayer filename.avi
``` it will tell you in the terminal what codecs it is using and any problems it has decoding the video.

---

### Post by Fungal Fractoids on 2007-12-14
^^ Itried that last command and got this in terminal:

```
user@user-laptop:~$ sudo mplayer /home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi.
File not found: '/home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi'
Failed to open /home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi.


Exiting... (End of file)
```

I'll go try uninstalling the w32 stuff as you suggested, will let you know how it goes...

---

### Post by Fungal Fractoids on 2007-12-14
Well, I installed those codecs you suggested and the non-gui mplayer but am still getting that same message on terminal :confused:

---

### Post by Fungal Fractoids on 2007-12-14
In the mplayer preferences there is a drop-down menu called 'Video codec family' and I can choose from a selection, but i doesn't matter which one I choose it's still all blue- even after restarting the app...

---

### Post by Fungal Fractoids on 2007-12-14
OK, so I've been looking into it a bit and found this fix:

[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

Thing is, I don't know whether I am using totem-gstreamer or not but when I open properties via terminal it gies me this message before opening up:

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
```

And, when I change the video output pipeline, I get an error message:

Custom: could not link xvimagesink1 to ffmpegcsp1

So this is my xorg.conf:

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

So can anyone see a way I might be able to fix this problem??? I'm using an ATI 1700 using the fglrx proprietary driver...

---

### Post by Tarmael on 2007-12-14
@ Fungal:

Have you ever tried to install the 8.433 driver?

Totem player and all the other ones such as Mplayer all use the same codecs intalled on the machine. Your problem also could come from the media you are trying to play, I've had issues with some DivX encoded video formats and have had almost perfect .ogg formats. The way I get around this is by using VLC and Totem. If it doesn't work in one, it'll work in the other because VLC uses it's own set of codecs.

---

### Post by Fungal Fractoids on 2007-12-14
Aha... And is VLC available through the packet manager?

---

### Post by SunnyRabbiera on 2007-12-14
you may want to dump gstreamer and use just the win32 codecs as they work better alone.
I have this issue with the gstreamer plugins

---

### Post by Fungal Fractoids on 2007-12-14
No luck :(

It's still blue but in VLC the screen jumps around...

---

### Post by Fungal Fractoids on 2007-12-14
> **SunnyRabbiera said:**
> you may want to dump gstreamer and use just the win32 codecs as they work better alone.
I have this issue with the gstreamer plugins

And how would you go about that... Heh, I'm a noob :)

-edit-

Duh, I figure it out, don't worry ;)

---

### Post by Tarmael on 2007-12-14
> **Fungal Fractoids said:**
> No luck :(

It's still blue but in VLC the screen jumps around...

That's quite odd...

What are the properties of the file(s) you are testing with??

---

### Post by Fungal Fractoids on 2007-12-14
^^ Not quite sure waht you mean but when I right-click properties video properties are:
624x352
XVID MPEG-4
24 frames per sec
Bitrate: N/A

But I am getting the same problem with any .avi I try to play, I only have one other non-avi file and I think its working ok.

I've tried everything as suggested above and no luck whatsoever

---

### Post by Schalken on 2007-12-14
> **Fungal Fractoids said:**
> ^^ Itried that last command and got this in terminal:

```
user@user-laptop:~$ sudo mplayer /home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi.
File not found: '/home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi'
Failed to open /home/user/videos/Weeds.S03E15.HDTV.XviD-XOR.avi.


Exiting... (End of file)
```

I'll go try uninstalling the w32 stuff as you suggested, will let you know how it goes...

First of all, only use sudo for administrative tasks! You don't need to be root to play a video.

Anyways, obviously mplayer is having trouble finding the file your trying to play. If anything can access it, so can mplayer. Go into a terminal and typing just "mplayer " (including the space, no sudo!) and drag the file into the terminal. The full filename should come up after "mplayer " in single quotes, then all you have to do is hit enter and mplayer will do it's best to play the video. This avoids any possible human errors in typing the filename manually.

---

### Post by Fungal Fractoids on 2007-12-14
> **Schalken said:**
> First of all, only use sudo for administrative tasks! You don't need to be root to play a video.

LOL, cool...

> Anyways, obviously mplayer is having trouble finding the file your trying to play. If anything can access it, so can mplayer. Go into a terminal and typing just "mplayer " (including the space, no sudo!) and drag the file into the terminal. The full filename should come up after "mplayer " in single quotes, then all you have to do is hit enter and mplayer will do it's best to play the video. This avoids any possible human errors in typing the filename manually.

Ok, so this is what terminal say when I do that:

```
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1075.8 kbps (131.3 kbyte/s)
Clip info:
 Software: cant touch this
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 

```

Any ideas?

---

### Post by Fungal Fractoids on 2007-12-14
Argh, I'm losing my mind! :confused:

I managed to get the fix from the link I posted working but it didn't fix my problem at all... I am at a loss :(

---

### Post by Schalken on 2007-12-15
> **Fungal Fractoids said:**
> LOL, cool...



Ok, so this is what terminal say when I do that:

```
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1075.8 kbps (131.3 kbyte/s)
Clip info:
 Software: cant touch this
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 

```

Any ideas?

And it doesn't play the video? Doesn't say anything after that? If it doesn't play the video it should at least say why :S

LOL: > ```
Software: cant touch this
```
[Hammertime!]("http://en.wikipedia.org/wiki/Can%27t_touch_this")

---

