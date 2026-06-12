---
title: "Choppy DVD playback"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2007-03-05
I have an older machine that I'm using as a DVD player connected to my TV.

The box is slow and doesn't have much RAM (550MHz AMD with 256MB RAM).  I'm guessing this could have a lot to do with it.  However, it does have a GeForce4 MX 128MB graphics card in it.

DVD playback is passable, but the video is constantly glitching where it freezes for a half-second or so.  Sometimes the sync is off continuously.

I have the NVidia drivers installed (the splash screen shows on boot-up) and TV-out works to my TV.  What can I look at to determine the cause?

I have tried Xine (Kaffeine, GXine, Xine) and VLC with the same results.

---

### Post by Monsieur le Comte on 2007-03-05
On closer examination, it appears that maybe OpenGL isn't working?  How can I know?

---

### Post by Shatrat on 2007-03-05
> **Monsieur le Comte said:**
> On closer examination, it appears that maybe OpenGL isn't working?  How can I know?

glxinfo | grep rendering

If it isn't working try this,
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Monsieur le Comte on 2007-03-06
when I run glxinfo I get a lot of what appear to be error lines saying something to the effect that:

"Xlib: extension "GLX" missing on display ..."

So I take it that it's something with my drivers not being set up correctly?  I'm going to take a look at installed packages again, and at my xorg.conf file.

---

### Post by panch0 on 2007-03-07
Try to enable the extension or maybe use the XVideo output instead. In KPlayer it's the default.

---

