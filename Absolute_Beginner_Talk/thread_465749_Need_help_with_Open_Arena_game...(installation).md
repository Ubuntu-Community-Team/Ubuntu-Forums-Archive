---
title: "Need help with Open Arena game...(installation)"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by SirNintendo85 on 2007-06-06
So I was viewing the Add/Remove programs list, and I saw this game, so I wanted to give it a try.  It downloads everything correctly, but when I double click to play, the screen goes black for about 2 seconds, then comes back to where I was.   Like it was trying to boot up but failed or something.  I have gotten other games to work, and I'm wanting to play this with a buddy of mine, so any help would be much appreciated!  Thanks.

---

### Post by Ripfox on 2007-06-06
Try dragging the launcher into a terminal, hit enter and post the output here. (I think that will work to launch it from a terminal the easy way without switching directories...if i am wrong someone correct me here please)

---

### Post by SirNintendo85 on 2007-06-06
I tried doing that, same result.  Nothing else popped up in terminal after that giving any indication of anything.

---

### Post by SirNintendo85 on 2007-06-06
Here's a little morning bump.

---

### Post by SirNintendo85 on 2007-06-06
And one more bump before work.  Please help me guys!

---

### Post by Bachstelze on 2007-06-06
Try to run it from a terminal :

```
openarena
```

Any error message ?

---

### Post by phr0ze on 2007-06-06
Do you have the proper graphics drivers installed?

---

### Post by Ripfox on 2007-06-06
Sounds like a graphics driver problem possibly here too...

---

### Post by SirNintendo85 on 2007-06-06
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



Here's my error

---

### Post by SirNintendo85 on 2007-06-06
I'm pretty sure the lack of OpenGL is causing it, but how do I get that for Ubuntu?

---

### Post by Ripfox on 2007-06-07
Ah ha - what kind of graphics card do you have?

---

### Post by SirNintendo85 on 2007-06-07
I think it is a Via Chrome 9 HC IGP card.

---

### Post by SirNintendo85 on 2007-06-07
Bump, still not able to get this to run.

---

### Post by MilesTeg on 2007-06-08
take a look at the [FAQ](http://openarena.wikia.com/wiki/FAQ#I_get_the_error_message_.22could_not_load_OpenGL_subsystem.22)

maybe this helps
bye
MilesTeg

---

### Post by original_jamingrit on 2007-06-08
> **SirNintendo85 said:**
> Calling SDL_Init(SDL_INIT_VIDEO)...
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



Here's my error

I don't know this stuff very well, but according to that error message it's trying to use hardware acceleration, and can't.  I see that one line in the error, trying to tell you to run in the terminal 

```
openarena +set r_allowSoftwareGL 1
```
  I have Openarena installed on my linux box (which I spilled water on recently), but I'm on a public computer and I can't find out what would happen if you ran that line in the terminal.  Worth a try, I suppose.

Those lines at the end do not mean that you're missing the OpenGL library, if you installed OpenArena through Synaptic or the Add/Remove Programs the appropriate library packages would be automatically downloaded as well.  It is likely that this is a hardware problem that is preventing you from running the program normally.

---

