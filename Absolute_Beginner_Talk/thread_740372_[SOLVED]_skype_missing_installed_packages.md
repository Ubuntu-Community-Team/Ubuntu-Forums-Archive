---
title: "[SOLVED] skype missing installed packages"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-03-30
Going through the mess of installing skype on Gutsy 64 bit, I feel like I'm pretty close to the end. If I type skype into the terminal, at this point, though, I get this:

```
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

```

I saw on <A href="https://help.ubuntu.com/community/Skype#head-6c3cbecd1f1ecd4388bde1462ee364bb57e4533b">This page</A> that I should see what shared packages are missing. Here's what happened"

```
$ ldd /usr/bin/skype | grep not
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
        libXss.so.1 => not found
        libQtDBus.so.4 => not found
        libQtGui.so.4 => not found
        libQtNetwork.so.4 => not found
        libQtCore.so.4 => not found

```

Now for the weird thing: I go into synaptic to install these packages, and I find that they are all already installed. What gives? Could it have to do with these packages being 64-bit, so the 32-bit skype doesn't notice them? I'm kind of a n00b when it comes to this kind of thing, so I'm not sure what to do next.

---

### Post by pseudo-random on 2008-03-30
Thats a snag with your ATI graphics card driver. Try the ATI driver instead.
Could you post your /etc/X11/xorg.conf

---

### Post by dinostabOMG on 2008-03-30
Hm. It seems I am using the ATI driver. In Restricted Drivers Manager, I see ATI Accelerated Graphics Driver, which is checked and in use.

xorg.conf:

```


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI RADEON x1900 XT"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-94
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON x1900 XT"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by pseudo-random on 2008-03-30
Common error this one but the solution escapes me.
[http://ubuntuforums.org/showthread.php?t=21543](http://ubuntuforums.org/showthread.php?t=21543)
Have you run 
```
fglrxinfo
```
to get some info about your card

---

### Post by dinostabOMG on 2008-03-30
Here's what fglrxinfo gives at the moment: ```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

But can you clarify why we are worrying about my graphics card settings? I struggled to get those sorted out, especially vis-a-vis compiz fusion, but it all seems to be working properly right now. Why should a problem with skype be related? Even if the problem is with the graphics card, how come there are supposed missing dependencies, even though those are already installed?

---

### Post by StOoZ on 2008-03-30
seems like you are missing the QT libaries, install latest QT from here:
[http://trolltech.com/products/qt]("http://trolltech.com/products/qt")

---

### Post by pseudo-random on 2008-03-30
Possible solution:
[http://divyad.wordpress.com/2007/11/11/install-skype-20-beta-on-ubuntu-gutsy710-amd64/](http://divyad.wordpress.com/2007/11/11/install-skype-20-beta-on-ubuntu-gutsy710-amd64/)

---

### Post by dinostabOMG on 2008-03-30
> **StOoZ said:**
> seems like you are missing the QT libaries, install latest QT from here:
[http://trolltech.com/products/qt]("http://trolltech.com/products/qt")

In synaptic, it is indicating that I have the following packages installed:

libqt3-mt
libqt4-core
libqt4-gui

Are these not enough/not the correct ones? Is there a reason I need to download them from the site rather than use synaptic?

---

### Post by xc3RnbFO8P on 2008-03-30
Skype 64 bit:
[http://ubuntuforums.org/showthread.php?t=432295]("http://ubuntuforums.org/showthread.php?t=432295")

---

### Post by dinostabOMG on 2008-03-30
> **pseudo-random said:**
> Possible solution:
[http://divyad.wordpress.com/2007/11/11/install-skype-20-beta-on-ubuntu-gutsy710-amd64/](http://divyad.wordpress.com/2007/11/11/install-skype-20-beta-on-ubuntu-gutsy710-amd64/)

WORKS! It was getlibs that seems to have done the trick. The site suggests installing from source, although I didn't have to do that. Man, this forum is awesome, and thanks, pseudo-random. I got the working solution 35 minutes after posting a question. Nice.

And thanks, Ringi, but I tried the basic install stuff but was having problems. But maybe getlibs should be added to to the HOWTO for skype for 64 bit users.

---

