---
title: "Ive lost Glx support and cannot get it back"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-03-02
[B]i reinsatalled ubuntu recently and hit a big number of problems which didnt deem to be there before.

These included sound recording on my ac97, a number of graphics problems, a new sound card (oss) whatever that means. 

Thats not so important, What is critical is, i cannot get blender to work (which is my most important peice of software) I have looked in Xorg.conf and the line load glx is there.

Blender however has different ideas and reports this:
[/B]"Xlib: extension "GLX" missing on display ":0.0"

[B]Ive checked the blender website what this error means and it says this:
[/B]
If you are getting this error it means that the glx extension is not enabled in /etc/X11/XF86Config.
GLX allows blender to access your 3d card and draw to the screen, but some distributions ship with GLX disabled.
It likely means that you just haven't got OpenGL installed or properly configured on your system. (It is also a symptom that you should review your 3D card setup in general).

[B]For a start i havent got this file /etc/X11/XF86Config. but im assuming its refering to xorg.conf (am i right?)
Also why in my xorg.cong does it say its on PCI:1:0:0 as its an agp card ?!?

Here is my xorg.conf anyway (ive removed the bits on fonts keyboard etc):

[/B]```
Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Fujitsu Seimens 900P"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"Fujitsu Seimens 900P"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Pragmatist on 2006-03-02
Did you install a Nvidia driver seperately??

---

### Post by LordBug on 2006-03-02
If you haven't already, open a shell and do 'sudo apt-get install nvidia-glx'.  This will install nVidia's drivers.  Then, open up /etc/X11/xorg.conf and (taken directly from the nvidia Linux driver page):
> 
Remove the line:

      Driver "nv"
  (or Driver "vesa")
  (or Driver "fbdev")

and replace it with the line:

    Driver "nvidia"

Remove the following lines:

    Load "dri"
    Load "GLCore"

In the Module section of the file, add the line (if it does not already exist):

    Load "glx"

This should take care of the glx issue.

---

### Post by dgrafix on 2006-03-02
Yoooz da man!

Thanks a lot, that kicked it just fine!

Hehe, Now for the sound and printers :-k

---

