---
title: "[SOLVED] Very Odd error?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-10-20
hey there, ive been running compiz-fusion and AWN and emerald on gutsy no problems, well cept for that AWN occasionally crashes, but other than that, all is running well, but when i typed glxgears into the terminal i got this:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
43818 frames in 5.0 seconds = 8762.468 FPS
45107 frames in 5.0 seconds = 9015.558 FPS
46554 frames in 5.0 seconds = 9299.527 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":1.0"
      after 284191 requests (283004 known processed) with 0 events remaining.


now ive noticed that the Xlib:  extension "XFree86-DRI" missing on display ":1.0". error usually crops up when trying to play with pSX or something, and then nautilus crashes and boots me out, 

heres the output of my fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT
OpenGL version string: 2.0.6747 (8.40.4)


i installed the fglrx driver using Envy, which works fine


anyone know what might be the problem?

---

### Post by dynamethod on 2007-10-20
can i not use DRI and XGL at the same time?

---

### Post by shae on 2007-10-20
Yes, you cannot use both at the same time.

---

