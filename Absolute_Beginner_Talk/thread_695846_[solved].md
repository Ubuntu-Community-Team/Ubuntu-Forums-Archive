---
title: "[solved] ??"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-02-13
i am fairly new to ubuntu and i have been having problems with getting videos to play, or anything really.  
 I have ubuntu 64 bit, i have flash installed and working and i think my java is working.

if i play a video on any particular website it will play with the mplayer plugin for firefox
 
but if i download the same video to my desktop and try to play it the mplayer opens and closes real quick

the same thing happens when i try to play mupen64, it will show up but when i click play everything disapears

I dont know what the hell is causing this but i was hoping that some of you might, so does anyone know what is happening? or how i can fix it?

---

### Post by taurus on 2008-02-13
Why don't you try to play that video file with gmplayer from a terminal to see if there is any error message?

---

### Post by tjwoosta on 2008-02-13
ok this is what i get what does this mean?

```
tj@tj-laptop:~$ gmplayer
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/tj/Desktop/3.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  384x288  (aspect 1)  25.000 fps  600.0 kbps (75.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 384 x 288 (preferred colorspace: Mpeg PES)
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
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 384 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 384x288 => 384x288 Planar YV12 
[ws] Error in display.  0.050 ct:  0.004   2/  2 ??% ??% ??,?% 0 0              
[ws]  Error code: 11 ( BadAlloc (insufficient resources for operation) )
[ws]  Request code: 140
[ws]  Minor code: 19
[ws]  Modules: flip_page
tj@tj-laptop:~$
```

---

### Post by tjwoosta on 2008-02-15
can anyone help me?

---

### Post by kbless7 on 2008-02-15
What does Mupen64 say when you run it through the terminal?

---

### Post by -random on 2008-02-15
have you tried vlc? it works for everyting except .rmvb files.

---

### Post by tjwoosta on 2008-02-15
this is what it says when i try to play a rom
```
tj@tj-laptop:~/Downloads/mupen64-0.5$ ./mupen64

(mupen64:7561): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory
rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
file found
rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
rom loaded succesfully
80 37 12 40
ClockRate=f
Version:144b
CRC: 33f4c13 319ee7a7
name: TWINE               
Manufacturer: Nintendo
Cartridge_ID: 374f
Country : United States
size: 4096
PC= 80000400
md5 code:9D58996A8AA91263B5CD45C385F45FE4
eeprom type:0
init timer!
memory initialized
[glN64]: (WW) Couldn't open config file '/home/tj/Downloads/mupen64-0.5/./plugins/glN64.conf' for reading: No such file or directory
[glN64]: (II) Initializing SDL video subsystem...
[glN64]: (II) Getting video info...
[glN64]: (II) Setting video mode 640x480...
demarrage r4300
dynamic recompiler
Signal number 11 caught:
        errno = 0 (Success)
tj@tj-laptop:~/Downloads/mupen64-0.5$ 
```

---

### Post by tjwoosta on 2008-02-17
does anybody have any ideas? is this possibly because i have  intel 965 integrated graphics which is blacklisted for compiz?   I have tried turning off desktop effects but it did not seem to help.

---

### Post by steveneddy on 2008-02-17
VLC works for me really well.

I have issues with mplayer in 64 bit myself.

Did you [look here]("http://ubuntuforums.org/showthread.php?t=368607")?

---

### Post by tjwoosta on 2008-02-17
i wish i had installed 32 bit but its too late now i dont want to start over especially after all that i have gone through to get my resolution and refresh rate correct and getting compiz working with blacklisted video

anyway it is not just mplayer it is every movie player i can find  and mupen64,
 they all work untill i actually try to open a file, then it just disapears.
somehow i can watch the mplayer plugin for firefox but not the actual mplayer

---

### Post by tjwoosta on 2008-02-17
ahhh i have finally figured it out 

after all of the trouble i have finally found a media player that works! It is the GNOME MPlayer from synaptec,   none of the other mplayer versions would work,vlc wouldn't work , totem wouldn't work, but GNOME MPlayer works.

Thank God!

---

