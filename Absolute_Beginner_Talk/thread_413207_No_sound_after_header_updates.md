---
title: "No sound after header updates"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-04-18
I have searched a bit and found some threads relating to this but none that seemed to fix my problem.

A couple of days ago I updated the kernel headers and I noticed that my sound was not working anymore.

Anytime I try to listen to a sound file my laptop says that there is no sound card...

I recompiled the alsa drivers and that turned the mute button orange on my laptop.

Now the sound file plays but nothing comes out of the speakers???  I checked the master volume control and everything _seems_ to be configured right, but no sound

---

### Post by nonewmsgs on 2007-05-06
well...it seems like when the xorg wizard runs it autodetects and configures everything, so i would try that.

 sudo dpkg-reconfigure -phigh xserver-xorg

---

