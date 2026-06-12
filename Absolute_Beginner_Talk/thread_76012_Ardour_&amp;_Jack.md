---
title: "Ardour &amp; Jack"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-10-14
Ok i have installed Ardour, Jack, and qjackctl.(trough synaptic)

But wheni try and run jack it gives me this error

This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* config file /etc/jackrc is of unknown version None.
 *info* matching dir found: /home/jason/jack/jack-0210c601
 *info* maybe cdparanoia is not installed?
 *error* could not read CD's TOC.

i need jack running to use Ardour

---

### Post by dolson on 2005-10-15
maybe cdparanoia is not installed?

---

### Post by jasonpeinko on 2005-10-15
it is
installed

---

### Post by jasonpeinko on 2005-10-15
i was looking on google and it said to use this command with jack

jackd -R -d alsa -d ens1371 -r 48000 -p 1024 &

---

### Post by jasonpeinko on 2005-10-15
```

jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

[1] 8818
jason@ubuntu:~$ loading driver ..
apparent rate = 48000
creating alsa driver ... ens1371|ens1371|1024|2|48000|0|0|nomon|swmeter|-|32bit
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM ens1371
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM ens1371
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa

```
i get that

---

### Post by BoyOfDestiny on 2005-10-16
try sudo killall esd

search the forums if you want more details.

---

### Post by jasonpeinko on 2005-10-16
nope same thing

---

