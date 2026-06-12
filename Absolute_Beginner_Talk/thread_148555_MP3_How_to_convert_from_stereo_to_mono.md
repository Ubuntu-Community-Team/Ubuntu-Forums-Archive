---
title: "MP3: How to convert from stereo to mono"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by aben on 2006-03-22
Hi there,

  Please address me on how to convert my MP3 file (stereo) to mono. I have experienced of low playback quality in my hand phone since the device only capable of playing dual-mono MP3. Thank you in advance :)

---

### Post by IYY on 2006-03-22
If you're not afraid of the command line and writing a little script, you could easily use the lame encoder (type **man lame** in the command line to get a manual page for it) to do what you want.

Specifically, I think it's the -a option you're looking for. Here's its description:

> Mix the stereo input file to mono and encode as mono.
The downmix is calculated as the sum of the left and right channel,
attenuated by 6 dB.

Make sure to also use the --mp3input option to specify that you want to convert from mp3 to mp3.

---

