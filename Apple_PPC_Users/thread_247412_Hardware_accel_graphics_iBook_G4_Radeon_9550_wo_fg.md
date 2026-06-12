---
title: "Hardware accel graphics iBook G4 Radeon 9550 w/o fglrx"
date: 2006-08-30
forum: Apple PPC Users
---

### Post by ebel_ on 2006-08-30
I've got an iBook G4 with Radeon 9550 video card, I got the laptop in Aug 2005. After a default install of Dapper, you won't have direct rendering (ie hardware accelerated graphics), but there is experimental support for R300s in the latest version of Xorg that dapper ships with. I had heard about this and was having trouble enabling these drivers, this is how I did it,

Firstly upgrade your system:
```
sudo aptitude update
sudo aptitude upgrade
```

Then modify your /etc/X11/xorg.conf so that your Device, Module and DRI sections look like this:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. M11 NV [FireGL Mobility T2e]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option	"AGPMode" "4"
	Option	"AGPFastWrite" "yes"
	Option	"EnablePageFlip" "on"
	Option	"ColorTiling"	"on"
	Option	"RenderAccel" "yes"
	#Option	"UseFBDev" "true" DISABLED!
	Option "EnableDepthMoves" "true"
	Option "BackingStore" "true"
	Option	"DynamicClocks"	"on" # Dynamic clocking of chip for my iBook.
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"ati"
EndSection

```

Then restart X (easiest way to to reboot).

Then you should have direct rendering using only open source non-propriatary drivers. You can check this with glxinfo or glxgears.

However AFAIK these are experiemental drivers (hence why they're disabled by default), so I don't know how stable they are. I've only just do this to my system.

I've noticed some errors when running glxgears, I get:
```

$ glxgears -printfps
Unknown device ID 4E56, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_render.c function r300_get_num_verts line 188
user error: Need more than 2 vertices to draw primitive QS !
***************************************************************************
6584 frames in 5.0 seconds = 1316.764 FPS

```

I don't know what that means or how to fix it. And I still haven't gotten XGL working yet.

---

### Post by fuoco on 2006-11-03
Hi, I have the same machine as you do. But for some reason when I upgraded to edgy I got direct rendering enabled (glxinfo) but only around 25 fps in glxgears.
Do you know what is the problem?

---

### Post by fuoco on 2006-12-17
I used 'prevu' to install newer mesa packages with a more recent r300 driver. This has resulted in my glxgears raising from 25 to 900. But now planet penguin racer has only 2.5 fps. Any idea?

---

### Post by doobydave on 2007-03-01
*bump*

---

### Post by fuoco on 2007-03-01
More or less, this is considered fixed in feisty which now includes Mesa 6.5.2

---

