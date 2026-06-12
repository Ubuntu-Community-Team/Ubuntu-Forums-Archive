---
title: "asus 1011px int mic problem"
date: 2011-12-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pinkpan on 2011-12-28
Alsa version 1.0.23, already tried alsamixer solution, pulseaudio getting down one channel at time. I've maked an update after the first unpacking.
Audio streams from the internal speakers normally, but mic doesn't work, no level, I've tried sound rec too......nothing.
Have I to update alsa???

---

### Post by pinkpan on 2011-12-31
ok, semi-solved....
I've reinstalled ubuntu from recovery and discovered that the original codec is alc269vb....don't know why after kernel update codec becomes alc259.

With 269vb it's all ok, int mic, speakers etc etc.

I would know how to update kernel without lose audio configuration.

Thanks.

---

### Post by gsoundsgood on 2012-02-01
isn't there any other solution that actually fixes this issue?

---

