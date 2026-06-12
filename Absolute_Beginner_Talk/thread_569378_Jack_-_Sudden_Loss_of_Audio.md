---
title: "Jack - Sudden Loss of Audio"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-10-07
I had jack running perfectly with my delta 44 card. 

I turn it on today, and out of the blue I get an error message "Could not connect to jack server as client"

so i turned off "Real time monitoring" it runs now, but still no sound!

I checked alsamixer -c1 all the settings are the way they were before. 

here is the message log:


> 00:02:01.048 Patchbay deactivated.
00:02:01.089 Statistics reset.
00:02:01.196 Startup script...
00:02:01.196 artsshell -q terminate
00:02:01.248 MIDI connection graph change.
can't create mcop directory
Link points to "/tmp/ksocket-aamir"
00:02:01.738 Startup script terminated with exit status=256.
00:02:01.738 JACK is starting...
00:02:01.738 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n2 -m
00:02:01.753 JACK was started with PID=6231 (0x1857).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210066048, from thread -1210066048] (1: Operation not permitted)
cannot create engine
00:02:01.829 JACK was stopped successfully.
00:02:01.829 Post-shutdown script...
00:02:01.829 killall jackd
jackd: no process killed
00:02:01.954 MIDI connection change.
00:02:02.043 Post-shutdown script terminated with exit status=256.
00:02:03.994 Could not connect to JACK server as client. Please check the messages window for more info.
00:02:33.379 Startup script...
00:02:33.379 artsshell -q terminate
can't create mcop directory
Creating link /home/aamir/.kde/socket-aamir-desktop.
00:02:33.679 Startup script terminated with exit status=256.
00:02:33.679 JACK is starting...
00:02:33.679 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p1024 -n2 -m
00:02:33.682 JACK was started with PID=6246 (0x1866).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
00:02:35.728 Server configuration saved to "/home/aamir/.jackdrc".
00:02:35.729 Statistics reset.
00:02:35.737 Client activated.
00:02:35.765 Audio connection change.
00:02:35.767 Audio connection graph change.
00:02:40.056 Audio connection change.
00:02:53.903 Statistics reset.
**** alsa_pcm: xrun of at least 1.522 msecs
00:03:36.688 XRUN callback (1).
**** alsa_pcm: xrun of at least 0.839 msecs
00:03:46.976 XRUN callback (2).
**** alsa_pcm: xrun of at least 2.179 msecs
00:04:23.586 XRUN callback (3).

---

### Post by homerj742 on 2007-10-07
All of a sudden it's working. 

Possibly loose physical connection somewhere...

---

