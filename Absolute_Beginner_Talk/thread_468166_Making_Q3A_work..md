---
title: "Making Q3A work."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-06-08
Well, I installed quake3 following [this]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3")
tutorial, the problem is that when I start q3, the screen goes black, and then it returns to my desktop.

How do I fix this?

Thank You,

OmnificienT

---

### Post by lambros on 2007-06-08
How are you attempting to run the game?  Are you using a menu shortcut or are you running it from a terminal?
If you could run "quake3" from a terminal, and then post the output here, that might help us diagnose your problem.
Alternatively, there are a couple of other methods of installing Quake 3 that you could try:
You could go to [http://ioquake3.org/](http://ioquake3.org/) and follow the instructions there.
Or you could install OpenArena.  If you're running Feisty, it's in the repositories:
```
sudo aptitude install openarena
```

I highly recommend OpenArena ([http://openarena.ws/](http://openarena.ws/)), as it is completely Free Software (the game code and all data files are free-as-in-freedom).  And it's compatible with standard Quake 3 maps, as far as I can tell.

HTH,
Lambros

---

### Post by OmnificienT on 2007-06-08
```

pim@Celeron:~$ cd /usr/local/games
pim@Celeron:/usr/local/games$ cd quake3
pim@Celeron:/usr/local/games/quake3$ ls
baseq3            missionpack   quake3          quake3.xpm
CHANGES-1.32.txt  pb            quake3-smp      README-Id-7-26-01.html
Docs              Q3A_EULA.txt  quake3-smp.x86  README-linux.txt
INSTALL           q3ded         quake3.x86
pim@Celeron:/usr/local/games/quake3$ quake3
bash: quake3: command not found
pim@Celeron:/usr/local/games/quake3$ quake3.x86
bash: quake3.x86: command not found
pim@Celeron:/usr/local/games/quake3$

```

This is what I tried, I can't make it start, while in Nautilus it says that the files are executables.

---

### Post by aidanr on 2007-06-08
```
./quake3
``` not ```
quake3
```

---

### Post by OmnificienT on 2007-06-08
```

/home/pim/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
com_zoneMegs will be changed upon restarting.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
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
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

```

Well, the evil signal 11 seems to be causing the problem.

---

### Post by aidanr on 2007-06-08
> ***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
what graphics card do you have? you don't have 3d acceleration, you need to install your graphics drivers
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

actually for dapper: [https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html)

---

### Post by lambros on 2007-06-08
Looks like you don't have 3D acceleration enabled for your graphics card.  If you can, go to System->Administration->Restricted Drivers Manager
to enable 3D support for your graphics card.  Let us know if you have any problems.  To test your 3D acceleration, you could run
```
glxgears
```
from a terminal.

Lambros

---

### Post by OmnificienT on 2007-06-09
Thanks, it works perfectly now. Do remember to set fglrx as the driver.

---

