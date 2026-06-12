---
title: "Powerpc NVidia/OpenGL problem"
date: 2009-04-30
forum: Apple Hardware Users
---

### Post by BigDaveyL on 2009-04-30
Hi all,

It looks like the colors are off for OpenGL programs.  Here is a picture of what I mean:
[IMG]http://www.frontiernet.net/~dliana/glxgears.png[/IMG]

I'm running a Powerbook G4 12" 1.0 GHz with an NVidia GeForce FX 5200.

I initally didn't have an xorg.conf (and I still had the issue).  I made one with some settings, and here it is:

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen		0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "record"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
	BoardName	"NV34M [GeForce FX Go5200]"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Any ideas?

---

### Post by stream303 on 2009-05-01
I have that same issue on my G5 iMac running the same video card.  Plus I'm seeing it with the nouveua video driver as well.

---

### Post by pxwpxw on 2009-05-01
Color wheel.

---

### Post by BigDaveyL on 2009-05-01
> **pxwpxw said:**
> Color wheel.

And ...?

---

### Post by pxwpxw on 2009-05-01
> **BigDaveyL said:**
> And ...?

Well, I get the same glxgears bad colors with nuoveau on G5, but it seems to reproduce the color wheel fairly well, so maybe it is a glxgears thing.

---

### Post by cyberdork33 on 2009-05-01
> **pxwpxw said:**
> Well, I get the same glxgears bad colors with nuoveau on G5, but it seems to reproduce the color wheel fairly well, so maybe it is a glxgears thing.
how do you do the colorwheel?

---

### Post by pxwpxw on 2009-05-02
> **cyberdork33 said:**
> how do you do the colorwheel?

It is a *.gif file I found searching for a color wheel. 

The idea was to compare a screenshot of a picture displaying a color wheel, with the 'original' somewhow.... or with other computers. But problem is where is the reference display going to be and who does the comparing, as I just discovered.

 "http://northlite.net/ps/images/color_wheel.gif"

Also as the OP says 'It looks like the colors are off for OpenGL programs'
so the gif is not much help there.

---

### Post by joshdudeha on 2009-05-02
Lol, that colour wheel, is an image not an openGL program like glxgears.
So of course it'll show up fine.

---

### Post by cyberdork33 on 2009-05-02
> **pxwpxw said:**
> It is a *.gif file I found searching for a color wheel. 

The idea was to compare a screenshot of a picture displaying a color wheel, with the 'original' somewhow.... or with other computers. But problem is where is the reference display going to be and who does the comparing, as I just discovered.

 "http://northlite.net/ps/images/color_wheel.gif"

Also as the OP says 'It looks like the colors are off for OpenGL programs'
so the gif is not much help there.

> **joshdudeha said:**
> Lol, that colour wheel, is an image not an openGL program like glxgears.
So of course it'll show up fine.
got it now.

Now if you put that color wheel on a OpenGL object and displayed it, then it might be helpful.

---

### Post by brian_252 on 2009-07-13
See [http://bugs.freedesktop.org/show_bug.cgi?id=22017](http://bugs.freedesktop.org/show_bug.cgi?id=22017)

Looks like this is the official bug report.

---

