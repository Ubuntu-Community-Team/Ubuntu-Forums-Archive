---
title: "Problem streaming from WinTV-NOVA-S-Plus DVB-S"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by riknos on 2007-12-25
Hi,

I am trying to get MythTV working. Backend and frontend loaded up ok on Gutsy desktop but I have had no success after several attempts to get any channels scanned into the MythTV Channels table using mythsetup . 

However, I think I have a more basic problem as although I can scan all the available channels and szap them into channels.conf  I have had no success piping an output stream to mplayer, xine or kaffeine. Either a player application  starts up then disappears or if a player app does start it does not display the stream (e.g. BBC 1 London). I have tried adding full path to mplayer but that makes no difference. What other file does the output refer to? See terminal output below.

Would appreciate any help.

richard@main-pc:~$ dvbstream -f 10773 -a 601 -v 600 -o | /usr/bin/mplayer -
dvbstream v0.6 - (C) Dave Chapman 2001-2004
Released under the GPL.
Latest version available from [http://www.linuxstb.org/](http://www.linuxstb.org/)
FRONTEND DEVICE: : Device or resource busy
Tuning to 10773 Hz
FE_GET_INFO: : Bad file descriptor
dvbstream will stop after -1 seconds (71582788 minutes)
Output to stdout
Streaming 2 streams
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...

---

