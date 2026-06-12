---
title: "Creative Video Webcam 5 not working in Feisty"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by RealMabu on 2007-09-29
I have Creative Video Blaster Webcam 5 (ooold webcam) and it looks like it's installed and detected but I can't access it.
I have read half-a-dozen threads but I'm getting lost, so I'm asking help from scratch.
Just to be precise about the device, the windows driver that can be downloaded from Creative is this:
[http://uk.europe.creative.com/support/downloads/download.asp?MainCategory=218&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Windows+XP&region=3&Product_Name=Video+Blaster+WebCam+5&Product_ID=1896&modelnumber=&driverlang=1033&OS=10&select=0&x=28&y=12]("http://uk.europe.creative.com/support/downloads/download.asp?MainCategory=218&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Windows+XP&region=3&Product_Name=Video+Blaster+WebCam+5&Product_ID=1896&modelnumber=&driverlang=1033&OS=10&select=0&x=28&y=12")

Then to linux.
lsusb says:
```
root@aldo-feisty:/home/aldo# lsusb
Bus 003 Device 002: ID 04a9:30f6 Canon, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
This device ID seems to be compatible with driver:
[http://www.rastageeks.org/ov51x-jpeg/index.php/Working_Webcams]("http://www.rastageeks.org/ov51x-jpeg/index.php/Working_Webcams")
But I'd prefer, if possible, not to install a hacked driver, but use native ubuntu drivers.

dmesg says:
```
root@aldo-feisty:/home/aldo# dmesg | grep video
[    0.210866] Boot video device is 0000:04:00.0
[   15.589743] Linux video capture interface: v2.00
[   16.011710] ubuntu/media/ov511/ov511.c: USB OV518 video device found
root@aldo-feisty:/home/aldo# 
```

and lsmod says:
```
root@aldo-feisty:/home/aldo# lsmod | grep videovideo                  16388  0 
videodev               28160  1 ov511
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
root@aldo-feisty:/home/aldo# 
```

/dev/video0 is as such:
```
crw-rw---- 1 root video      81,   0 2007-09-30 00:36 video0
```

and I am in "video" group:
```
root@aldo-feisty:/home/aldo# cat /etc/group | grep video
video:x:44:aldo
root@aldo-feisty:/home/aldo# 
```

Now I launch camorama from command line and I get the "Could not connect to the device /dev/video0" error.
Terminal output is:
```
root@aldo-feisty:/home/aldo# camorama

(camorama:8273): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@aldo-feisty:/home/aldo# 
```

Issuing camorama as user 'aldo' I get the same error from camorama but no terminal output.

Trying to show video through mplayer as suggested by [https://help.ubuntu.com/community/Ov51x]("https://help.ubuntu.com/community/Ov51x") produces nothing but an error:
```
root@aldo-feisty:/home/aldo# mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
unable to open '/dev/video0': Function not implemented


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
root@aldo-feisty:/home/aldo# 
```
This time, same identical output issuing as 'aldo'.

Now, here is where I am lost.
What do I need to do next?
-install manually Ov51x driver?
-which driver, the hacked one or the 'default' one?
-suggestions?

Thank you!

---

