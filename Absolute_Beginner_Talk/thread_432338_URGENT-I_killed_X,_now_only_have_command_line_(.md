---
title: "URGENT-I killed X, now only have command line :("
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-03
I installed nvidia-glx-new and ran 

sudo nvidia-glx-new enable

Now I only have a command line.  I have tried

sudo nvidia-glx-new disable

to no avail.  It has apparently made like 3 backup files now, none of which I can see the name of (don't know how) and can't restore (don't know how)

Please help, I am going mad here :(

---

### Post by bobplano on 2007-05-03
if you just killed X use ```
startx
```
or ```
sudo X
``` for the second command it has to be a uppercase X

---

### Post by gohanssjn on 2007-05-03
Sorry, by killed, I mean when I restart, it says it can't be started :(

(ww) NV: no maching Device section for instance (BUSID PCI:1:0:0) found
(ee) No Devices detected.

Fatal Error
no screen found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining

---

### Post by bobplano on 2007-05-03
have you tried```
sudo dpkg-reconfigure xserver-xorg
```
that is usually a cureall because you can choose the drivers and resolution you want

---

### Post by gohanssjn on 2007-05-03
Trying now.

nope, still no go :(

Off to spiderman, cya all in the morning.  wis I could just do an auto fix from the liveCD or reinstall X or my drivers or something

---

### Post by Seisen on 2007-05-03
If you ever run into problems again like this its better to do this in the terminal.

```
sudo dpkg -reconfigure -phigh xserver-xorg
``` this way it doesn't ask you as many questions.

---

### Post by medya on 2007-05-03
hey you should replace a working xorg.conf 
in the command prompt do this
> cd /etc/X11/


then
> dir xorg*.*

now you should see something like xorg.conf.backup
do this
sudo mv cp xorg.conf.backup   xorg.conf
for detalied explaition[ go to here]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")


(if there was no backup file tell me I will tell u another thing)

---

### Post by gohanssjn on 2007-05-04
> **medya said:**
> hey you should replace a working xorg.conf 
in the command prompt do this


then

now you should see something like xorg.conf.backup
do this
sudo mv cp xorg.conf.backup   xorg.conf
for detalied explaition[ go to here]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")


(if there was no backup file tell me I will tell u another thing)

When I type what is above with my file name replaced, I get xorg.conf is not a directory.

---

### Post by gohanssjn on 2007-05-04
Oh god.  I removed the 'cp' like the link said, and now my backup is gone too.  :(

---

### Post by use a name on 2007-05-04
> **gohanssjn said:**
> Sorry, by killed, I mean when I restart, it says it can't be started :(

(ww) NV: no maching Device section for instance (BUSID PCI:1:0:0) found
(ee) No Devices detected.

Fatal Error
no screen found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining

Looks like the nv driver is still used. You can:

```

sudo vi /etc/X11/xorg.conv

```
If you figure out [how vi works](http://www.google.com/search?source=ig&hl=en&q=vi+howto&btnG=Google+Search).

You might find two "Device" sections, both with a line
```

Identifier ...

```
with on the ... something to identify your setup. Under section "Screen" you will find a line
```

Device ...

```
Now make sure that on those ... you put the Identifier from the "Device" section that uses Driver "nvidia" instead of "nv".

Hope that helps.

---

### Post by gohanssjn on 2007-05-04
> **Seisen said:**
> If you ever run into problems again like this its better to do this in the terminal.

```
sudo dpkg -reconfigure -phigh xserver-xorg
``` this way it doesn't ask you as many questions.

I get "conflicting actions" when I choose this.

Maybe my bad drivers are also still installed?

Help :(

---

### Post by gohanssjn on 2007-05-04
In the xorg.conf I picked Nvidia, still nothing :(

---

### Post by gohanssjn on 2007-05-04
Ok, I have the LiveCD up, can I just fix it by reinstalling something from here???

---

### Post by gohanssjn on 2007-05-04
Ok, here's an idea.

Can I copy my Livecd's etc/X11/xorg.conf to my install on my HD somehow?

---

### Post by use a name on 2007-05-04
Technically, you could, but that one will be using the old driver again, or maybe even a vesa driver.

Can you put the contents of your xorg.xonf here? From the liveCD you can mount the drive you've installed linux to in order to post the contents.

---

### Post by gohanssjn on 2007-05-04
Ugh.  I told X to uninstall and reinstall, still "No screens found"

Replaced the xorg.conf, nothing.

Now when I try to run the xorg.conf o change it, Nvidia isn't even an option anymore.  So lost :(

---

### Post by use a name on 2007-05-04
Yep, if you reinstall, it wipes the xorg.conf...

Have you tried [envy](http://www.albertomilone.com/nvidia_scripts1.html)? If not, try it. You can get it with apt-get. It may be that you still have to manually make the new nvidia entry the default one.

---

### Post by lakersforce on 2007-05-04
replace one of the backup files with the primary.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

of course you will have to find the appropiate backup file. The numbers actually make sense.

---

### Post by Churnd on 2007-05-04
It seems to me you are installing the wrong driver.  What kind of video card do you have?  You might need to use the nvidia legacy driver by :

```
sudo apt-get install nvidia-glx-legacy
```

Then your currently configured xorg.conf should work.

---

### Post by gohanssjn on 2007-05-04
I have the correct drivers now I believe.  I have a Nvidia 7400go.

Also, the Ubuntu screen at the begining shows up fine, in 24bit color, just goes to command prompt only after that.

---

### Post by Terl on 2007-05-04
Can you post your xorg.conf?  That will help a lot.

---

### Post by gohanssjn on 2007-05-04
xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"NVIDIA 7400GO"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA 7400GO"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Churnd on 2007-05-04
> **gohanssjn said:**
> I have the correct drivers now I believe.  I have a Nvidia 7400go.

Also, the Ubuntu screen at the begining shows up fine, in 24bit color, just goes to command prompt only after that.

You mean the Splash screen with the status bar?  That doesn't rely on the nvidia driver.  It will run regardless of which driver you have installed.  How do you know you have the correct drivers?  A few "not so old" cards can't use the newest driver that nvidia-glx installs.  My laptop has a Geforce4 440 Go, and I had to use the legacy driver.

---

### Post by gohanssjn on 2007-05-04
Tried Envy, still no go.

Envy got a bunch of errors and says at the end:

sudo: /etc/init.d/kdm: command not found

Also, using the nvidia driver worked until I tried nvidia-glx-new.  Nvidia-glx used to work except hibernate, that's why I tried the new ones and X died >.>

---

### Post by gohanssjn on 2007-05-04
Well, I am about 20min of work away from just reinstalling this thing.  I am getting ****** off.

---

### Post by gohanssjn on 2007-05-04
Ok, the only thing I've done before this is install multimedia stuff and confiure GRUB, it's getting reinstalled.  Thanks for the help all, but I just an not at a high enough level to fix this.

---

### Post by Churnd on 2007-05-04
> **gohanssjn said:**
> Tried Envy, still no go.

Envy got a bunch of errors and says at the end:

sudo: /etc/init.d/kdm: command not found

Also, using the nvidia driver worked until I tried nvidia-glx-new.  Nvidia-glx used to work except hibernate, that's why I tried the new ones and X died >.>

Hibernate doesn't so much rely on the video driver as it does ACPI.

Did you:

```
sudo apt-get remove nvidia-glx*
```

then

```
sudo apt-get install nvidia-glx
```

You're probably still trying to use the nvidia-glx-new driver, which likely isn't compatible with your card.

---

### Post by gohanssjn on 2007-05-04
Well, I've reinstalled now, but yes, I had run both of those commands.  Thanks all, it only took 15min to trinstall and update back to where I was, so a fix wasn't worth it anymore.

---

### Post by ryodoan on 2007-05-06
That is what I love about ubuntu, when I goof up really bad a reinstall and re-update of ubuntu is so easy.

---

