---
title: "Synaptic touchpad howto?"
date: 2007-03-30
forum: Apple Intel Users
---

### Post by MacbookGuru on 2007-03-30
Hello Ubuntu Community,

I've recently put Ubuntu (6.10) on my MacBook (Core 2 Duo) and I've got everything working except the mouse. Or, rather, the touch pad. Sure, it has worked just fine by default, but I've been told that if I wanted to do more advanced things such as two finger scrolling or two finger right click I need to install synaptic drivers.

The problem is all of the tutorials I've read are just a little too presumptuous that I know what it means to 'just add such-and-such line to this-and-that file' but never say where the file is, or just exactly how to do some of the other things they say to do. If someone could please help with maybe a step-by-step guide on how they managed to get synaptic driver to work on their macbook that would be awesome! Thanks for any help you might be able to give.

---

### Post by cyberdork33 on 2007-03-30
synaptics should already be installed.

Look in your /etc/X11/xorg.conf file in the Touchpad section. You can only edit this file if you use sudo. You will see where the Driver is set to synaptics. there are a few options set already, and many more that are not set. At the command line, you can type:

```
 man synaptics 
```

and it will describe the different options available. To use any of the options, simply add another line in the touchpad section of the xorg.conf file, with the option's name and the desired setting.

Example of format:
```
 Option "YourOptionName" "true" 
```

Hope this helps!

---

### Post by kerry_s on 2007-03-30
Grab qsynaptics or gsynaptics. qsynaptics is the best to me, it offers more features.

sudo apt-get install qsynaptics

sudo gedit /etc/X11/xorg.conf

add this line to the "synaptics" touch pad section.

Option "SHMConfig" "true"

(i noticed a bug in which some xorg.conf's are missing the synaptic section. To get it run this in terminal" sudo dpkg-reconfigure -phigh xserver-xorg ")

---

### Post by jdriessen on 2007-03-31
kerry_s, Thankyou for yor quick guide on installing Synaptics TouchPad. I had to reconfigure my xorg.conf file using the command you posted and thenk It works, ha! no more fumbling about tapping things by mistake!

I'd like to know how I can enable/disable tapping, or other features of the touch pad, am I right in presuming this would be in xorg.conf?
as described by cyberdork33?

---

### Post by kerry_s on 2007-04-02
> **jdriessen said:**
> kerry_s, Thankyou for yor quick guide on installing Synaptics TouchPad. I had to reconfigure my xorg.conf file using the command you posted and thenk It works, ha! no more fumbling about tapping things by mistake!

I'd like to know how I can enable/disable tapping, or other features of the touch pad, am I right in presuming this would be in xorg.conf?
as described by cyberdork33?

No, you just open the qsynaptic program and uncheck next to enable, it has a check box for each setting, so you can just disable scrolling or tapping. You might want to make a launcher or menu command or just use alt+F2 type qsynaptics. I try a put a pic later when i go to grandmas, I set it up on her laptop.

---

### Post by jdriessen on 2007-04-10
thanks again, it was easy once i found the touchpad control panel...

---

### Post by Azathoth_ on 2007-04-10
If you launch now qsynaptics, you can choose some options with 2 or 3 fingers

---

### Post by Chrisj303 on 2007-04-11
> **kerry_s said:**
> Grab qsynaptics or gsynaptics. qsynaptics is the best to me, it offers more features.

sudo apt-get install qsynaptics

sudo gedit /etc/X11/xorg.conf

add this line to the "synaptics" touch pad section.

Option "SHMConfig" "true"

(i noticed a bug in which some xorg.conf's are missing the synaptic section. To get it run this in terminal" sudo dpkg-reconfigure -phigh xserver-xorg ")

This is driving me MAD! - I need to add the line 'Load    "synaptics"' to my /etc/x11/xorg.conf , in order to load the synaptics touchpad driver. No matter how i go about it, it will not let me save! I've tried 'sudo gedit /etc/x11/xorg.conf' , i've tried 'sudo su - ' then it still will not let me edit then save xorg.conf!
What am i doing wrong - surely it can't be this difficult! 


cheers,
chrisj303

---

### Post by katabatic on 2007-04-17
> **Chrisj303 said:**
> This is driving me MAD! - I need to add the line 'Load    "synaptics"' to my /etc/x11/xorg.conf , in order to load the synaptics touchpad driver. No matter how i go about it, it will not let me save! I've tried 'sudo gedit /etc/x11/xorg.conf' , i've tried 'sudo su - ' then it still will not let me edit then save xorg.conf!
What am i doing wrong - surely it can't be this difficult! 


cheers,
chrisj303



Linux is case sensitive. You must write X11, not x11

---

### Post by psynyd on 2007-04-17
Are u trying to edit the file from your mac os partition? It won't let you do that. You have to be logged in from ur ubuntu partition.

Cheers!

---

### Post by Chrisj303 on 2007-04-17
I managed to edit my X11/xorg.conf - i used nano instead of gedit, and it let me save.. But after adding the 'Load synaptics' line , then saving - qsynaptics is still giving me the message 'need to install qsynaptics driver' !. It is definitly installed though, so i'm really at a loss as what to do..

Right now, when i load the 'qsynaptics' all the options are greyed out - it won't let me change a single setting.
I don't know - i'm seriously starting to reconsider Linux, EVERYTHING regarding ubuntu seems such a headache, especially when i have OSX on the next partition.


cheers,
chrisj303

---

### Post by cyberdork33 on 2007-04-18
Did you add this portion:
> add this line to the "synaptics" touch pad section.

```
Option "SHMConfig" "true"
```

I am not sure how you are adding a "Load Synaptics" line, but that is not really what you need to do... You should have a device section in your xorg.conf for your touchpad something like this:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```

This will "load"the synaptics driver to be used with your touchpad. The ```
Option "SHMConfig" "true"
``` line may need to be added in this section for qsynaptics to work.

---

### Post by Chrisj303 on 2007-04-18
Yes - i ve done all the above, and no joy.

I added the 'Load          "synaptics" '  line to the modules section of xorg.conf, as i read in another thread that this was needed.

chrisj303

---

### Post by cyberdork33 on 2007-04-18
> **Chrisj303 said:**
> Yes - i ve done all the above, and no joy.

I added the 'Load          "synaptics" '  line to the modules section of xorg.conf, as i read in another thread that this was needed.

chrisj303

Well I have never heard of adding that before... but if it isn't giving errors i guess you can't complain.
If your config is setup as above then IDK what else to tell you. I am assuming you have restarted the x server...

---

### Post by ry4nolson on 2007-04-19
what version of ubuntu are you using? if you're using edgy you need a newer kernel.  I also don't know why you're adding Load "synaptics"

near the bottom of xorg.conf you need to add to the Server Layout section.

InputDevice	"Synaptics Touchpad"

and also this may sound obvious/dumb but are you restarting? sometimes restarting x just isn't enough.

---

### Post by Chrisj303 on 2007-04-19
I'm running edgy eft 6.10 - the 'ultimate editition 1.2', my kernal is 2.6.11.

When you say restart the x-server, do you mean rebooting my macbook? - if so then i've resrarted many times, i always do after making changes like this. After adding to x-org, i just saved and rebooted.


Thanks for your consideration guys, it's apprieciated!



chrisj303

---

### Post by cyberdork33 on 2007-04-19
Restarting the machine should be fine. you can also restart just x (the gui environment) without restarting the entire machine. 

I found this:
[http://simon.vanderlinden.eu.org/howtos/macbook-emulate-a-synaptics-touchpad-with-ubuntu-gnulinux/](http://simon.vanderlinden.eu.org/howtos/macbook-emulate-a-synaptics-touchpad-with-ubuntu-gnulinux/)

> It seems that a more recent Linux kernel than those present in Edgy Eft repositories (2.6.17) is needed. Either the 2.6.18.x, or a patched version of the present kernel (see [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61223)](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61223))

---

### Post by rhebert on 2007-04-21
Thanks to all the help in this thread, I finally got my 2-finger scrolling working last night.  However, whenever I try to use this feature in Firefox, it skips back to the previous page.  I suppose that two fingers on the trackpad is mapped to middle click somehow.  I thought I could fix this by entering 

Option "TapButton2" 0
Option "TapButton3" 0

to xorg.conf, but no love.  Any ideas what I might be doing wrong?

Much appreciated.

---

### Post by kraeloc on 2007-04-21
I need help. I just installed 7.04 yesterday. I was trying to set up my trackpad, before I knew about qsynaptics/gsynaptics and started by adding Option lines to my synaptics inputdevice section in xorg.conf. I added a few options, rebooted, and my trackpad stopped responding.

Since then, I have removed my added options, installed both gsynaptics and qsynaptics, and rebooted several times. My trackpad still doesn't work.

It's not a total disaster, because my D600 has an eraserhead-style stick. But it's very annoying, and I would like my trackpad back.

This is what my inputdevice entry looks like for my trackpad:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

---

### Post by rhebert on 2007-04-22
Re: my earlier post about Firefox mishandling my two finger scroll:  I found the answer here:
[URL="http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Horizontal_Scroll_Issues_with_Firefox"]
http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Horizontal_Scroll_Issues_with_Firefox[/URL]

---

### Post by Tyrdium on 2007-04-23
> **rhebert said:**
> Re: my earlier post about Firefox mishandling my two finger scroll:  I found the answer here:
[URL="http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Horizontal_Scroll_Issues_with_Firefox"]
http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Horizontal_Scroll_Issues_with_Firefox[/URL]Thanks! That's far better than my quickie solution of disabling horizontal scrolling.

---

### Post by Jiran on 2007-04-23
Hi there,

I have basically the same problem: My laptop uses the touchpad for it's mouse, but I want to enable scrolling on it. The only problem is that when I go to edit my xorg.conf file, there's no synaptics section! My touchpad is a synaptics one, as I've already checked that. Can I just add in a section to the xorg.conf file? If so, what should I add?

Thanks!

---

### Post by rhebert on 2007-04-25
It is unfortunately not quite as simple as just adding a section for the synaptics touchpad; you'll have to change a few other sections too.  Be sure to MAKE A BACKUP of your xorg.conf before you start tinkering around in it - if the changes don't work you may have to boot into recovery mode to fix it, and it'll be easier if you have the backup to revert to.  Use 

sudo cp xorg.conf xorg.conf_backup1 

Then edit your xorg.conf as follows.  You can add a synaptics section that will look something like this:

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"1"
	Option		"SHMConfig"		"true"
	Option		"VertTwoFingerScroll"	"true"
	Option		"HorizTwoFingerScroll"	"true"
	Option		"TapButton1"		"0"
	Option		"TapButton2"		"3"
	Option		"TapButton3"		"2"
EndSection

You'll then want to go to the section marked "ServerLayout" and add the line 

> 	InputDevice	"Synaptics Touchpad"

I don't know whether the next step is necessary, but I also changed the "Configured Mouse" section to the following:

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"

EndSection

Once that's done, try restarting X.  With any luck you should be up and running.  It took a fair bit of noodling to get this working though, and YMMV.

---

### Post by macdaddy3 on 2007-04-28
how do u get to the qsynaptic menu

---

### Post by furbys on 2007-04-29
> **macdaddy3 said:**
> how do u get to the qsynaptic menu

System>Preferences>Touchpad. Well, I assume it's that I can't get it to work for some reason.

When I start gsynaptics I get the error

```
Gsynapics could not initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config yo use Gsynaptics
```

I set the SHMConfig to true in the xorg.conf file. Am I doing something wrong? I'd post the whole file but it's a bit long, actually I will.

```

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
	Option		"Composite"	"0"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mouse0"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"100"
	Option		"RightEdge"	"1100"
	Option		"TopEdge"	"50"
	Option		"BottomEdge"	"300"
	Option		"FingerLow"	"20"
	Option		"FingerHigh"	"30"
	Option		"MaxTapTime"	"150"
	Option		"MaxTapMove"	"90"
	Option		"MaxDoubleTapTime"	"180"
	Option		"VertScrollDelta"	"25"
	Option		"HorizScrollDelta"	"30"
	Option		"VertTwoFingerScroll"	"true"
	Option		"HorizTwoFingerScroll"	"true"
	Option		"FastTaps"	"true"
	Option		"TapButton2"	"3"
	Option		"TapButton3"	"2"
	Option		"MinSpeed"	"0.5"
	Option		"MaxSpeed"	"3.5"
	Option		"AccelFactor"	"0.35"
	Option		"SHMConfig"	"on"
EndSection

```

---

### Post by glickmiller on 2007-05-14
Furbys, you have two Synaptic Touchpad Sections, and the first one does not have SHMConfig line.  It should be set to "true" not "on."

Thanks Rhebert for showing the config.  I finally have my touchpad working right!

---

### Post by canavar on 2007-05-16
Hey guys,

I did whatever you wrote above;

1- add Option "SHMConfig" "true" to /etc/X11/xorg.conf (i also tried "SHMConfig" "on" and restart X, but still doesnt working).
2- add InputDevice    "Synaptics Touchpad"  to Section "ServerLayout"
3- restart X with ctrl+alt+backspace

it still gives me that stupid error:confused:: "Shared memory is not accessible. please add the option 'SHMConfig "on"' into the touch pad  section of /etc/X11/xorg.conf". 

I have no  problem with using touchpad, but i want to "enable" "disable"  it on demand.I use kubuntu 7.04, i try to control synaptics with ksynaptics. Of course every option in ksynaptics is faded, cant change.Here is my xorg.conf:



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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
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
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
 	Option 		"SHMConfig"		"true"
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
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
	Identifier  "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
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
	Option	    "Composite" "0"
EndSection

---

### Post by canavar on 2007-05-17
I think i found the problem; 

securitas@securitas:~$ cat /var/log/Xorg.0.log | grep EE 
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"  

I am sure i have a touchpad :) i've been using it for years. What should i do?

---

### Post by ronocdh on 2007-05-17
> **canavar said:**
> I think i found the problem; 

securitas@securitas:~$ cat /var/log/Xorg.0.log | grep EE 
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"  

I am sure i have a touchpad :) i've been using it for years. What should i do?
In your overview of steps taken in the post above, canavar, I didn't do step 2. I did add SHMConfig and label it true, but that's it.

What does **sudo apt-get install qsynaptics** give you? After it's installed, how about **qsynaptics**?

---

### Post by canavar on 2007-05-17
securitas@securitas:~$ sudo apt-get install qsynaptics
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
qsynaptics is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-input-wacom libglu1-xorg-dev libsqlite0-dev xlibmesa-gl-dev
  libpq-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And

securitas@securitas:~$ qsynaptics
users home is /home/securitas
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
restore old settings...
syndaemon: no process killed
Can't access shared memory area. SHMConfig disabled?
retVal is 0
securitas@securitas:~$    

At first i tried just  first and third option above. But it was still same.Today i tried to add line Load "synaptics" , 
still no result. I checked whether evdev and psmouse modules are loaded, 

securitas@securitas:~$ lsmod | grep evdev
evdev                  11008  5
securitas@securitas:~$ lsmod | grep psmouse
psmouse                38920  0

That is not a big problem but it would be nice if i were able to enable-disable touchpad. Thanks anyway...

---

