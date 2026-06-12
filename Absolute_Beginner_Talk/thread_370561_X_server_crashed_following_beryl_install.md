---
title: "X server crashed following beryl install"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-02-25
I followed wiki's guide on how to install beryl.
[HTML]http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia[/HTML]
I created the script via the automatic directions, executed it, and restarted. This is where I believe the problem occured. When X tried to start now, the blue screen comes up. After further review, no devices were detected to load display, and it kicks me out to the command line.

The script automatically creates a backup of the xorg.conf file, so I uninstalled beryl.

```
sudo aptitude remove beryl
```

This removed beryl and beryl manager. Then I restored the backup of xorg.conf.

```
sudo mv xorg.conf.backup.beryl-install(or something to that effect) xorg.conf
```

I'm thinking that everything will go back to normal right? Wrong. X server still refuses to start. How can I get X back up? Thank you!

---

### Post by STREETURCHINE on 2007-02-25
if you backed up try

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

restart x

```
ctrl>alt>backspace
```

---

### Post by StarscreamD on 2007-02-25
No, I explained in my post that I did restore my previous xorg.conf file. Perhaps the script installed the incorrect nvidia driver?

My setup is a 1.3 Ghz Celeron with 512 mb of SDRAM, and a NVIDIA GeForce 420 MX.

---

### Post by STREETURCHINE on 2007-02-25
sudo mv xorg.conf.backup.beryl-install(or something to that effect) xorg.conf

this command i feel is wrong that is why it did not work .
try the one above copy and paste it in and restart x and all should be fine

if that dont work try

     gksudo dpkg-reconfigure xserver-xorg

---

### Post by STREETURCHINE on 2007-02-25
oh and dont forget to restart x

ctrl>alt>backspace.

if that dont work post back and we will try something else.

---

### Post by StarscreamD on 2007-02-25
This code:

```
gksudo dpkg-reconfigure xserver-xorg
```

Did this:

> (gksudo:3725): Gtk-WARNING **: cannot open display

I couldn't use your first suggestion because I had already exectuted the mv command, so there is no original backup file to use the cp command on. What do you think?

---

### Post by STREETURCHINE on 2007-02-25
just out of interest try sudo instead of gksudo


              ```
sudo dpkg-reconfigure xserver-xorg
```


if it works just use the defaults if you dont know

---

### Post by StarscreamD on 2007-02-25
sudo, instead of gksudo worked. I installed all of the defaults, and the exact same error occurs. Again, I have an NVIDIA GeForce MX 420 video card, so my question is this:

Would that affect initial setup of the card? Maybe that fact does not let my video card fall under the criteria of default. Thank you for your help so far, STREETURCHINE.

---

### Post by STREETURCHINE on 2007-02-26
> **StarscreamD said:**
> 
Would that affect initial setup of the card? Maybe that fact does not let my video card fall under the criteria of default. Thank you for your help so far, STREETURCHINE.

no i dont think so. (but just in case here is a link to the envy script to install your drivers)
   
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

do you have a live cd or dvd

i take it you cant use edgy at the moment 

do you duel boot and can access the etc/X11 file

---

### Post by StarscreamD on 2007-02-26
Yes I dual boot, and can access the xorg.conf file. I also have a live cd. Edgy is down, except the command line.

---

### Post by STREETURCHINE on 2007-02-26
ok you should be able to run the live disk mount the hard drive and paste the xorg.conf from the disk to your  harddrive X11.

it will put you back to the base setup

or you can try searching through edgy from your outher os ,
find the backup if any and paste the contents to your X11 file reboot to edgy and it should work.well with a bit of luck any way

---

### Post by StarscreamD on 2007-02-26
I actually had a total of three different backups on my xorg file, yet I never had to copy at the command line. So when everything went haywire, I used the mv command instead of cp, like you suggested. Did this corrupt my backups somehow? I have tried to use all of the backups as the original xorg file, and all of them have the same error. I remember when I first installed Ubuntu Edgy on my system, that I had to edit some file to get my NVIDIA display card to work properly and boot into X. Whatever I did I miessed that up because it is acting like it did when I first installed Ubuntu. I really hate to reinstall: that is a last resort for me. Got any other ideas?

---

### Post by STREETURCHINE on 2007-02-26
can you paste a copy of your xorg.conf file and i will have a look.

have you tried the live cd

as to reinstalling i have done it many times,i used to fiddle heaps and kept breaking my xorg.conf  lol

if we get it working i will then give you a simple fix for this but we need a working model first.

---

### Post by StarscreamD on 2007-02-26
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"nvidia"
	#BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"No Logo"
EndSection

Section "Monitor"
	Identifier	"DELL E770s"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"DELL E770s"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


Here is my backup, which was the settings before I installed Beryl. I'm assuming, after I unintall Beryl completely, using aptitude remove beryl, and replacing the modified xorg.conf with my backup, that it would work... right?

As for my live CD, it will work with my onboard video card *if* I move my monitor cable from my aftermarket NVIDIA card to my onboard card. It will not setup my card correctly, however. Maybe I should try envy from the command line..?

---

### Post by STREETURCHINE on 2007-02-26
this is just baffling ,
your xorg looks fine

just to satisfy my curiosity  do

```
sudo aptitude update 
sudo aptitude upgrade
```

from command line and reboot

then try the envy script

then we will blunder on and see where we end up    :lolflag:

---

### Post by StarscreamD on 2007-02-26
I ascertained that I am *supposed* to be using the 1.0-96xx legacy driver that NVIDIA provides. It seems that the beryl script I used didn't apply to my video card. I think it even replaced my working NVIDIA driver with the updated one that isn't suported by my card. I looked into the logs, and it fails on the driver initialization. Gimme a lil while to hash this out...:popcorn:

---

### Post by STREETURCHINE on 2007-02-26
ok post results,,,:)

---

### Post by StarscreamD on 2007-02-26
I fixed that problem, but more popped up in it's place. Here's what had to be done to get X server up:

```
sudo aptitude install nvidia-glx-legacy
sudo aptitude install nvidia-settings
sudo aptitude install-xconfig
sudo nvidia-glx-config enable
```

Came to the conclusion that the newest nvidia driver was automatically installed during beryl installation. After these commands and rebooting, all was well and X popped up as it should. See my next post to learn what happened next...!

---

### Post by Luk0r on 2007-02-26
I really recommend you use envy to get the latest and greatest drivers for your card.  To do this, log out of your desktop (so you're on the login screen) and hit CTRL+ALT+F1, then log in at the command line and do:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb
sudo dpkg -i envy_0.8.2-0ubuntu1_all.deb
envy
```
After doing that, your X server should start up fine.  Then you can proceed to install Beryl: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

---

### Post by StarscreamD on 2007-02-26
I did as you suggested. Thanks for the tip, I really appreciate it!

---

