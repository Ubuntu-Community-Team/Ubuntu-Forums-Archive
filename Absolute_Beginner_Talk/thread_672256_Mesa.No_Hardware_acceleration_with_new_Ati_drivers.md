---
title: "Mesa.No Hardware acceleration with new Ati drivers."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-19
> ----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


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
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Received signal 11, exiting...


When i installed new Ati drivers 8.1 with this way
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)
I get the error above,when i want to play Wolfenstein.
What is the problem?

---

### Post by Pevichaey5 on 2008-01-19
if your trying to run enermy territory, it says on my machine, with full ati 3d support, that i don't have 3d support, flightgear is nearly the same

i think the games have problems with my graphics card

maybe its the same for you

---

### Post by mister_pink on 2008-01-19
Have you got desktop effects on? Try turning them off if you do. Also you could try the suggestion in the error message - add "+set r_allowSoftwareGL 1" to the command to run it.

---

### Post by Ub1476 on 2008-01-19
That guide didn't work for me either when installing ATI 7.12. I removed it and let Envy to install the driver, as well as allowing it to configure my xorg.conf. Worked brilliant, even though Firefox scrolling and Compiz was more laggy than with the Restricted Driver (which I'm back with now).

---

### Post by rhc on 2008-01-19
> **Ub1476 said:**
> That guide didn't work for me either when installing ATI 7.12. I removed it and let Envy to install the driver, as well as allowing it to configure my xorg.conf. Worked brilliant, even though Firefox scrolling and Compiz was more laggy than with the Restricted Driver (which I'm back with now).

Envy doesn't install the new Ati drivers.

---

### Post by spiderbatdad on 2008-01-19
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

