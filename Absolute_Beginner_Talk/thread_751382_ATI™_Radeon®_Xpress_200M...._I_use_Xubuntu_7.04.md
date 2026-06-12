---
title: "ATI™ Radeon® Xpress 200M.... I use Xubuntu 7.04"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Draken2910 on 2008-04-10
okay here is the deal,I have a Radeon® Xpress 200M, i have installed wolfenstein enemy territory and when i run it in the terminal like im supposed to start it. it gives me an "OpenGL" problem then it closes. i tried running it software mode but obviously the frames per second that i was getting was making me wanna rip my eyes out.

I have installed my driver using envy and such and says that the same version is already installed. I dont know what to do. Im not giving up on linux so dont worry about me begging and threating to quit. Ill learn this stuff but i need some help on what to do. I have switched from fluxbuntu to xubuntu 7.04 and im glad i did, so im not entirely a beginner and know my way around. 

Here are the specs on my computer if you all need them.

[http://support.gateway.com/s/Mobile/Q106/Blade/1014029Rsp2.shtml](http://support.gateway.com/s/Mobile/Q106/Blade/1014029Rsp2.shtml)

---

### Post by Draken2910 on 2008-04-10
oh and heres what i get after installing it

captaind@xubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

it doesnt say ATI thats the wierd part

---

### Post by stchman on 2008-04-10
> **Draken2910 said:**
> okay here is the deal,I have a Radeon® Xpress 200M, i have installed wolfenstein enemy territory and when i run it in the terminal like im supposed to start it. it gives me an "OpenGL" problem then it closes. i tried running it software mode but obviously the frames per second that i was getting was making me wanna rip my eyes out.

I have installed my driver using envy and such and says that the same version is already installed. I dont know what to do. Im not giving up on linux so dont worry about me begging and threating to quit. Ill learn this stuff but i need some help on what to do. I have switched from fluxbuntu to xubuntu 7.04 and im glad i did, so im not entirely a beginner and know my way around. 

Here are the specs on my computer if you all need them.

[http://support.gateway.com/s/Mobile/Q106/Blade/1014029Rsp2.shtml](http://support.gateway.com/s/Mobile/Q106/Blade/1014029Rsp2.shtml)

I have an Xpress 200M in my Toshiba laptop and it plays openGL games.

Use Envy to install the proprietary ATI drivers.

Make sure to uninstall any ATI driver before installation using Envy.

---

### Post by Draken2910 on 2008-04-10
for everyone to know

I found ENVY and used it to install my drivers for my card and it worked wonders

> I have an Xpress 200M in my Toshiba laptop and it plays openGL games.

Use Envy to install the proprietary ATI drivers.

Make sure to uninstall any ATI driver before installation using Envy.

and you need not have to uninstall any drivers for ENVY does it for you. it uninstalled the fglrx and connected to the server with extreme speed of 600 k/b sec wirelessly and was the simplest install i have ever used in my life *Gives a firm handshake to makers of ENVY and Xubuntu*

to check to make sure that the drivers have been installed successfully i went to my restricted drivers manager and when i put in my password it brought up "There are no restricted drivers on your system to configure" Just to throw that out there for everyone

---

### Post by joshrobinson on 2008-04-10
> **Draken2910 said:**
> oh and heres what i get after installing it

captaind@xubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

it doesnt say ATI thats the wierd part

yeah your drivers are busted, they installed wrong
i dont get why people use envy, it causes more problems then good, and i personally will never use it

i have the same exact video card in my laptop, and installing the xorg-driver-fglrx package works every time

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release


```
thats what fglrxinfo will output when they are installed correctly

---

### Post by Draken2910 on 2008-04-10
can you please post the correct way that it should be handled then???? because i tried wolfenstein et again and it give me the same dang message as before..... all i wanna do is be able to shoot people lol

---

### Post by stchman on 2008-04-10
> **joshrobinson said:**
> yeah your drivers are busted, they installed wrong
i dont get why people use envy, it causes more problems then good, and i personally will never use it

i have the same exact video card in my laptop, and installing the xorg-driver-fglrx package works every time

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release


```
thats what fglrxinfo will output when they are installed correctly

Envy installs the latest drivers while you are limited to one version of the driver in the repos.

Envy is excellent.

---

### Post by Draken2910 on 2008-04-10
i used envy and i installed the latest driver but it gives me this

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
[B][I][I] You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.[/I][/I][/B]
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

