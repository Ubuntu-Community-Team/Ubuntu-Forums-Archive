---
title: "How to install MPlayer"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by hongquan1987 on 2007-07-10
I want to install MPlayer by compiling, but when ./configure, I receive error: gcc not found, although inside Synaptic, I see gcc

---

### Post by Outrunner on 2007-07-10
```
sudo aptitude install build-essential
```

Then you can continue with ./configure, etc

But why not just install it from the repositories?

```
sudo aptitude install mplayer
```

---

### Post by alienexplorers on 2007-07-10
The easiest way to install mplayer without playing with compiling it would be to load it from symantic with aptitude ans stated above.

---

### Post by AlexenderReez on 2007-07-10
my mplayer preference -->

video = xv  x11/xv

audio = alsa


what i like the most about mplayer is it play better .rm video than realplayer itself:guitar::guitar:

---

