---
title: "[SOLVED] darn games won't even open!!! help!"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by cool2000m on 2007-12-19
I've been having the weirdest problem. my games won't do anything no matter how many times I click on them- even if they have worked before. Maybe it's an update or whatever but those darn things won't load. Help please?

oh, and btw, that thread-starting 'have you tried these threads yet?' message is helpful but it never stays. oh well...

---

### Post by gaten on 2007-12-19
I assume you're talking about the games in the "Applications->Games" menu? Try opening them in a terminal and see if any error messages pop out. 

For instance, to run "Mines":
```
gnomine
```


and see if any errors come up.

---

### Post by cool2000m on 2007-12-19
none come up, it's just the ones I downloaded that are 3d. tremulous worked before, why not now?

---

### Post by shae on 2007-12-19
3D acceleration could be broken.  Post the output of:
```
glxinfo | grep direct
```

---

### Post by cool2000m on 2007-12-19
I get this:

```

cool2000m@ubuntu:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

and for Tremulous, I get this:

```
tremulous 1.1.0 linux-x86 Nov 13 2006
----- FS_Startup -----
Current search path:
/home/cool2000m/.tremulous/base
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
execing autogen.cfg
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
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```

---

### Post by cool2000m on 2007-12-20
I am now installing an update (51 files!) that I am hoping will fix this problem; 3 of these are OpenGL drivers. Man, I am loving Ubuntu! If it weren't for all of the file's and apps I'd be losing, I'd switch over in a heartbeat!\\:D/

EDIT: no, this did nothing, and the readouts are still the same.

---

### Post by cool2000m on 2007-12-23
c'mon, I really need an answer to this! Help!

---

### Post by cool2000m on 2007-12-23
c'mon, guys. anybody?

Oh, and btw, I have a vt8378 [s3 unichrome] integrated video card.

---

### Post by cool2000m on 2008-01-10
okay, so I just upgraded to an official install and everything works fine. I think it's because I enabled effects.

---

### Post by bluewres on 2008-01-21
I am also having the same sorts of outputs for those terminal commands.  Are there any suggestions as to how to fix this?
thanks.

---

### Post by argie on 2008-01-21
> **bluewres said:**
> I am also having the same sorts of outputs for those terminal commands.  Are there any suggestions as to how to fix this?
thanks.

It looks like you don't have direct rendering, and fixing that depends upon what kind of graphics card you have. 

Also, if you're on some low-grade onboard graphics, you may never be able to play some games. This is unlikely unless you're using a very old computer, but I put it here just for completeness. And this thread is currently marked Solved, so it's unlikely people will read it. Try posting a new thread for your issue with information about your graphics card.

---

