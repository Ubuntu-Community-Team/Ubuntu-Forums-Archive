---
title: "Help: Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:1.0&quot;"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-13
Anyone no how to solve this problem?
I have gone through countless hits on google and the ubuntu forums - I found many maybe's a few (not so clear) solutions, none for me though - I'm just getting more and more confused now.
Situation
graphics: ati x1600, screen: 1680x1050, computer:core2duo laptop.

I have setup beryl + xgl following various tutorials
I now have the opportunity to either start a gnome session or an xgl session

When I login to an xgl session Beryl will run but xorg very frequently hits 100% whether beryl runs or not. When Beryl is not running the screen is not repainted as it should be. For instance the left pane of nautilus will often be blank and folders are only repainted as the mouse pointer is moved over them.

When I try the glxgears the wheels run smoothly in a gnome session but rather sluggish in an xgl session.

Btw: people mention that frame rates should be printed out from the glxgears command - I havn't seen anything - how is it used?

When i login to a gnome session fglrxinfo gives me this:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```Looks ok to me - right?
When I login to an xgl session fglrx gives me this:
```
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```
Looks like something's wrong with **"XFree86-DRI" missing**?
My xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc101"
	Option	    "XkbLayout" "dk"
	Option	    "XkbVariant" "nodeadkeys"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
#	Driver      "vesa"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "0"
EndSection


```
One interesting thing:
I changed **"Composite" "Disable"** to **"Composite" "0"**
Then the error changed from **Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0"**. To the one above (the **localhost** part disappeared).

I've create an 'xgl.desktop' file:
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl
Icon=
Type=Application

```
and a script '/usr/bin/startxgl':
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

```
I tried the following:
1) Change to DISPLAY=:0
As there are no references to a display 1 in the xorg.conf..
result: an xgl session (a window with gray background and nothing else)  starts in what appears to be a normal program widow inside the gui. 
Solve: revert to DISPLAY:1
2) created a new screen entriy changed from '0' to '1' like this ** aticonfig-Screen[1]** as I thought that it needed configurations for a display 1.
Result: could not boot into the gui. 
Solve: boot into recovery, edit with nano /etc/X11/xorg.conf delete the offending entries.

What can be done about this?

---

### Post by pay on 2007-01-13
That is all normal side effects from using XGl. You can not use 3d acceleration when using an XGL session.

---

### Post by fsando on 2007-01-13
Thanks a lot. Nothing wrong then?
Could you perhaps point me to some good sources of information on xgl and xserver?

---

### Post by pay on 2007-01-13
What kind of information do you want? Howto setup xgl? Drivers and xorg?

---

### Post by fsando on 2007-01-13
> **pay said:**
> What kind of information do you want? Howto setup xgl? Drivers and xorg?That too but I've seen quite a few by now :D 
But I was thinking more in the line of some in-depth information. For example I didn't know that "XFree86-DRI" error was anything to do with 3D or how exactly this influences my system. I'v seen a lot about 'direct rendering' and 'not supported by ati driver' etc. but don't know what it is about.
So in one sense I'm a complete noob regarding graphics - but on the other hand I am quite capable of understanding complicated tech stuff.
I would like to know what xgl, the gnome desktop, and the x-server are and how they connect. I would like to be able to understand the strange commands in the "startxgl" file and the entries in the xorg.conf.

---

### Post by pay on 2007-01-13
Well the Gnome desktop is basically the user interface between you and the kernel. The X-server is the graphics system and XGL is a hack on the the X-server to allow 3D effects. Xorg also has it's own implementation of xgl built in called AIGLX, but you won't be able to use that since your video card isn't supported by the radeon driver. For more in depth information you will have to read books about Linux, like this one [http://www.kroah.com/lkn/](http://www.kroah.com/lkn/)

---

### Post by KaeseEs on 2007-01-13
I had the same issues and fglrxinfo error with a radeon MobilityFire x1400 on my Thinkpad T60.  Try the following:

```
 sudo depmod -a
```

Then restart your x-server.  It worked for me.  If it doesn't work for you, it means that XGL is forcing the 'Desktop Compositing' extension on in fglrx, and there's no hope while using XGL.

---

### Post by fsando on 2007-01-14
pay: Thanks a lot - funny thing is that I bought an earlier version of that same book - never read it then but will definitely do it now. :)
KaeseEs: no it won't help me, my card does not (or the driver does not) support it. Just have to live with it until it is supported - if it ever happens :(

---

### Post by Villenya on 2007-02-04
i am having the same problem, is there no way to run xgl/beryl on x1400 then?

---

### Post by fsando on 2007-02-04
> **Villenya said:**
> i am having the same problem, is there no way to run xgl/beryl on x1400 then?
That's not what it means - to be honest I'm not entirely sure what exactly it means, I believe that ati cards are taking some level of performance hit. 
I'm pretty sure you can run beryl, there are probably lots of people running beryl on that card.
I'm running beryl/xgl with x1600 and I'm very satisfied. But things run a little slower when I start Beryl and are less stable, it's not a big deal though - coming from window :)

I have beryl version 0.2.0+svn20070201-r3555, I find it very robust now and it's very close to release - mine is release candidate 1.

A good guide to install is here:

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
I would recommend the svn repositories (as it is so close to release)

The ati fglrx driver should be in synaptics 
(System > Administration > Synaptics) 
from here it should be pretty easy to install. You may have to enable restricted repositories
 (System > Administration > Software Sources)
Also beware there are several different versions of startgl.sh floating around in the howtos and they give very different results.

EDIT:
Just remembered how the problem probably was solved. I believe it was an upgrade to a newer version of beryl that did something good.
I would recommend enabling/adding all relevant repositories and do all your updating/installing through synaptics - it seems to be doing a pretty good job.

If you need the newest driver from ati here is how I installed it (and uninstalled it again - it didn't work for me). And be warned - they do not recommend it:
[http://ubuntuforums.org/showthread.php?p=2080144#post2080144](http://ubuntuforums.org/showthread.php?p=2080144#post2080144)

---

### Post by shareMenaPeace on 2007-02-04
One thread to rule them all v2: Beryl & Official Compiz
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

From there

A short introduction to beryl: [http://wiki.beryl-project.org/index.php/FAQ/Beryl](http://wiki.beryl-project.org/index.php/FAQ/Beryl)

And what are XGL and AIGLX? [http://www.freesoftwaremagazine.com/node/1797](http://www.freesoftwaremagazine.com/node/1797)

Well im still a little confused what is this xgl and aiglx it seems my gfx card can handle both.

---

### Post by Villenya on 2007-02-04
thanks! updating to svn version of beryl fixed the problem, everything works fine now :D

---

### Post by the_rover on 2007-02-07
Hi,

I'm the owner of a Dell Inspiron 6400 dual core with ATI x1400 with an Ubuntu Edgy and I have to say that XGL/Beryl runs on that graphics card.

I've tested from beryl 0.1.3 to the last on ubuntu repositories beryl 0.2 with the last Ati drivers (8.33-6 I think) and all worked correctly.

It was so easy following some tutorials found on the web but... now it doesn't work!!!

I have the same problem posted here.

By the way I can say that I have updated some packages so I was trying to play around with kiba-dock but I am not sure which. It's possible this is the problem.

I'm sick of reinstalling and reconfiguring Ati drivers and xorg and nothing really happens. My gnome session still has 3d acceleration but xgl doesn't.

I was focused in xorg.conf file cause the display 1 issue just how you did but now I start to think the problem is in some of the modules or compatibility. 

One thing I've tested was changing the xgl inicialization:

Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & DISPLAY=:1

to:
Xgl :0 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & DISPLAY=:0

Te result was an xgl session with 3d acceleration but beryl didn't work... mmmm strange.

Sorry, I can't help with any more. I'll keep, reading, trying and posting results.

Any help is wellcome (including corrections in my english write :D)

(Edited to correct some mistakes and smilies messing around)
Regards.

---

### Post by Adler on 2007-02-12
Hi All,

I run Linux, and Beryl like a rabbit. My present Debian based distro is Linux Mint. Basically, Ubuntu with all the codecs that you want, plus a few other things.

Has any one got Google Earth going with Beryl?

Adler

---

### Post by the_rover on 2007-02-14
After many tests I realized that Xgl doesn't work the same than Xorg. Many 3D applications won't run in xgl like Xorg (DRI), for example glxgears doesn't. This was what confussed me...

Drivers were installed correctly and reinstalling Beryl (v2.0 from Treviño repository) it started to work fine again.

My configuration, if this helps somebody:

- Dell Inspiron 6400 dual core 2400. Ati X1400.
- Ubuntu Edgy 6.10.
- Xorg 7.1
- Ati propietary drivers 8.33-6
- I can't remember now Xgl version but it is the last from ubuntu edgy repositories.
- Beryl 2.0

Regards.

---

### Post by teolemon on 2007-02-16
I did the steps mentionned above on an Acer Aspire 1640z , even trying to use the svn. But Beryl doesn't seem to work (falls back on Metacity) and fglrxinfo sends this back:
```
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
```
Any idea where the whole thing is blocking ?

lspci sends back this:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)

```
and this
```
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 714a

```

---

### Post by teolemon on 2007-02-17
Fixed by entering 
```
gksudo "gedit /etc/modules"

```
Into a terminal and adding fglrx to the file.

---

### Post by f1dude on 2008-02-08
Try:

export DISPLAY=:0.0

it enabled direct rendering after I did that. =D

---

### Post by Tamjay on 2008-02-26
> export DISPLAY=:0.0

Thanks F1Dude.  This worked well for me trying to finally get Direct Rendering!  Lot's of games wouldn't run before I was able to do this, but two quick questions if anyone can help.

This may sound strange, but why is it i have to cut and paste this for it to work and it dosen't work when I just type it in?  (emberassing huh?)


And one other thing.  Where can I put this command where it just activates when i log in my  session so it will just be there when i log in?


Thanks.

---

### Post by knowledge_is_power on 2008-03-19
theres no spaces around the =

---

