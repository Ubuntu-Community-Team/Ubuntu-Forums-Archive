---
title: "does anyone know how i can fix my mplayer?"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-07-13
whenever i run mplayer it get the message in the attachment included. it says look for vo x11 but i have no idea how to do that. it keeps saying my video card doesnt have the right driver.  i ran the command it wanted in konsole and  that is also included in the attachment. also i have no control on the play/pause/fast foward aspect of any video i am playing in mplayer. it just opens and starts playing and the controls at the top are more like visuals than usual tools. could that be related to the video problem?

can anyone help me? it says try vo x11, where can i find that driver?

here is the output for "mplayer -vo help"

> 
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
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
        md5sum  md5sum of each frame

91 audio & 204 video codecs


i think i need all the video codecs.

---

### Post by simonn on 2006-07-13
vo = video output, it is a parameter to mplayer

Try running mplayer from the command line with like so:

> 
mplayer -vo x11 [other paramaters....]


If that works, read the mplayer documentation and add it to the configuration file so that the setting is kept permanently.

---

### Post by maddbaron on 2006-07-13
this is what I got.

> 
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing [other.
File not found: '[other'
Failed to open [other

Playing paramaters....].
File not found: 'paramaters....]'
Failed to open paramaters....]


Exiting... (End of file)


---

