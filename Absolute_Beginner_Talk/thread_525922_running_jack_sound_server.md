---
title: "running jack sound server"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-08-14
hey i tried installing jack, but i couldnt find it in synaptic, so i used sudo apt-get install jack. it installed, now how do i get it running? do i need a GUI? and if not, where can i get one?

---

### Post by Luksion Knight on 2007-08-15
ok i figured out i needed the jack gui, but now when i try to start it, it returns the following error: 23:30:25.471 Patchbay deactivated.
23:30:25.480 Statistics reset.
23:30:25.516 MIDI connection graph change.
23:30:25.688 MIDI connection change.
23:30:36.431 Startup script...
23:30:36.431 artsshell -q terminate
23:30:36.676 Startup script terminated with exit status=256.
23:30:36.677 JACK is starting...
23:30:36.677 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
23:30:36.681 JACK was started with PID=13610 (0x352a).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
23:30:36.706 JACK was stopped successfully.
23:30:36.706 Post-shutdown script...
23:30:36.706 killall jackd
jackd: no process killed
23:30:36.921 Post-shutdown script terminated with exit status=256.
23:30:38.730 Could not connect to JACK server as client. Please check the messages window for more info

---

