---
title: "emachines onboard graphics + PCI nvidia card (Fatal server error: no screens found)"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by xrobx on 2007-08-12
Hello everyone, i'm brand new to ubuntu. i've only messed around with linux otherwise using a damn small linux live CD. So I've decided i'd like to try and Dual boot windows XP and ubuntu 7.04 off of my about 4 years old emachines. First off I'd like to just get the live CD to work. 

well when I start the CD and after the loading screen, it goes to a black screen where it takes like 5 minutes trying to find which drive my CD is in. I think this has to do with my DVD drive being primary but its broken...so after a certain number of failed attempts it searches my normal CD drive. and all goes well. 

Then, after that it does all its checking with the [OK]'s and stuff. But after that part, I get all of these little dialogs and such asking me to view diagnostic files and stuff. I get sent back to a command line and this is the error:

```

(EE) I810(0): Cannot read V_bios
(EE) I810(0): VBE Initialization failed.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

I've been searching around on these forums for a bit to try to find an answer, but the threads that are a bit similar to my problem haven't been answered.

So far, I've memorized a few commands: startx, sudo, nano, lspci...

and i've tried to use these to solve my problem:

sudo dpkg-reconfigure (with and without -phigh) xserver-xorg


after doing it without -phigh, on the dialog where it asks where your video card is, it can only find my onboard graphics... I've even already gone into the bios and chosen it to use PCI and not onboard...

As for last measures, I've even changed it back to onboard... when i boot the CD, i get a boot screen but after i choose to start the CD, a quick "Loading..." thing flashes in the top left corner but after that, it's just black...

so basically my problem is, it doesnt recognize my nvidia geforce FX5500.

I really prefer not to download another thing like that alternate installer. also i'm reluctant to even try to install yet, when i partitioned my C: on windows, it said a few files couldn't be moved. i dont know if i should worry about that or not. also, i don't really know of a good way to install this stuff as dual boot. i heard the live CD doesnt always partition it correctly, and things like that. anyway, if any of you have an answer to any of these problems, i'd greatly appreciate your time. thank you very much.

---

### Post by hamburglar6 on 2007-08-12
when you reconfigure xorg what driver do you choose.  in case you haven't yet, try 'nv' first and if that doesn't work try 'vesa'.  if your install works after that you will probably want to install the proprietary drivers from nvidia using Envy which can be found here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).  

also it would be a very good idea to back up any important documents on your windows partition before actually doing the install, if you haven't already.

---

### Post by hamburglar6 on 2007-08-12
sorry xrobx i misread your problem.  what is the output of lspci?  if your card isn't being recognized at all then how are you getting output on your screen?

---

### Post by Gremlinzzz on 2007-08-12
my problem is, it doesn't recognize my nvidia geforce FX5500. well at least you know your problem Now whatca going to do about it.I would remove the a fending card install ubuntu then put card back and try envy.Will this work i don't know.the easiest way i found to install ubuntu dual boot  is live cd.create a partition for ubuntu then delete it making it free space then when prompt choose== guide use largest continuous free space .that's it let ubuntu do the rest.

---

### Post by xrobx on 2007-08-12
well actually i think its fussing at the fact that i have an onboard card and a separate card i upgraded to, and can't figure out which one to choose. I just know when i switch to onboard from the bios, I dont get passed the first boot screen. The next screen is just black...

I'd just really like to get the liveCD working before I try to do an actual install, and also that would be impossible to install without it working correctly (right?) since i don't want to download alternate installer.

EDIT:

ok so i've been messing around with it and stuff. i went in through safe graphics mode, but it still failed. but anyway,  through lspci i found out that it actually has detected my nvidia card. in my xorg.conf file, it doesnt say intel anymore, it just says "generic video card" but when i change the busid thingy to 02:09:0 (this is what lspci said my nividia card was at, it works now. so atleast i can get it to work. also i dont remember very well i think i chose vesa too. maybe nv. i'll check again and update you

another edit:

okay so in my xorg.conf file:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:02:09:0"
EndSection

previously the BusID was "PCI:0:2:0", which i'm guessing that was my onboard graphics.

---

### Post by hamburglar6 on 2007-08-12
so now that your card is detected is the livecd working?  if not, try switching 'vesa' to 'nv' and then restarting X.

---

### Post by xrobx on 2007-08-12
> **hamburglar6 said:**
> so now that your card is detected is the livecd working?  if not, try switching 'vesa' to 'nv' and then restarting X.

yes, the live CD is functional. i haven't tested it without using safe graphics mode, but i imagine if i follow the same steps, it will work. what do you think? next, i'm going to install ubuntu, so everything will be dual boot. i did like you said, and backed up all my files. and i already defragged. i'll let you know how it went.

---

### Post by xrobx on 2007-08-13
ok i need some help i think... i'm at the partitioning step. it shows my C: , my thumbdrive, and my external drive. i dont wanna use the entire disk so i choose manual. if i choose the main thingy i can create a new partition, but a message pops up that sounds like it will delete everything on there. and if i click on the actual disk thingy that says 80GB, i can only delete or edit the partition. how can i make this work? i'm trying to dual boot XP (already installed) and ubuntu 7.04 (trying to install now) but i'm not so sure about these messages...

edit:

ok i see the normal installer doesnt let me resize the 74GB partition, so i tried gparted, and it failed to resize it...any tips??

edit again:

well i'm using partition magic (in windows xp) to resize my C:\ partition. i hope it doesnt mess it up and render it unbootable...

---

### Post by hamburglar6 on 2007-08-13
yeah i think thats just about the only way to go.  you should always backup important data before trying to resize a partition.  hope all goes well.

---

### Post by xrobx on 2007-08-13
alright everythings up and running. ubuntu is installed. both OSes still boot. i just dont know if my graphics card is being used to its full potential. i mean according to my xorg.conf, it still thinks its integrated...

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"vesa"
	BusID		"PCI:02:09:0"

(originally the BusID was 0:2:0. i had to change it to my nvidia card; BusID)

so is there any way to sucessfully install drivers? for geforce FX 5500? because i've tested 3D already: screensavers. and they lag pretty bad. by the way, thanks for all the help so far guys :)

---

### Post by hamburglar6 on 2007-08-13
use the link in my first post to download the Envy script and it will download and install the appropriate drivers for you.  after you do that run the command
```
glxinfo | grep direct
```

and it should tell you that direct 3D rendering has been enabled. let us know how it goes.

---

### Post by xrobx on 2007-08-13
> **hamburglar6 said:**
> use the link in my first post to download the Envy script and it will download and install the appropriate drivers for you.  after you do that run the command
```
glxinfo | grep direct
```

and it should tell you that direct 3D rendering has been enabled. let us know how it goes.

well i installed the envy thing, it said it went through. then i went to terminal and pasted that command. it appears there was failure:

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

---

### Post by hamburglar6 on 2007-08-13
could you post a copy of your xorg.conf?  also, when you boot up your computer into ubuntu, do you see the nvidia splash screen?  when you use the 3D screen savers do they work correctly now?

---

### Post by xrobx on 2007-08-13
> **hamburglar6 said:**
> could you post a copy of your xorg.conf?  also, when you boot up your computer into ubuntu, do you see the nvidia splash screen?  when you use the 3D screen savers do they work correctly now?

```
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"vesa"
	BusID		"PCI:02:09:0"
EndSection

Section "Monitor"
	Identifier	"SDM-HS75P"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SDM-HS75P"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
```


i haven't rebooted since i installed envy thingy

at this moment, using the screen savers, they still lag a bit

---

### Post by hamburglar6 on 2007-08-13
ok- you are still using the vesa driver.  use envy again to uninstall the driver, and then install the driver again.  this time when it asks you if you want it to automatically update your xorg.conf say yes, and also say yes when it asks you if you want to reboot.

EDIT: just in case i wasn't clear- after you install envy, you still need to run it.  you can either go to Applications > System Tools > Envy or type envy -g in a terminal window.

---

### Post by xrobx on 2007-08-13
ohhh, i didn't know to run it. well i ran it, uninstalled the drivers, installed them and got an error. it told me to check the log file

```
python pulse.py nvidia
root@rob-desktop:/usr/share/envy# python pulse.py nvidia
Ubuntu Feisty 32bit
Your graphic card has been detected as a GeForce FX 5500
Your graphic card is supported by the latest driver
ENVY: The following packages are not installed:
linux-headers-`uname -r`

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatk1.0-dev libaudio-dev libbeecrypt6 libcairo2-dev libcupsys2-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev
  libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev
  libgpg-error-dev libice-dev libjpeg62-dev liblcms1-dev liblzo-dev libmng-dev
  libopencdk8-dev libpango1.0-dev libpng12-dev libpopt-dev libqt3-headers
  libqt3-mt librpm4 libsm-dev libtasn1-3-dev libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxt-dev
  mesa-common-dev qt3-dev-tools x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xf86misc-dev
  x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libgcrypt11-doc libglib2.0-doc gnutls-doc gnutls-bin
  libgtk2.0-doc libpango1.0-doc imagemagick libqt3-mt-psql libqt3-mt-mysql
  libqt3-mt-odbc libqt3-i18n qt3-doc alien mailx
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  kernel-wedge libatk1.0-dev libaudio-dev libbeecrypt6 libcairo2-dev
  libcupsys2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgcrypt11-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev
  libgnutls-dev libgpg-error-dev libgtk2.0-dev libice-dev libjpeg62-dev
  liblcms1-dev liblzo-dev libmng-dev libopencdk8-dev libpango1.0-dev
  libpng12-dev libpopt-dev libqt3-headers libqt3-mt libqt3-mt-dev librpm4
  libsm-dev libtasn1-3-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev
  libxmu-headers libxrandr-dev libxrender-dev libxt-dev libxtst-dev
  libxxf86misc-dev libxxf86vm-dev mesa-common-dev qt3-dev-tools rpm sharutils
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev zlib1g-dev
0 upgraded, 65 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.5MB of archives.
After unpacking 79.8MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  x11proto-core-dev libice-dev libsm-dev libxau-dev libxdmcp-dev
  x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-render-dev
  libxrender-dev x11proto-xext-dev x11proto-fixes-dev libxfixes-dev
  libxcursor-dev libxext-dev libexpat1-dev zlib1g-dev libfreetype6-dev
  libfontconfig1-dev libxft-dev libxi-dev x11proto-xinerama-dev
  libxinerama-dev libxmu-headers x11proto-randr-dev libxrandr-dev libxt-dev
  x11proto-record-dev libxtst-dev x11proto-xf86misc-dev libxxf86misc-dev
  x11proto-xf86vidmode-dev libxxf86vm-dev kernel-wedge libglib2.0-dev
  libatk1.0-dev libbeecrypt6 libpng12-dev libcairo2-dev libgpg-error-dev
  libgcrypt11-dev libtasn1-3-dev libpopt-dev libopencdk8-dev liblzo-dev
  libgnutls-dev libcupsys2-dev mesa-common-dev libgl1-mesa-dev
  libglu1-mesa-dev libpango1.0-dev libgtk2.0-dev libjpeg62-dev liblcms1-dev
  libmng-dev libqt3-headers libqt3-mt libxmu-dev libaudio-dev qt3-dev-tools
  libqt3-mt-dev librpm4 rpm sharutils
E: There are problems and -y was used without --force-yes
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev
```

---

### Post by hamburglar6 on 2007-08-13
make sure you have all of the correct software repositories enabled.  go to system > administration > software sources and enable the 'universe' and 'multiverse' repositories.  if that doesn't work could you post a copy of your /etc/apt/sources.list?

---

### Post by crzyakta on 2007-09-25
bump, whats the update on this?

---

### Post by louieb on 2007-09-25
Try a better live CD. I've found that DSL and Knoppix will boot to the desktop when others fail.  If one gives you a desktop then you can be pretty sure the Ubuntu alternate install will give you a desktop too. 

I didn't see it but how much memory does this pc have?

---

### Post by doorknob60 on 2007-10-04
I have the same problem with my PCI nVIDIA GeForce FX 5200...hopefully this works...

---

