---
title: "ATI vs. glxgears"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-02-13
I read somewhere taht to test your graphics card, you run glxgears on the terminal and see the output.
Whenever I start it, it seems to be going allright. The gears are spinning normal but after about two seconds of spinning, they considerebly slow down. They run so slow you can  actually see the gears refreshing. When I quit, I get the following error:

jaygo333@Ubuntu:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).
jaygo333@Ubuntu:

What's killed or shutdown and how do I fix It.

:h34r: Jaygo333 :h34r:

---

### Post by sharke on 2006-02-13
[QUOTE=Jaygo333]I read somewhere taht to test your graphics card, you run glxgears on the terminal and see the output.
Whenever I start it, it seems to be going allright. The gears are spinning normal but after about two seconds of spinning, they considerebly slow down. They run so slow you can  actually see the gears refreshing. When I quit, I get the following error:

jaygo333@Ubuntu:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).
jaygo333@Ubuntu:

What's killed or shutdown and how do I fix It.

:h34r: Jaygo333 :h34r:[/QUOTE]
Try this command glxgears -iacknowledgethatthistoolisnotabenchmark
iam not kidding this works
Regards
Sharke

---

### Post by Jaygo333 on 2006-02-13
[LEFT][/LEFT]

Nice Trick but still same response. 
the gears are spinning at like 1 Frame Per Second.

Wow.!
When I quit, it gave me these frame rates.
jaygo333@Ubuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
992 frames in 5.1 seconds = 192.837 FPS
476 frames in 5.2 seconds = 91.407 FPS
480 frames in 5.9 seconds = 81.470 FPS
480 frames in 9.6 seconds = 49.930 FPS
720 frames in 5.6 seconds = 129.407 FPS
720 frames in 5.6 seconds = 128.626 FPS
720 frames in 5.4 seconds = 132.715 FPS
720 frames in 5.7 seconds = 126.809 FPS
720 frames in 5.5 seconds = 130.406 FPS
720 frames in 5.6 seconds = 127.568 FPS
720 frames in 5.8 seconds = 124.198 FPS
600 frames in 7.0 seconds = 85.545 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
jaygo333@Ubuntu:~$

But at the end, it still sas its explicitly killed. 
What's Wrong. 

:h34r: Jaygo333 :h34r:

P.S. This thing really suprised me, when I run Doom 3 in Windows(bleH) I get like 30FPS. 
These say I get upto 192FPS. Is this true.
I gotta get me some linux native games, FAST.!

---

### Post by firetux on 2006-02-13
> glxgears -iacknowledgethatthistoolisnotabenchmark

glxgears -printfps does the same;) 
How much fps does it give?

Can you give the output from "fglrxinfo"?

---

### Post by sharke on 2006-02-13
If fglrxinfo command not found try glxinfo.
Thanks for glxgears -printfps sure is easier to remember.
Regards
Sharke

---

### Post by anodizer on 2006-02-13
Those fps are kinda bad. It seems your 3d accelleration doesn't work as it should. Type in the terminal fglrxinfo , if your config is correct you'll see something like: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5642 (8.22.5)

Where (8.22.5) is the version of the ati fglrx driver installed. If you see smthn like Mesa or DRI the problem is your xorg.conf or your drivers installation.

---

### Post by firetux on 2006-02-13
I agree with anodizer: those fps are really bad, I'm around 4000+ with an ati X700 mobility, nvidia users can get up to 10.000 fps!!!

Try fglrxinfo or glxinfo as sharke says:
if you dont get:
```
OpenGL vendor string: ATI Technologies Inc.
```
but something with mesa you don't have 3D accel.

---

