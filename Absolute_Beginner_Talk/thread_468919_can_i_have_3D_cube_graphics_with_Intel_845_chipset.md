---
title: "can i have 3D cube graphics with Intel 845 chipset?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by sreenivas1234 on 2007-06-09
Am Really NEW to linux, some how with help of people in this forum  i installed Ubuntu 7.04 on my michine successfully,but the 3 D desktop is not working, when i click to activate it will come BLANK white screen, thats it, after clicking or press Esc normal Ubuntu destop appears again.

system configuration: HP d220 ( branded PC)

Intel X86 pentium 4 processor

1.8MHz CPU

integrated intel xtream graphic card ( 64MB) [No extra graphic card]

40GB hard drive

Intel 82845 Mother board  ( 845 family)

768MB DDR RAM in two slots 512+256

monitor: Samsung samptron 45Bn

internet :
cable connection Motorola SB5100


AM ATTACHING THE SCREEN SHOTS OF MY  COMPUTER INFORMTION, IN JPEG FORMAT, PLESE SOME BODY HELP ME, ( all in XP)
1.Graphic card information
2. System information
3. Hard ware information 

I DESPIRATLY WANTED THE GRAPHICS IN MY SYSTEM
EAGERLY WAITING FOR THE REPLY 
TAHNKING YOU

---

### Post by insane_alien on 2007-06-09
it should theoretically be possible but it wouldn't run very well. as in it would be jerky and possibly unstable. its still very much beta software and probably shouldn't be used by new people who want everythng to 'just work'

---

### Post by sreenivas1234 on 2007-06-09
Good news that it is possible, any body help me with this,
i really fed up with VISTA which doest support  for my PC for their, AERO, i have to change my PC.

i watched the videos ubuntu in Youtube simply amazing, please help me.

---

### Post by Zzl1xndd on 2007-06-09
It should work without any issues, Im running compiz on a machine with a 16meg card. now the first question ill ask is have you already installed Ubuntu?

---

### Post by sreenivas1234 on 2007-06-09
Yes to day i installed Ubuntu on different Hard drive Not in Xp hard drive, the configuration of the system is all ready i mentioned in SCEEN SHots.

---

### Post by CheeseEatingBulldog on 2007-06-09
For Desktop effects to work, you need to add a few lines to the 

/etc/X11/xorg.conf

Such as 	Option		"XAANoOffscreenPixmaps"	"true" to your device section (video card) 

and  

Section "Extensions"
	Option "composite" "true"
Endsection 

To the end of the file.

That is of course assuming that you have DRI working (open a terminal and type 'glxgears' or for more info 'glxinfo' to check). If not you will need to sort a driver out.

---

### Post by sreenivas1234 on 2007-06-09
where to enter these lines? in terminal?

"/etc/X11/xorg.conf"

where is options? am sorry am really new to linux. please bear with me. Thanking you

---

### Post by CheeseEatingBulldog on 2007-06-09
Sorry, will clarify a bit.

Before you edit anything make a backup of your current xorg.conf!

Your video settings are in the file /etc/X11/xorg.conf, which can be opened with the text editor of your choice (gedit, nano, vi) from the terminal by typing:

sudo gedit /etc/X11/xorg.config

This will open the file in write status (as root). Once open you will see your settings, one which is the 'device' that defines your video card and the 'modules' section that defines which kernel modules are loaded, you need to add some so that it looks a bit like this:

Section "Module"
Load "i2c"
Load "bitmap"
Load "dbe"
Load "dri"
Load "ddc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection

For the device section, take mine as an example (I have a geforce2 card):

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
Option "RenderAccel" "true"
Option "AddARGBGLXVisuals" "True"
# Option "UseFBDev" "true"
Option "AllowGLXWithComposite" "true"
Option "backingstore" "true"
Option "TripleBuffer" "true"
# VideoRam 65536
Option "XAANoOffscreenPixmaps" "true"
Screen 0
EndSection

Compare with your section, and add 

Option "RenderAccel" "true"
Option "AddARGBGLXVisuals" "True"
Option "XAANoOffscreenPixmaps" "true"

To your section (ignore the others in my file as I have a tvout setup as well and some options are card specific).

Now at the end of the file, if it is not already present add:

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "true"
EndSection

Now save and close all apps and push ctrl+alt+backspace, which will reload the X server. If it does not come back either restore your xorg.conf or type 

dpkg-reconfigure xserver-xorg

at the prompt to setup your xorg from scratch (wizard).

Search the forums here for your card, or similar cards and check their xorgs.

Hope it helps.

---

### Post by sreenivas1234 on 2007-06-09
after performing these steps

 Disable Composite Extension

In Ubuntu Feisty the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to disable Composite you have to edit the xorg.conf file:

gksu gedit /etc/X11/xorg.conf

and add these lines at the end of the file:
File: /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection


SOURCE:[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

after restart , then when ever i click system>>preferences>>Desktop effects  i will get error mesage am uploading the Screen shot.
previously a popup window opnes and asks for enable desktp effects after i click on enabled white blank screen will appear. Now am not able to see even the pop up it sefl.

some body please help me

---

### Post by jiminycricket on 2007-06-10
I believe with some old graphics cards you have to specify the amount of video ram.  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4) > 

You can create /etc/drirc file with the following contents:
<option name="allow_large_textures" value="2" />

However, it's most probable your graphics card does not enough video RAM to handle the multiple large textures anyway.

Also make sure you cange the BIOS shared Video Memory from 1MB to 8MB.

---

### Post by sreenivas1234 on 2007-06-10
i checked in BIos the video adaptor is 8MB ( that is max) is by default it is.

i installed easy ubuntu and updated with ATI drivers i think this is causing the problem
how can i uninstall the ATi drivers from Easy ubuntu, now its grayed out.

---

### Post by sreenivas1234 on 2007-06-10
when i enter this code:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) # (Okay if it is already installed)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a


_i willget this_

sreeni@sreeni-desktop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN       
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources
Fetched 3B in 3s (1B/s)  
Reading package lists... Done
sreeni@sreeni-desktop:~$ sudo apt-get install linux-restricted-modules-$(uname -r) # (Okay if it is already installed)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sreeni@sreeni-desktop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sreeni@sreeni-desktop:~$ sudo depmod -a

when i enter code:

sudo gedit /etc/X11/xorg.config

a blank xorg.config opens up. what does it mean?

---

### Post by sreenivas1234 on 2007-06-10
finallly i formated PC and installed again ubuntu

when i enter code in terminal

gksu gedit /etc/X11/xorg.conf

hear the xorg.conf file

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
	Load	"i2c"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection


but my graphic card is intel 845 integrated (GPU)
can any body help me in installing correct video drivers for my chip set??
i found the intel website downloaded the linux drivers for my mother board but i dont know how to install them the drivers are i915 mentioned in it. 
some body please help me to activate 3D desktop.

---

### Post by CheeseEatingBulldog on 2007-06-11
Like I said in my previous post you need to add some stuff to your video card settings:

Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection

From this thread: [http://ubuntuforums.org/showthread.php?p=2771308](http://ubuntuforums.org/showthread.php?p=2771308) I assume it should look *something *like this:

Section "Device"
Identifier "Intel 845"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 64000
Option "UseFBDev" "false"
Option "RenderAccel" "true"
Option "AddARGBGLXVisuals" "True"
Option "XAANoOffscreenPixmaps" "true"
EndSection

The vesa driver will not work.

---

### Post by smartsaah on 2007-06-13
I myself just installed Bery after intital gitches...inspite being a newbie to the Ubuntu and Linux world, what i understood is that, 1.MHz wont give you the desired performance...turning of Bery can even slow down your whole system and may lead towards its freezing altogether!

I suggesest you not to install Beryl in this configuration...may be you should really get an uptodate PC for the latest 3D graphics...

---

### Post by CheeseEatingBulldog on 2007-06-13
Just to add some disbelief, I just upgraded my vaio to feisty which uses the i810 driver, and with the built in AIGLX it runs desktop effects, albeit with some residue some time...but the built in card has 4MB for graphics!

---

