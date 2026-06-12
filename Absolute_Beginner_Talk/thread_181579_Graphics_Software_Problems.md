---
title: "Graphics Software Problems"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by flaran on 2006-05-24
OK, so I finally got my HP ZV6000 laptop working with Ubuntu-- and let me tell you, it was a beast.  Now my problem is with running this program.  Here is the error I get:

```

***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

```

Alright, so it is saying that Mesa is my problem.. should I just allow Mesa to run this, or is there some alternative to let me use hardware acceleration?

---

### Post by flaran on 2006-05-24
OK, running without hardware acceleration is obviously not an option with this program..  Is there any way to enable hardware acceleration with mesa?

---

