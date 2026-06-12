---
title: "[SOLVED] tremulous doesnt work/graphics card"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by linux.convert on 2007-10-09
I installed Tremulous thru synaptic manager, and this is what I got...

USER@LAPTOP:~$ tremulous
tremulous 1.1.0 linux-x86 Nov 13 2006
----- FS_Startup -----
Current search path:
/home/USER/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 8/8/8 Color bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by skymera on 2007-10-09
what is your graphics card?

have you fgot the correct/latest driver?

---

### Post by linux.convert on 2007-10-11
I have a ATI Radeon XPRESS 200M 5955 (PCIE), and thats what terminal tells me, not just what I think I know. Im not sure about drivers, how to download them or whatever, since it doesnt work like windows.

---

### Post by Daveth on 2007-10-11
might be worth having a look at this.....

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

for drivers

---

### Post by moto89 on 2007-10-11
I had this problem the first time I ran Tremulous too. The problem was very easily fixed for me. I simply went system>administration>restricted drivers manager. The proper NVIDIA driver was already there just not in use. One click and my problems were solved. Check out the above post for info on getting the driver if it is not present.

---

### Post by linux.convert on 2007-10-12
that last one did it. i went to restricted drivers manager and that solve everything, it even seems to run fine. thanks alot.

---

