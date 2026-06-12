---
title: "Mouse cursor crashed on secondary monitor with dual monitor(xinerama)"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by yutiro on 2007-01-27
Hi.
I'm using ubuntu edgy, and I have installed it on my dell laptop (Compaq Presario V2000 series)
I'm using ati radeon mobile integrated graphic card, (ATI radeon xpress 200M).

After setting up my graphc card driver using fglrx, I tried to set up dual monitor with xinerama.
WIth a tons of kind help and posts, i could set it up by editing xorg.conf files, and it works perfectly!!! except my mouse cursor..

When i put my mouse cursor on the secondary monitor, the cursor crashed. Everything works fine except the mouse pointer..

Is there anybody experiencing the same problem??
Is there anybody who knows how to fix it??

Please help, I really wanna escape from Micro$oft as soon as possible.

Here, i attach my xorg.conf file.

---

### Post by BaddestCross on 2007-02-18
I'm getting ready to try dual monitors for the first time with my Averatec 7100 laptop.  It has the ai xpress 200m like yours.  Did you come across a solution to this mouse problem?

My goal is to be able to have a movie playing on one screen and a photo slide show running on the other.  Is this possible?


BC

---

### Post by yutiro on 2007-02-19
well... I actually i don't know that much about these dual monitor things.
So, I cannot give you answers about those movie or slide stuff.
But, I finally solved the cursor crash problem.
If you want to try dual monitor, follow these:

Basically, I have followed the HOWTO below.
 [http://www.ubuntuforums.org/showthread.php?t=321766](http://www.ubuntuforums.org/showthread.php?t=321766)

The following things are exactiy what i did.

1. Enable all repositories using synaptic package manager.

2. Back up xorg.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkp

3. Disable Composite
sudo vi /etc/X11/xorg.conf

and add
Section "Extensions"
Option "Composite" "Diable"
EndSection

4. Download ati driver from the ati web site: ati.com
(ati-driver-installer-8.33.6-x86.x86_64.run

5. At the folder where I downloaded the file do the followings:

sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debhelper debconf libstdc++5
linux-headers-$(uname -r)

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh

sudo dpkg -i xorg-driver-fglrx_8.32.5-1*.deb
sudo dpkg -i fglrx-kernel-source_8.32.5-1*.deb
sudo dpkg -i fglrx-control_8.32.5-1*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

sudo shutdown -r now

6. After rebooting, check whether it works or not.
sudo fglrxinfo

It must say that I am using ati driver instead of mesa.

---

### Post by BiGJoE1984 on 2007-03-03
> **yutiro said:**
> well... I actually i don't know that much about these dual monitor things.
So, I cannot give you answers about those movie or slide stuff.
**But, I finally solved the cursor crash problem.**


How did you solve that? I have the same problem on my Radeon9600..

I am actually already using Ati proprietary drivers.

---

### Post by kubusz on 2007-05-20
Hi,

did someone solve the mouse cursor problem? I am using two monitors (notebook and external wide screen  monitor) and when I move the mouse cursor on the second screen (wide screen monitro LG 194 WT) the mouse cursor changes into a wierd square. I do not know how to change into normal arrow.

I tried to modify my xorg.conf - disable composite - this acctualy workes in Edgy  Eft 6.10, but not in 7.04 Feisty Fawn.

Does someone have any ideas how to solve it?

Thanks Kubusz

---

### Post by yutiro on 2007-05-22
Hey,
The things I talked about before was only in Edgy 6.10 not in 7.04.
I have absolutely no idea about how to do in Fiesty, which is my current problems to solve..
Let me know if you find any solutions.
Thanks

---

### Post by neoraist on 2007-06-13
I've got the same problem,  there's a solution for it? actually i'm user the restricted drivers from ubuntu repos, but i've identic results with propietary drivers, and with it, i can't set up direct rendering...

thanks a lot

---

### Post by jorgepedret on 2007-06-17
Im having the same problem :(, playing with the xorg.xonf file I tried adding SWcursor to the main device:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	#Option	    "DesktopSetup" "horizontal,reverse"
	BusID       "PCI:1:5:0"
	Screen      0
	**Option     "SWCursor" "true"**
EndSection

I see the cursor showing correctly on both screens, but the cursor keeps lagging, it sticks everywhere and leaves a trail wherever you move it, so this options makes it worst than having the wired square.

Please if someone have an answer for this problem let us know!

---

### Post by servo153 on 2007-07-05
Hey guys, I am having a mouse issue with dual monitors, not quite sure if it's similar to what you guys are getting.  

I have a GX620 desktop with ati video card, and two 17" LCD monitors.  I'm a wiz at the xorg.conf file as I've had to redo it many times to get it working.  So, I have my two monitors working, desktops are spanned, I can drag windows between them, the whole 9 yards.  The only issue I have is when I use the mouse in my left screen, it can sometimes be inaccurate.  Like the click will be just up and to the right of where the cursor actually is.  Also, if i drag the mouse over the edge of any window, it jumps a bit and snaps back.  It's hard to make windows bigger or smaller cause I don't know exactly where the cursor is.

Also, if I'm doing something on the right screen and the mouse cursor changes to a wheel for example, when i drag the cursor over to the left screen the cursor remains the same icon until I drag it back to the right screen and then back to the left.  

This is a small issue, but can be annoying.  Any ideas?

---

### Post by RyCS42 on 2007-07-06
Just wanna say thanks yutiro. Your little guide helped me solve my multi-monitor cursor issue with Xinerama. Your steps are still applicable in Feisty; I think there's only one line that needs to be changed.

I'll go ahead and post exactly what I did for Feisty, even though it's largely just your steps over again.

```

1. Enable all repositories using synaptic package manager.

2. Back up xorg.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkp

3. Disable Composite
gksudo gedit /etc/X11/xorg.conf

and add
Section "Extensions"
Option "Composite" "Disable"
EndSection

4. Download ati driver from the ati web site: ati.com
(ati-driver-installer-8.33.6-x86.x86_64.run

5. At the folder where I downloaded the file do the followings:

sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debhelper debconf libstdc++5
linux-headers-$(uname -r)     // I forgot to run this line, but it made no difference in my experience.

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/feisty
sudo ln -sf dash /bin/sh

sudo dpkg -i xorg-driver-fglrx_8.38.6-1*.deb
sudo dpkg -i fglrx-kernel-source_8.3865-1*.deb
sudo dpkg -i fglrx-amdcccle_8.38.6-1*.deb   // This package was different from the one you listed. I just switch out to this package instead.

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

sudo shutdown -r now

6. After rebooting, check whether it works or not.
sudo fglrxinfo

It must say that I am using ati driver instead of mesa.
```

And there you have it. Although I guess this is technically ATI's Big-Desktop rather than Xinerama, I'm fine with it so long as it works! :]

---

### Post by Darth Arturito on 2007-10-06
Hi there, 
It seems like you having a lot of troubles with it :)

I got that solved by:

Installing:

ati-driver-installer-8.40.4-x86.x86_64

downloaded from ati website (i have ati radeon 9600)

and this is my xorg.conf :


------------------------------------------------------
[COLOR="DarkGreen"]Section "ServerLayout"
	Option "Xinerama" "true"
	Identifier     "Default Layout"
	Screen      0  "Main Screen"
	Screen      1  "Second Screen" LeftOf "Main Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
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
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "0 Main Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "1 Second Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "0 ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
	Screen	    0
EndSection

Section "Device"
	Identifier  "1 ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
	Screen	    1
	Option "SWCursor" "true"
EndSection

Section "Screen"
	Identifier "Main Screen"
	Device     "0 ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor    "0 Main Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Second Screen"
	Device     "1 ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor    "1 Second Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection[/COLOR]

-------------------------------------------------------------

---

### Post by JohnQ on 2007-10-10
> **servo153 said:**
> Hey guys, I am having a mouse issue with dual monitors, not quite sure if it's similar to what you guys are getting.  

I have a GX620 desktop with ati video card, and two 17" LCD monitors.  I'm a wiz at the xorg.conf file as I've had to redo it many times to get it working.  So, I have my two monitors working, desktops are spanned, I can drag windows between them, the whole 9 yards.  The only issue I have is when I use the mouse in my left screen, it can sometimes be inaccurate.  Like the click will be just up and to the right of where the cursor actually is.  Also, if i drag the mouse over the edge of any window, it jumps a bit and snaps back.  It's hard to make windows bigger or smaller cause I don't know exactly where the cursor is.

Also, if I'm doing something on the right screen and the mouse cursor changes to a wheel for example, when i drag the cursor over to the left screen the cursor remains the same icon until I drag it back to the right screen and then back to the left.  

This is a small issue, but can be annoying.  Any ideas?

I have exactly the same problem on my Gutsy Beta install.  The only difference is that my primary monitor is my left screen.  The cursor problems (the jumping a little higher click and never changing the cursor from spinning wheel, text insertion, grabbed hand) occur on my right screen.

I've been hoping that one of the daily updates would fix it, but not yet.

---

### Post by iKnowNotMuch on 2007-10-16
Hi guys I hope this helps.

I found this [http://blog.wolfman.com/articles/tag/ubuntu](http://blog.wolfman.com/articles/tag/ubuntu) which rather casually mentioned the solution that fixed it for me.  Running a fresh install of 7.04, and I used aticonfig to do the settings. 

All I had to do was add the following to the end of my xorg.conf

Section "Extensions"
Option "Composite" "False"
EndSection

and yipeee it worked!

if you've already go the extensions section, just add that composite line to it, don't create a new section if you don't need to.

---

