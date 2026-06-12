---
title: "Mplayer keeps crashing when using dvds"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-16
Mplayer crashes when I play dvd's.  I tried in a terminal so I could see what was happening and the last part said this:

...
MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

What could be the problem?

---

### Post by dlpfmVfH on 2006-06-16
which mplayer did you install, the ones from the repo's ...
or did you compile it yourself...

if it is from the repo's check if you installed libdvdread...
or search for dvd in synaptic...and install any usefull packages...concerning dvd's

---

### Post by WADemosthenes on 2006-06-16
I got it from automatix.

I got all the apps that looked usefull for dvds, no luck.

---

### Post by dlpfmVfH on 2006-06-16
maybe if you set mplayer's config the video output to xv,
or to gl2...

maybe that helps..

or it is related to this :

[https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/38939](https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/38939)

---

