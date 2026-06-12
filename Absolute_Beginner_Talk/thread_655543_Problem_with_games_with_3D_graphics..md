---
title: "Problem with games with 3D graphics."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2008-01-01
I recently installed Armagetron and then Open Arena. I noticed in Armagetron that the graphics looked different (the grid was only visible in the immediate vicinity of my lightcycle) but thought that maybe I was wrong (it had been awhile since I played the game). However, I installed Warzone 2100 and was shocked at how slow it ran, I have a pretty decent video card (decent enough to run most last gen games like Morrowind, Halo etc..) and I know that this game is not even up to the graphics that those games can render. Anyways, I also installed Open Arena and it won't even open the game up. I get this message in the console when I try to run it:

ioQ3 1.33+oa linux-i386 Dec  7 2007
----- FS_Startup -----
Current search path:
/home/skaldicpoet9/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (76 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (191 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (11 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1496 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (9 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (620 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (171 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (73 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (926 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
3573 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
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
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
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
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


The strange thing is it seems that this issue is only related to 3D games. I have Gnometris, Battle for Wesnoth and Freeciv an they all work excellently. So I am thinking it is an issue with my 3D graphics acceleration. I am looking forward to playing Open Arena so any help is much appreciated :)

---

### Post by t0p on 2008-01-01
From the error messages you just reproduced, I get the impression you haven't enabled the Restricted Drivers Manager.  It's located under **System > Administration > Restricted Drivers Manager**.  Some people, who want a totally Free system, say it's okay to make do with the default driver.  But my experience is that 3G graphics are impossible without the acceleration provided by the restricted drivers.

---

### Post by LordTyrans on 2008-01-01
Huuum I'm not very experienced with Linux, but it does look like you haven't installed your graphics card drivers. Therefor no opengl support for 3d games. So...

1.Have you installed your G card drivers if yes then try adding "+set r_allowSoftwareGL 1"
to the command line when starting the game as it states in the error message. This should use software acceleration instead Although it would be allot slower.

2. If no go to the manufacturers site and look for some Linux drivers. I don't know about Ati drivers but nvidia drivers are very easy to install + the site has instructions on how to do it:).

3.If you had the drivers installed and you did what i suggested but it still did not work then the last thing would be to try and reinstall the drivers encase some of the packages have become corrupted, Which is very unlikely but it could happen.

Other than that i can't help you, anyway hope that helped.

Edit: Dang he beat me to helping

---

### Post by skaldicpoet9 on 2008-01-01
Hmm, it says that my ATI driver is enabled.

Do you think that they problem may be this:

Earlier I accidentally disabled the ATI restricted driver so it was uninstalled apparently.

I got a message saying that I needed to restart my system for the changes to come into effect but instead I figured I would just reinstall the driver again befire I restarted. So I reinstalled it and then restarted the comp but maybe it still thought it was finalizing the uninstall? Maybe I should just uninstall the driver, restart and then reinstall it again?

---

### Post by LordTyrans on 2008-01-03
Yeah,

That might have caused it but it is very unlikely, Although it is possible.

All i can suggest is to reinstall the restricted ati drivers, as it wont hurt to do so and it is normally quite an easy thing to do.

That SHOULD enable opengl acceleration.

Remember to look for the opengl libraries with the Synaptic packet manager, they might have been removed.

But unfortunately i have never used an ati card with Linux so am not sure what else to suggest.

---

