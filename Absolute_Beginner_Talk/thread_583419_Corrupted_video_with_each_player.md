---
title: "Corrupted video with each player"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Ev1L on 2007-10-20
Hi,
I am using Gutsy on Asus G1 with Nvidia Go 7700.
The first video I watch with any player (mostly Totem-xine) are fine, but after closing it (maybe there is another reason but I couldn't reproduce the mulfunctioning, looks random), when I try to restart any video, even the previous one, I can only hear the voice and I see horizontal coloured (pink or green) stripes with a barely recognizable message written (I guess it is written something with a 404 at some point :) ).
This happens with every player, also VLC.

I tried to reinstall Totem, Nvidia drivers (glx-new) and other stuff I can't even remember, but the problem is still there.

Any idea?

Thank you,
EviL

---

### Post by adamorjames on 2007-10-20
You have visual effects on? You tried the different video drivers for mplayer? Probably none of that will help though. It sounds like a bad error. Bump.

---

### Post by Ev1L on 2007-10-20
i tried to disable effects and rebooted but still happened.
I didn't try to change drivers in mplayer, but when the error happened I tried that, totem and vlc,
Next time I will try to do it, but it doesn't seem a big solution, because what if I need to use VLC?

---

### Post by Ev1L on 2007-10-20
i just found out that part of the background sentence seems to be Leave fullscreen :)
First unuseful(?) clue

---

### Post by Ev1L on 2007-10-20
ok, with xv X11/Xv (the default) gives that problem, but mplayer is able to show correctly with gl2 X11 (OpenGL) - multiple textures version.

now, can anyone tell me how to set it as system default?
I can also paste a xorg.conf part to help:

> 
Section "Device"
	Identifier	"nVidia Corporation GeForce Go 7700"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce Go 7700"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection


---

### Post by adamorjames on 2007-10-20
You seem to like VLC. Try using openGL in VLC, go to "Settings">"Prefrences" and "Output modules", make sure the "Advanced options" checkbox is ticked. :) Each player should have an option of which driver to use. I know Xine, MPlayer and VLC do.

---

### Post by NilsE on 2007-10-20
You can try a couple of the options in

gstreamer-properties

---

### Post by avox on 2007-10-21
> **Ev1L said:**
> ok, with xv X11/Xv (the default) gives that problem, but mplayer is able to show correctly with gl2 X11 (OpenGL) - multiple textures version.

now, can anyone tell me how to set it as system default?
I can also paste a xorg.conf part to help:

My ***mplayer*** also just went through the same problem and changing the video output fixed it as I surmised (but what caused it in the first place?!  grrrr...).  That being said, what "it" are you referring to as a system default:  The default player for video files?  Which video driver ***mplayer*** uses?

---

### Post by Ev1L on 2007-10-21
My "it" is:
every player comes with X11/Xv as default, thus i suppose it is the "system default driver", so instead of changing it manually on each player, i just would like to do it once (just guessing: could i change something on xorg.conf so gl2 becomes default instead of Xv?)

---

### Post by adamorjames on 2007-10-21
> **Ev1L said:**
> My "it" is:
every player comes with X11/Xv as default, thus i suppose it is the "system default driver", so instead of changing it manually on each player, i just would like to do it once (just guessing: could i change something on xorg.conf so gl2 becomes default instead of Xv?)

I don't think it is possible... :(

---

### Post by avox on 2007-10-21
> **adamorjames said:**
> I don't think it is possible... :(

Considering that mplayer's default config is kept in /etc, i'd have to concur.  Each player probably stores their default settings separately, but maybe there's a switch somewhere for xine/gsteamer/etc settings...?  I didn't see anything tho, sorry.  :(

---

### Post by Ev1L on 2007-10-21
maybe gstreamer-properties as suggested before.but seems that i have a limited choice respect of mplayer, i tried to avoid Xv, i hadn't the chance to try if it solved anything

---

