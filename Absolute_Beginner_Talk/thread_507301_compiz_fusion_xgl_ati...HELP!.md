---
title: "compiz fusion xgl ati...HELP!"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by buffylette58 on 2007-07-22
hey there! I've got a fresh install of 7.04, (ignoring the ati driver in restricted) I installed "Envy" to sort out the driver for my graphics card, ATI radeon 9600 XT. I ran Envy, "uninstalled ATI driver" then "installed ATI driver"....

that all seemed fine, then I tried to install compiz... that all seemed fine too, i installed compiz fusion and emerald, from those tuxfamily repos...

first problem, compiz would not run! i had beryl running nicely on this PC before, but in that instance I did not use Envy, I used the restricted drivers manager and changed a few things in my xorg.conf, which I found on this forum. 

But when trying to run compiz i type 'compiz --replace' and I get an error about 'texture_from_pixmap... unsupported', or something. I cannot get the exact error now.

So I read around the forum, and found stuff about XGL, and aiglx....I don't understand it. So i thought I'd follow a guide on getting Compiz working with an ATI card. But before I did that I thought it would be a good idea to uninstall my video driver, and start from scratch. So I uninstalled my video driver via Envy.

Rebooted, straight into a blue "cannot access X server" screen. So I nano'ed into a backup of my xorg.conf, and found the "driver" was called "vesa"... so I nano'ed into my xorg.conf, changed the driver to VESA, and it let me back into the GUI of ubuntu!

now if I type it, i get:
```
onica@monica:~$ compiz --replace
Fatal: Compiz can't be ran using VESA or VGA divers.

```

So here I am. I could follow a guide getting compiz going with an ATI card, but I'm thinking if I mess with the "startxgl.sh" files it could make things worse. And I'm not sure what to do about the driver anyway, because the latest ATI driver from Envy didn't help.

I think I just need some guidance on what I need to do in this situation! lol

So if anyone could help that would be great...

---

### Post by LuisAugusto on 2007-07-22
Post your sources.list.

---

### Post by buffylette58 on 2007-07-22
u sure thats relevant??

anyway, 

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by LuisAugusto on 2007-07-22
Haha, sorry, I made a mistake I mean your xorg.conf, sorry, sorry, remember drugs are bad xD

---

### Post by buffylette58 on 2007-07-22
LOL :p

well, I didn't think the driver would be the problem, so I reinstalled the driver via Envy, same prob:

```
monica@monica:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

and yea, heres my xorg.conf:

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
	Identifier	"Generic Video Card"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 828FI"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL 828FI"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
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



Section "Extensions"
	Option "Composite" "Disable"
EndSection

```

---

### Post by LuisAugusto on 2007-07-22
Since you're using ATI propietary driver you can't run compiz on top of aiglx. you need to use XGL, install it this way:

```
sudo apt-get install xserver-xgl
```

```
sudo gedit /usr/local/bin/startxgl.sh
```

Copy and paste this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

```
sudo mkdir /etc/X11/sessions
```

```
sudo gedit /etc/X11/sessions/xgl.desktop
```

Copy and paste:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

```
sudo chmod a+x /usr/local/bin/startxgl.sh 
```

Now, restart your computer and in GDM select XGL sessions instead of GNOME.

---

### Post by buffylette58 on 2007-07-22
ok thanx 4 ur help...that all seemed to work, except when I log into the XGL session, everything is distorted, the icons, the text...I would've got a screenshot if I could see where I was going... :p

So now I'm back in 'Xclient'

---

### Post by LuisAugusto on 2007-07-22
> **buffylette58 said:**
> ok thanx 4 ur help...that all seemed to work, except when I log into the XGL session, everything is distorted, the icons, the text...I would've got a screenshot if I could see where I was going... :p

So now I'm back in 'Xclient'

Did you restart the computer?, that sounds like not, but it may be your envy installed driver, I have the same ATI as you, it works fine for me whit the driver from the repos (from the restricted driver manager).

Hope this help you.

---

### Post by buffylette58 on 2007-07-22
yea i restarted the PC

does my xorg.conf look ok?

ok, so if it's a driver issue, how do I revert back to the driver from the repos? When I uninstalled the ATI driver in Envy, i got the blue 'cannot find x server' screen

---

### Post by LuisAugusto on 2007-07-22
After uninstall the envy driver run, don't reboot:

Run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then reboot.

Then install the fglrx driver from restricted driver manager.

---

### Post by buffylette58 on 2007-07-22
I just tried reverting back to an earlier driver in Envy, (8.28.8), rebooted, loaded into XGL, and Compiz Fusion is working awesomely! :D

thanx 4 yo help buddy ;)

---

### Post by LuisAugusto on 2007-07-22
> **buffylette58 said:**
> thanx, but i got impatient lol, and I just tried reverting back to an earlier driver in Envy, (8.28.8), rebooted, loaded into XGL, and Compiz Fusion is working awesomely! :D

thanx 4 yo help buddy ;)

You welcome, I'm glad you finally got it to work.

See you.

---

### Post by buffylette58 on 2007-07-23
hii, I'm back! :p

all the drivers from Envy do the same thing, stuff up somehow! I guess this is because my ATi Radeon 9600XT is too old for these drivers.

so what I want to do is revert back to an older driver, which suits my graphics card, or revert back to the driver from the restricted drivers, because that seemed to work on a previous installing with Beryl (I'm not sure how different it's all going to be with compiz fusion)

After uninstalling the drivers via Envy, I tried "sudo dpkg-reconfigure -phigh xserver-xorg" and went through the setup, chose "vesa" for the driver (ati or vga didn't seem to work), and booted back into ubuntu.... but the ATi restricted drivers module did not appear!

My sources.list is fairly default, so I don't think that is the issue.

can anyone help?? I've been at this all day! :p

---

### Post by buffylette58 on 2007-07-23
I've tried looking up which exact driver version is suitable for my card, and how to install it, but I haven't had much luck.

Or, reverting back to the 'restricted drivers' driver should do the trick, if I can get that to appear.

Hmm, can anyone help me out? :)

---

### Post by sad_iq on 2007-07-23
type ```
gksu restricted-managet
``` that will sytart it!

---

### Post by buffylette58 on 2007-07-23
umm, na i mean for the ATi driver to appear in restricted drivers, like it used to?

---

### Post by freebird54 on 2007-07-23
You should be able to pull it from Synaptic (or using apt-get).  The one in the repos works fine for older ATI (mine's a 9550) .  Not sure what version is in the Feisty repos - as my system was upgraded from an Edgy install - so fglrx 8.28.8 is what I'm running.

Checking Synaptic.....  looks like you acquire as linux-restricted-modules-2.#.## etc...

Once it's there - make sure the bolded bits in this Xorg.conf are in yours..

```
freebird@roost:~$ cat /etc/X11/xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
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

[B]Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection[/B]

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
					        # /dev/input/event
        # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"       # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"       # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                # /dev/input/event
                                                # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"       # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"       # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                # /dev/input/event
                                                # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"       # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"       # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Radeon 9550"
[B]        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"[/B]
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon 9550"
        Monitor    "Samsung_900iFT"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

[B]Section "Extensions"
        Option      "Composite" "Disable"
EndSection[/B]
```


Usually that should be enough if other versions were sufficiently removed.  If not - let us know and we'll tell you some more tricks :)

---

### Post by buffylette58 on 2007-07-23
ok I tried that, I uninstalled it all via Envy, I reinstalled the fglrx 7.xx.x driver via Synaptic, I patched up my xorg.conf file like above, and i get the same thing.

Whether I disable or enable emerald, compiz, gdesklets or anything I thought may have caused it, I still cannot get compiz again, and the GUI seems buggy, the appz in Sessions take ages to respond and load up, nm-applet/keyring manager starts like 5minutes after being in ubuntu, and it should be instant, and there are no window decorations, only when I 'emerald 
.--replace', but that even stalls after a minute or so....

There seems to be something wrong with my gfx driver, or my xorg.conf file?

I'm pretty lost now :s

Here's my xorg.conf file:

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "ServerFlags"
	Option		"AIGLX" "off"
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
	Identifier	"ATI Radeon 9600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev" "true"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9600"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

Section "Extensions"
	Option 		"Composite" "Disable"
EndSection

```

Any ideas?

---

### Post by sad_iq on 2007-07-23
Ok...this worked for me once..[COLOR="red"]**USE AS A LAST RESORT**[/COLOR]..Make sure compiz (or anything related) won't automatically start and do this:
 ```
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get remove --purge linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver
```
 **Reboot**!!!!
Then do this:
```
 sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) 
sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver
```
 Also make a copy of your xorg.conf before you proceed!!!

---

### Post by buffylette58 on 2007-07-23
that sounds promising, but I don't think it will load into the GUI after the reboot if it's looking for the 'ati' driver, 'vesa' worked tho for some reason. Should I select that instead before I reboot?

also, should i use '-phigh' in the line? so I don't have to select the mouse, keyboard and all those settings, I had to do that before

---

### Post by sad_iq on 2007-07-23
you could choose **--phigh**. Also copy the comands I gave you on paper  in case you have trouble with the ati driver after a reboot...you can still get to a command line and put them from there!!! Choosing vesa shouldn't hurt thou!!!

---

### Post by buffylette58 on 2007-07-23
aite, thanx buddy, here goes! *holds breath*

---

### Post by buffylette58 on 2007-07-23
I'm back! And I followed exactly what you said....and it worked nicely... well, it didn't look buggy. plus the ATI driver was back in 'restricted drivers'. it was ticked but it said 'not in usee' next to it, so I unticked it, and ticked it again, restarted, and I'm back into ubuntu and it's looking like the driver has been resolved.

Now I'll try starting compiz again, and if I have further problems it's probably the xorg.conf needs fine-tuning... I might be back lol but thanx heaps for the help!

---

### Post by sad_iq on 2007-07-23
Glad it worked...bookmark my commands for when you have trouble(well actually they're not mine...just forgot where I got them from :( )...to test if you have your drivers correctly installed type ```
glxinfo | grep direct
``` It should print: "direct rendering: Yes"

---

### Post by buffylette58 on 2007-07-23
awesome, it says rendering yes! but compiz still isn't running....

it's running a bit slow at the start (opening Session appz), but it gets there, maybe it's the gdesklets slowing it down a bit... how do I make gdesklets enabled on startup, without opening the  main managing window? I tried "gdesklets shell -w &", that didn't help.

To get compiz going I think I'll have to fix my xorg.conf again

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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Radeon 9600"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9600"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by buffylette58 on 2007-07-23
I forgot to log in to the XGL session:p that fixed it

ok it all seems sweet now! thanx again the helpin' ;)

---

### Post by freebird54 on 2007-07-23
You might want to edit you rmonitor configuration section to match up with its real capabilities.  Hopefully you can get these from a manual, or off the net by model number.  The Section can look like this:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

```

but that is foir a 'not too capable' monitor, and would yield a max setting of (perhaps) 1024X768 @ 60 Hz.  Below is mine (with settings MUCH more capable in bold):
```

Section "Monitor"
        Identifier   "Samsung_900iFT"
[B]        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0[/B]
        Option      "DPMS"
EndSection
```

These are for a 19 inch CRT - so don't use them!  Find yours, and the weirdness may clear up - espcially if your screen has a particular setting that it likes.

Another thing that can be tried is:

```
gksudo gedit  /etc/modprobe.d/blacklist
```

and add in these 2 lines

```
# causes fglrx to fail and mesa drivers to load
blacklist ati-agp
```

as sometimes there are vestiges of other tings left behind.  Hope these items are enough to get you going!

---

### Post by anja on 2007-07-27
hi ppl! im buffylettes mum!

i've just installed compiz fusion via the tuxfamily repos also...but it wont start
```

anja@anja:~$ compiz --replace
Fatal: Failed test: non-power-of-two texture support
Checks indicate that it's impossible to start compiz on your system.

```

i've got a crappy on-board video card, but it still says "rendering yes"!

i tried creating an XGL session, but it kept going back to the GDM, and wouldnt even load into it

any ideas on how to get it started??

my xorg.conf:
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
	Identifier	"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Optima CM504"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Monitor		"Optima CM504"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by praveenmarkandu on 2007-07-28
hi, i dont mean to hijack this thread but i thought it would be relevant as this is the ONLY thread i found addressing this matter of ati proprietary drivers and compiz-fusion

i have an ati X700mobility and am using the latest drivers from ati. 

i have followed most of your steps sad_iq. its been great. but i do notice that from a fresh start of your pc and logging into XGL its fine. but when you logout or when your computer goes into standby and you try to relogin the graphics become all wonky and stuff. like explained at the end of page 1 of this thread. i have to restart X (ctrl+alt+backspace) and choose XGL in order to get everything right again. 

i tried your next step > sudo dpkg-reconfigure -phigh xserver-xorg
which didnt help at all so i got scared. lol. any pointers would be much appreciated.

my xorg.conf
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
	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Driver		"fglrx"
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
	Device		"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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

---

### Post by freebird54 on 2007-07-29
Not too sure - but you might want to try being careful what screensavers you run.  In my experience (Edgy & Feisty) if you run ATI and XGL, stay away from any 3d-calling screensavers.  If they don't lock you up totally, they will cause screen confusion such as you describe.  The 'slideshow type' ones don't display this problem - and it might not be your problem anyway  :)

---

### Post by praveenmarkandu on 2007-07-29
i came up with a pretty basic but practical solution
administration--> login window --> general tab --> check restart the xserver with each login. 
i basically cuts me out of doing 1 addtitional step which was what was annoying me. this is a great thread. someone should pin it for all those who are using ATI proprietary drivers. next laptop im getting wont have an ATI card thats for sure

---

