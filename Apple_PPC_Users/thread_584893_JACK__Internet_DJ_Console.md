---
title: "JACK / Internet DJ Console"
date: 2007-10-21
forum: Apple PPC Users
---

### Post by Knoeki on 2007-10-21
hiya!

I'm DJ'ing for an internet radio station... now, so far, I'm stuck to using windows for streaming...

Well, I found Internet DJ console, but I'm having some troubles with it... these problems are most likely caused by JACK..

this is what I get when starting Internet DJ console:

```
The JACK sound server needs to be running in order to run IDJC.
In order to manually start it try something like:

		$ jackd -d alsa -r 44100 -p 2048

If you would like JACK to start automatically when you start IDJC try this:

	echo "/usr/bin/jackd -d alsa -r 44100" >~/.jackdrc

If you have already done this it is possible another application or non-JACK sound server is using the sound card.

Possible remedies would be to close the other audio app or configure the sound server to go into suspend mode after a brief amount of idle time.
```

when I do

```
jackd -d alsa -r 44100 -p 2048
```

in a console, I get:

```
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 2048 frames, buffer = 2 periods
Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
```

anyone know how to fix this? or.. any alternative apps?


btw, I think I've ran the app before, now it just gives the error and doesn't run at all... -_-'

---

### Post by komputes on 2007-12-14
I'm also in need of Internet Radio DJ software and ICDJ seems to bee the only native way to do this. I am able to connect to the icecast server, log in, I can hear myself as well (microphone)->(interwebs)->(live_stream) so all that good stuff works. What doesn't work is trying to import playlists (from vlc or rythmbox) or even dragging and dropping MP3's.

Since I followed all the instructions to the letter I'm not sure what I'm doing wrong. I made sure that all the dependencies were met. Can someone experienced with IDJC try it on Gutsy and report on this post if it works for them.

---

