---
title: "Sound Problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by phallictractor on 2007-08-14
I just downloaded stepmania ( a ddr sim for pc) and when i start it the sound doesnt work. It works for everything else but it doesnt work on the game.the error log says 

00:00.167: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy

00:00.167: 

00:00.167: //////////////////////////////////////////////////////

00:00.167: Exception: Couldn't find a sound driver that works

00:00.167: //////////////////////////////////////////////////////

i have a dell optiplex g280.
any help is much appreciated.

---

### Post by Jeek Elemental on 2007-08-15
are you using alsa as default sound driver?

if so, get ALSA-OSS from the Synaptic package manager.

start your program with

aoss <program name>

this will translate oss calls to alsa and hopefully make sweet :guitar:

---

