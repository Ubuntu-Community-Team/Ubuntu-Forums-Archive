---
title: "Black Screen after splash screen"
date: 2008-05-15
forum: Apple Hardware Users
---

### Post by crapple on 2008-05-15
Hi I am getting a black screen after the splash screen.

This is my computer except mine had more ram put in
[URL="http://www.everymac.com/systems/apple/emac/stats/emac_800_ati.html"]
http://www.everymac.com/systems/apple/emac/stats/emac_800_ati.html[/URL]

It is a ppc g4.


I have tried this but none of it is the same in hardy

[URL="https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8"]
https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8[/URL]


Any other ideas

Thanks

---

### Post by stream303 on 2008-05-16
Sorry to hear the PPC eMac upgrade didn't go well - I know it has been giving you problems after reviewing your threads in the PPC archives.  We must be missing an important step.

I saw in your recent post about having 6.06 Dapper actually running on it.  This is good.  We can use that info to help out Hardy.

Can you backup or write down your existing /etc/X11/xorg.conf file from 6.06?  Can you post it here?

The main issues that the eMacs seem to face is that you need to get to some sort of virtual terminal, because later on you'll need to manually modify your /etc/X11/xorg.conf files to have the right driver (ati), and also the right HorizSync (71-73) and VertRefresh (70-140), although I did see different values based on this:
[http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/](http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/)

The "monitor" section of xorg.conf in hardy with manual editing would look something like this: (although according to the values in the link above, they are a bit different)
```
Section "Monitor"
        Identifier      "Configured Monitor"
        **HorizSync     71-73**
        **VertRefresh   70-140**
EndSection
```

And your manually edited "Device" section would look something like this  (YOUR BusID will be different):
```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Driver       "ati"**
EndSection
```

I think the key issue for us to help is to know *exactly* what you have tried, and have not tried, other than saying that the faqs didn't work.  We're probably stumbling over just one little thing...

---

### Post by crapple on 2008-05-16
I don't have a copy of the old config file.
I decided to do a fresh install.

I will try to find out the info another way.


I have only  tried those to things.  But the faq x config had different things then mine.

---

### Post by stream303 on 2008-05-16
Ok, step one will be to see what happens prior to actual install, and what happens post install of Hardy 8.04 PPC

Which installer are you using: "alternate", "live-cd desktop", or "server"?  Many would recommend the "alternate" unless you are severely limited in ram.

Sooo..  are you actually able to install and see something on the screen, or does it fail at this point?

---

### Post by crapple on 2008-05-17
I used the alternative install cd.  The system installed fine I can see the splash screen.  But after that the screen goes black.

I have tried editing the file but it isn't working.

---

### Post by neorou on 2008-05-17
I wonder if it is possible you may need to reset your battery clock or buy a new on?

[http://www.macbattery.com/3.6-volt-battery/36voltbattery.html](http://www.macbattery.com/3.6-volt-battery/36voltbattery.html)

I think gdm does not load if the system clock is set back to 1970 or whatever it is set back to.

---

### Post by crapple on 2008-05-17
No it is not my clock because I have checked the system time and it is a normal time.

---

### Post by stream303 on 2008-05-17
Ok, that's great news.  Since you can edit the xorg.conf file, we know you can get to a virtual terminal with hardy.  We can also rule out the date issue.  We also know that Dapper 6.06 works on your eMac.

So the only thing left is your /etc/X11/xorg.conf file in Hardy.

(One option would be to install Dapper again, and be sure to write down what is shown in the xorg.conf there, and we can apply some of those values into Hardy's xorg.conf)

I'm assuming you changed the driver to "ati" and changed the HorizSync and VertRefresh values as shown.

Now we just need to keep track of what you have tried in xorg.conf.

Can you try disabling glx and dri?  Try adding this to the bottom of your xorg.conf file:

```
Section "Module"
   Disable "glx"
   Disable "dri"
EndSection
```

It would be helpful if we could actually see your edits to the xorg.conf file as you go.  Since Hardy's file is pretty bare, it seems that it wouldn't be too hard if you had to manually post them here.  This way we can keep track of what you actually have in that file.

One other option would be to change the horiz and vert values to those that were shown in that blog link and let us know how that goes.

---

### Post by oswaldkelso on 2008-05-17
Maybe?

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/153599](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/153599)

---

### Post by jla on 2008-05-17
I have an old G3 imac which I installed Hardy Heron on. At first it didn't boot to X11  and startx didn't work. I added a modeline to the monitor section and it starts to X11 fine now. You must know your screen size and frequency that it runs at ie 1024x768 @75 mhz. Then google modeline and you can find a chart with your numbers on it. Edit /etc/X11/Xorg.conf and  in the monitor section add a line like. Modeline "1024x768" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync.

---

### Post by crapple on 2008-05-18
I am reinstalling drapper.  I will make a copy of the X11 conf file and post it here when it is done.
Then can someone tell me what to do with it?


Thanks

---

### Post by crapple on 2008-05-18
This is my X11 conf in drapper

```
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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
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
	Identifier	"ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	71-73
	VertRefresh	70-140
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
	Monitor		"iMac"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

```

Now what do I do.  It won't let me update I have to do a fresh install.

Thanks

---

### Post by avtolle on 2008-05-19
First: reinstall 8.04.

Second: when the black screen appears, get to a terminal (Ctrl+Alt+F1, e.g.) and update the system:```
sudo aptitude update && sudo aptitude upgrade
```Then, after all the updates, etc., have downloaded and installed, restart the computer. From terminal ```
sudo shutdown now
```. 
Third, when you restart the system, if the black screen still appears, get to a terminal and```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak #make a backup
sudo nano /etc/X11/xorg.conf
```which will allow you to edit the file.
Scroll through the file until you find Section "Monitor" and type the following```
HorizSync 71-73
VertRefresh70-140
``` before the words "EndSection".
Then, scroll down to Section "Screen" and type```
Subsection "Display"
Modes "1024x768"
EndSubsection
``` This needs to be added before the words "EndSection".
Then, scroll down to the end of the existing file, and add the following:```
Section "DRI"
Mode 0666
EndSection
```at the end of it. 
Then, still at the terminal```
Ctrl+O #writes the changes to the file
Enter #to save file as xorg.conf
Ctrl+X #to exit Nano
sudo shutdown now #to shut system down
```.
Reboot, and see if the display works.
If it does, then you've done it; if it doesn't, more editing may be required.

I note that a week or so ago, after manually editing my xorg.conf file to the specs given earlier in another thread, I added Screens and Graphics to my Application Menu, and from there, was able to particularly identify my monitor, my graphics card, etc., so that what now appears in my xorg.conf file is more like what "used to be there". However, until one is able to get the display going, this is of little help.

---

### Post by avtolle on 2008-05-19
After adding screens and graphics to the application menu, and running it, choosing the correct display, and graphics card, the current version of my /etc/X11/xorg.conf file reads as follows"
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
    Fontpath    "/usr/share/fonts/X11/misc"
    Fontpath    "/usr/share/fonts/X11/cyrillic"
    Fontpath    "/usr/share/fonts/X11/100dpi/:unscaled"
    Fontpath    "/usr/share/fonts/X11/75dpi/:unscaled"
    Fontpath    "/usr/share/fonts/X11/Type1"
    Fontpath    "/usr/share/fonts/X11/100dpi"
    Fontpath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    Fontpath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load        "i2c"
    Load        "bitmap"
    Load        "ddc"
    Load        "extmod"
    Load        "freetype"
    Load        "int10"
    Load        "vbe"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS"
    Boardname    "ati"
    Busid        "PCI:0:16:0"
    Driver        "ati"
    Screen    0
    Option        "MergedFB"    "off"
EndSection

Section "Monitor"
    Identifier    "Apple Studio"
    Vendorname    "Apple"
    Modelname    "Apple Studio Display 15 LCD"
    Horizsync    28.0-49.0
    Vertrefresh    60
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS"
    Monitor        "Apple Studio"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes        "1024x768@60"    "800x600@60"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    Inputdevice    "stylus"    "SendCoreEvents"
    Inputdevice    "cursor"    "SendCoreEvents"
    Inputdevice    "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection
Section "ServerFlags"
EndSection

I post it here for informational purposes, not as a specific file that everyone's file should look like. Apparently, using the Screens and Graphics application is the correct way to get the xorg.conf properly configured, but I'm not sure how this would work from the CLI.

---

### Post by crapple on 2008-05-19
Now it just goes into text mode and no black screen but no graphical thing etheir.  What else can be done.

---

### Post by avtolle on 2008-05-19
> **crapple said:**
> Now it just goes into text mode and no black screen but no graphical thing etheir.  What else can be done.
OK, have you tried Ctrl+Alt+F7 to get to the GUI? 
Another thought: at the terminal, type "startX' (without the quotes) and if you get an error message that X is already running, at least we'll have some clue about what is going on.

---

### Post by crapple on 2008-05-19
I had to remove this section or it gives me error can't find screen.

```
Subsection "Display"
Modes "1024x768"
EndSubsection
```

It says the x server is already running.

But now I am back to the black screen.

---

### Post by jla on 2008-05-19
Try looking here and at the external links to common modeline sizes.

Or Google modeline and you can learn something about how CRT works.

[http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline),

I swear I don't know much about modelines but these numbers  from this chart copyed into the monitor section along with horizsynch and vertrefresh got my imac going.I still have to log in to the text terminal and then startx to get the video going.From what I've read the modeline numbers translate the digital part of the computer into analog signals that the CRT uses to run.

---

### Post by crapple on 2008-05-20
Thanks for the reply. I will try it but if anyone can try and explain in more detail that would be great.

---

### Post by oswaldkelso on 2008-05-27
This seems like what has happeded to my debian testing install.  Bug #457612 

I did read somewhere of how to get it working (down grade xorg I think it was) but the debian devs are trying to fix it properly and as I have more than one pc thought it better to let my emac be a crash test dummy.

---

### Post by crapple on 2008-09-16
I have gotten my exact configuration file from dapper into hardy but still no go any other ideas?

---

### Post by milkwood on 2008-09-16
You should try this below.

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

After booting is complete:

1.Type: ctrl-option-F1 (should give you a command prompt, may take a couple of tries)
2.Type: sudo nano /etc/X11/xorg.conf (return)
3.In the Monitor section, change "HorizSync" to 58-62 and "VertRefresh" to 75-117.
4.Disable DRI. In the Module section, put a hash mark (#) at the beginning of the line containing "load dri".
If you have no Module section, make one like this:

Section "Module"
  Disable "glx"
  Disable "dri"
EndSection

5.Type: ctrl-O (return) to write edited file
6.Type: ctrl-X to exit nano back to command line

then,just type "reboot",and press enter.


Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 58-62
        VertRefresh 75-117
EndSection

Section "Module"
   Disable "glx"
   Disable "dri"
EndSection

good luck!

---

