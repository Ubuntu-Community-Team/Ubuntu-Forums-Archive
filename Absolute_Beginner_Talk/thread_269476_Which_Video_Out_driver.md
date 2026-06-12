---
title: "Which Video Out driver?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-10-01
Hi everyone.
A couple of days ago I finally got Mplayer installed and working, after a lot of help and advice from this here forum. After the next start-up though, I got this; [COLOR="DarkOrange"]"Error opening/initializing the selected video_out (-vo) device."[/COLOR]
So I checked out the FAQ at mplayer and got this; [COLOR="Magenta"]"Q:
I've just installed MPlayer. When I want to open a video file it causes a fatal error: 
Error opening/initializing the selected video_out (-vo) device.
How can I solve my problem? 
A:
Just change your video output device. Issue the following command to get a list of available video output drivers: 
mplayer -vo help "[/COLOR]
 I got a list but I have no idea which is the driver currently in use nor which is the one I should choose.
[COLOR="Blue"]MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Pentium D/XE Smithfield; Xeon Nocona,Ir windale (Family: 15, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
        3dfx    3dfx (/dev/3dfx)
        xvmc    XVideo Motion Compensation
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        ggi     General Graphics Interface (GGI) output
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        aa      AAlib
        caca    libcaca
        dxr3    DXR3/H+ video out
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame[/COLOR] 

Guessing is always on the cards but recently I've become more cautious about impulsively reconfiguring parts that I don't fully understand.

Second point regards the correct syntax. I've been having considerable trouble with this!!
All advice appreciated.

---

### Post by Mr Frosti on 2006-10-01
Video out is simply the method of displaying Video for MPlayer. You can control which specific method is used with the "-vo" switch. The easiest way to do this is to have "gmplayer" installed, and go into Preferences and select your Video out preference. 

A safe bet is always the "X11" vo method. Try this and see how this works.

---

### Post by carloslosgrande on 2006-10-02
Thank you Mr Frosti, but I'm still a little unsure of syntax. When you say just use the -vo command to change it, could you be more specific.
I'm really unfamiliar with command syntax and have been having some trouble with it.

I looked around for gmplayer but can't seem to find it. Dapper packages, softpedia, sourceforge, etc.

Thanks again.

[FONT=Comic Sans MS]Boy am i Dumb.
I don't know about Gmplayer but I found the preferences field, [it was there all the time], and have experimented with various vo's. X11 is the one for me.
Thanks again Mr Frosti!:-D[/FONT]

---

### Post by jay019 on 2007-04-17
This post solved a different sort of problem for me. Was looking for a program to onvert video to animated gif. Little did I know it was sitting on my computer all along. Hot damn!!!

---

