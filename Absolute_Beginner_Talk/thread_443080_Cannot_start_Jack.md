---
title: "Cannot start Jack"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by urny on 2007-05-14
I get the following message when launching JACK.
Could someone help with some pointers.
I have installed everything I can find to do with JACK

11:45:20.816 Patchbay deactivated.
11:45:20.839 Statistics reset.
11:45:20.854 Startup script...
11:45:20.854 artsshell -q terminate
11:45:20.866 MIDI connection graph change.
can't create mcop directory
Creating link /home/urny/.kde/socket-urny-desktop.
11:45:21.093 Startup script terminated with exit status=256.
11:45:21.093 JACK is starting...
11:45:21.093 /usr/bin/jackd -dalsa -ddefault -r44100 -p1024 -n2
11:45:21.095 JACK was started with PID=10132 (0x2794).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... default|default|1024|2|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
11:45:21.140 JACK was stopped successfully.
11:45:21.140 Post-shutdown script...
11:45:21.140 killall jackd
jackd: no process killed
11:45:21.295 MIDI connection change.
11:45:21.349 Post-shutdown script terminated with exit status=256.
11:45:23.306 Could not connect to JACK server as client. Please check the messages window for more info.

---

