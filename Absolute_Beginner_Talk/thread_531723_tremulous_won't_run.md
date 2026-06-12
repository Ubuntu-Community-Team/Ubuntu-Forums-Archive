---
title: "tremulous won't run"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by fumoffu on 2007-08-21
I just installed tremulous, but every time I run it it immediately crashes. This is what it gives me after running it in Konsole. 
```
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
```

I'm running kubuntu 7.04 with kernel  2.6.22-9 generic 

output of lspci
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev              80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev              80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev              80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev              80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Contro             ller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200             M]
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC              (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139             C+ (rev 10)
```

---

### Post by switchcode on 2007-08-21
Did you try what the error output suggests?
```
You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
```
So open a terminal and type
```
tremulous +set r_allowSoftwareGL 1
```

I installed Tremulous from synaptic. I use a compaq presario laptop with Intel express graphics and it runs beautifully; Excellent game btw.. Aliens all the way =)

---

### Post by fumoffu on 2007-08-21
> **switchcode said:**
> Did you try what the error output suggests?
```
You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
```
So open a terminal and type
```
tremulous +set r_allowSoftwareGL 1
```

I installed Tremulous from synaptic. I use a compaq presario laptop with Intel express graphics and it runs beautifully; Excellent game btw.. Aliens all the way =)
Hmm, well it kinda worked =) It started but it was really slow and very glitchy. Any other ideas?     *stares* Humans!!

---

### Post by switchcode on 2007-08-22
Hm Im no expert here; but make sure you have the proper drivers for your graphics card. Go to hardware information, find your graphics card and google for "<YOUR GRAPHICS CARD> ubuntu drivers".. Im sorry I cant be of more help; When installing ubuntu on this machine, ubuntu recognised my graphics card straight away. Obviously when you have installed drivers for your card, just run Tremulous normally without the extra command line options.
 ALIENS FOREVER! -stares back-

---

### Post by splintercellguy on 2007-08-22
Have you installed restricted drivers? It seems that DRI is off.

---

### Post by fumoffu on 2007-08-22
Yeah, I've already installed the restricted drivers. And yet is says I'm using the mesa driver...*confusing* Should I try installing them again? I'll try that and let you know how it turns out. :)    *pulls out Lucifer cannon*

---

### Post by fumoffu on 2007-08-22
Ok, I tried that but to no avail, it gave me the same error after I tried to run trem. :(
Could it be that I'm not installing the driver correctly?
These are the instructions I followed  [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html#176980](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html#176980)

---

### Post by splintercellguy on 2007-08-22
Post the output of glxinfo | grep rendering.

---

### Post by fumoffu on 2007-08-22
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: no

Ok, I just removed and reinstalled the drivers for the third time.  Updated output of glxinfo | grep rendering

direct rendering: Yes


Tremulous appears to run now. However, I only get about 5-10 fps when I'm playing, which makes it very unplayable. Oh, and when I exit tremulous I think my window manager crashes, because I can longer see the top bar in any app I run. If anyone has any ideas, they would be much appreciated :)

---

### Post by fumoffu on 2007-08-22
bump

---

### Post by fumoffu on 2007-08-23
Bumpeth

---

