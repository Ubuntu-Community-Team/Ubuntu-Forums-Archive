---
title: "JACK assistance"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-08-28
I am having a bit of trouble getting JACK to work
i have jackd and qjackctl installed
when i start jack from the command line i get 
```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: no locale found: /usr/share/locale/qjackctl_en_GB.UTF-8.qm

```
and when i click start in qjackctl i get an error message saying
> Could not connect to JACK server as client.
Please check the messages window for more info.
the output in the messages window is
```

00:01:29.777 Patchbay deactivated.
00:01:29.809 Statistics reset.
00:01:30.144 MIDI connection graph change.
00:01:30.149 MIDI connection change.
00:02:50.036 Startup script...
00:02:50.037 artsshell -q terminate
00:02:50.978 Startup script terminated with exit status=256.
00:02:50.986 JACK is starting...
00:02:50.987 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
00:02:51.003 JACK was started with PID=17643 (0x44eb).
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
00:02:51.193 JACK was stopped successfully.
00:02:51.195 Post-shutdown script...
00:02:51.195 killall jackd
jackd: no process killed
00:02:51.491 Post-shutdown script terminated with exit status=256.
00:02:53.204 Could not connect to JACK server
```
does anybody know what is going wrong??
thanks

---

### Post by Steveway on 2007-08-28
> the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Is any application with sound running? A media player or so?

---

### Post by simon303 on 2007-08-28
did have rhythmbox running, but i noticed that message and tried closing rhythmbox, but still failed to start jack
output was
```

00:14:47.473 Patchbay deactivated.
00:14:47.626 Statistics reset.
00:14:47.762 MIDI connection graph change.
00:14:47.847 MIDI connection change.
00:14:49.449 Startup script...
00:14:49.450 artsshell -q terminate
00:14:49.931 Startup script terminated with exit status=256.
00:14:49.932 JACK is starting...
00:14:49.933 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
00:14:49.953 JACK was started with PID=18112 (0x46c0).
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
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
00:14:50.048 JACK was stopped successfully.
00:14:50.049 Post-shutdown script...
00:14:50.050 killall jackd
jackd: no process killed
00:14:50.287 Post-shutdown script terminated with exit status=256.
00:14:52.014 Could not connect to JACK serve
```

---

### Post by Steveway on 2007-08-28
> Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
That sounds like an hardwareissue.
I don't know what you can do, try this:
sudo apt-get install libasound2-plugins

---

### Post by simon303 on 2007-08-28
same message

---

