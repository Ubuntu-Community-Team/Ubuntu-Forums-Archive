---
title: "fglrx ATI driver problem"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Talic on 2007-04-02
Hi, I just installed the fglrx driver for my radeon X1900XTX by using this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Post-Installation_Checks](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Post-Installation_Checks) and every time I try to verify it I keep getting the Mesa project as my OpenGL vendor. I did try the trouble shooting commands but I just get this 

$ mkdir -p /usr/X11R6/lib/modules/dri 
$ ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
ln: creating symbolic link `/usr/X11R6/lib/modules/dri/fglrx_dri.so' to `/usr/lib/dri/fglrx_dri.so': File exists

After that I would run fglrxinfo again and still get Mesa again :( 

I think I installed it right otherwise, my resolution and refresh rate was set after I installed it.

---

### Post by dstew on 2007-04-02
Did you install the driver using the Ubuntu way (Method 1) or manually?

---

### Post by Majorix on 2007-04-02
Donno about you but I had installed it the manual way on 6.06 and got no problems.

---

### Post by ambien on 2007-04-02
I have had a lot of problems with my Radeon X1300 card so far...at first when I configured it like that link said, my display was almost unusable, so i deleted the composite line from my /etc/X11/... and everything works OK, but no hardware acceleration, and I get the mesa driver...I found a page that describes this problem exactly, but the instructions to fix are beyond my (non-existent) expertise, if anyone can do this, please say!

 Graphical Anomalies

This was experienced with an ATI Radeon X1600 Pro 512mb:

After following instructions for both Method 1 and Method 2, whenever the Composite Extension is disabled, the display would be almost unusable, but the fglrxinfo command would display the correct information. If the Composite Extension is re-enabled the display would be usable, but fglrxinfo would report using mesa drivers.

To resolve the problem it maybe needed to lower the AGP Aperture setting in my BIOS to 128mb (or lower worked too). The AGP Aperture was initially set to 256mb. After setting the AGP Aperture to 128mb, everything worked perfectly; the Composite Extension is disabled, fglrxinfo reports the correct drivers, and direct rendering is enabled. Some systems may require setting the AGP Aperture to the highest setting (256mb or 512mb).
[edit] References

---

### Post by dstew on 2007-04-02
This is referring to changing a setting in your computer's BIOS (basic input/output system) to help your AGP hardware to work better.

The system BIOS is the software that is stored in a read-only memory that stays intact even when the computer is turned off. When you turn on your computer, the first thing it does, before it loads the operating system from the hard disk, is to run the BIOS code to set up its hardware. The BIOS also does some system testing to make sure everything is OK before it tries to load the operating system from the disk.

You can access the Setup screens for your BIOS by pressing a certain key when the computer first starts up. It is usually one of the function keys, like F2 or F12, or sometimes the Delete key. The very first splash screen you see when you start your computer will often tell you which key to use. If it disappears before you get to use it, just restart the computer and be ready to press the key as soon as you see the splash screen.

Once you have entered your BIOS setup screen, the different settings are usually explained pretty well for you. You might need to look for a while to find the AGP settings, but they should be in there somewhere. When you are in your BIOS setup, do not change a lot of things, just the one thing you think you need to change. When you exit BIOS, it usually asks you if you want to save your changes. Tell it yes, and exit. It should reboot.

---

### Post by ambien on 2007-04-02
lol THAT BIOS!!! I feel stupid, thought it would be different for LInux...OK going to try this out, if it works I will repost very shortly...if not, it is because I am troubleshooting a bad display lol!

***UPDATE***
f2 took me to BIOS, but only had options to set video to AGP or PCI, nothing about size!!!

---

### Post by Talic on 2007-04-03
Yeah I installed it the Ubuntu way and I'm running 6.10 x64 version.

It seems like Ubuntu is really picky about my X1900XTX, before I installed this driver it was a pain to get the desktop loaded onto my screen. I had to ctrl+alt F1 then ctrl+alt F7 to get it to work.

But it works fine now except for the fglrx showing up as mesa.

---

### Post by BOBSONATOR on 2007-04-03
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Always works for me in edgy, you should try.

---

### Post by freebird54 on 2007-04-03
Here are a couple of things that might help.  I am running a Radeon 9550, w/Beryl worling etc... anyway.

The sym link you apparently tried before wasn't enough for me either - probably because of the order in which I tried things :)  So we are going to get the old ati-agp out of the load sequence, by blacklisting it.  Open a Terminal, and

```
sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.backup
gksudo gedit /etc/modprobe.d/blacklist

```
and paste or enter the following into the file

```
# causes fglrx to fail and mesa drivers to load
blacklist ati-agp
```

Save, exit, reboot.  Then see if your /etc/X11/xorg.conf matches the bolded items in the following extracts..

```
[B]Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection
[/B]

```

and

```
Section "Device"
        Identifier  "ATI Radeon 9550"
[B]        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"[/B]
        BusID       "PCI:1:0:0"
EndSection
```

and

```
[B]Section "Extensions"
        Option      "Composite" "Disable"
EndSection
[/B]
```

Got it all?  Should work - does for me anyway - and I'm still a n00b too :D

---

### Post by Talic on 2007-04-03
I don't think I have the fglrx module enabled after doing 

gksudo gedit /etc/default/linux-restricted-modules-common

it says its disabled.

# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""

I think its stopping me from installing the binary driver.

---

### Post by ambien on 2007-04-03
I tried freebird's fix, as soon as I enter the "composite" "disable" lines I get the correct information when I type fglrxinfo, however, all hell breaks loose on my desktop. Here is my /etc/usr/X11/xorg.conf file. PLEASE HELP!

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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
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
	Identifier   "FPD1730"
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
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "FPD1730"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
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

Section "ServerFlags"
    Option     "AIGLX" "off"
EndSection

#Section "Extensions"
Option    "Composite" "Enable"
EndSection

```

```
fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

---

### Post by ambien on 2007-04-03
No luck. still the same old crap. Starting to think this problem can't be fixed

---

### Post by freebird54 on 2007-04-03
I am not sure of your definition of 'all hell breaks loose' but on the suspicion that it might be inappropriate resolution/refresh settings - here is one way to reset that.  Use <ctrl><alt><F1> to open an alternative console, and login as usual.  (<ctrl><alt><F7> will bring you back when done)

```
sudo dpkg-reconfigure xserver-xorg
```

Which will put you into a text mode interface to resetting your x server options (essentilly rebuilding your xorg.conf file). Most of what you see will be OK to leave either empty, or as default - except the bits about the monitor and resolution settings. By the way - <tab> key to move around between items, <arrow> keys to move within an item,  <space> to 'mark' or select items (such as resolution values) and <enter> to choose OK or confirm a choice.

When you get to the monitor setting, try to autodetect the monitor. Give it a name when asked. Choose 'MEDIUM' for setting it up. Choose the 'BEST' safe resolution that you know of (perhaps 1280x1024 @ 60 Hz refresh??). When you have the list of possible resolutions, use the space bar to toggle the 'mark' beside it as you wish - BEING SURE NOT TO MARK ANY UNSAFE (too high) RESOLUTIONS!

When you are done - WRITE DOWN the name it saved the backup under - in case you made things worse (unlikely).  You will still need to add in the 'bolded' lines from before - this command rewrites the whole thing.  When the 'FBDev' lines etc have been added, use <ctrl><alt><backspace> to restart the X server.

Hopefully 'hell' will remain in abeyance.

---

### Post by jasfat on 2007-04-04
i'm having same problem with mine x1600 no drivers work have tried every guide i can find and everyone f.... up my desktop. log inn screen no show, ctrl-alt f1/f7 no go.
when i try to reconfigure x the screen goes black :S

---

### Post by freebird54 on 2007-04-04
OK - jasfat.   Same thing - need more input!  What card - what driver did you try - what does xorg.cong look like - and what specs does your monitor like to have (Horizontal Sync /vertical Refresh / resolution)

With that - we can give it a try :)

---

### Post by jasfat on 2007-04-04
last i tried this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

the card is a ATI X1600PRO 
screen is a fujitsu-siemens s19-1 with 1024*1024
tried the troubleshooting and everything.
my xorg.conf looks just like ambien's output

jasfat

---

### Post by freebird54 on 2007-04-04
Try putting the bolded items (from an earlier post) in the 'Device' section - INLCUDING the FBDev one.  If all the fixes aren't in this thread- they are in
[http://ubuntuforums.org/showthread.php?t=400964](http://ubuntuforums.org/showthread.php?t=400964)

Try it out - and report what the 'tests' result in on your system.

We'll try from there - if needed :)

---

### Post by jasfat on 2007-04-04
nope didn't help :-(

started in recovery mode and got 
Error: unable to open display :0

---

### Post by freebird54 on 2007-04-04
Which version of the fglrx driver did you install?  I am losing track of all the threads I've been doing :)

If the power of your card matches the rest of the hardware - maybe you need the newest driver?  If so - you'll have to either track down a thread showing 'by hand' install from the ATI site - or wait till I get back up again, I'm afraid.....

Can't think enough right now!

---

### Post by jasfat on 2007-04-04
tnx for your help :D
but i did the easy way.... called a buddy and exchange my ati card for a nvidia 

problem solved for me :grin: 

now everything runs smooth and delicious


jasfat

---

### Post by ambien on 2007-04-05
tried all the suggestions, still no luck! my X1300 just doesnt play well with linux, and my motherboard is stone-age so I can't try the AGP suggestion. No hardware acceleration for me :( I heard feisty fawn will have better support though, so I am hopeful

---

### Post by freebird54 on 2007-04-05
My motherboard is pretty old too - like 1999 I think.  However, flashing a BIOS update helped considerably! (brought it up to 2004 I think - and gave me support for drives over 137 Gb).  Have you investigated that avenue for change?

---

### Post by wyth on 2007-04-05
Rather than posting my own similar problems/questions, I'm gonna tag along here.

I have an ATI Radeon R250 (FireGL 9000), running Feisty, and have tried installing the xorg-driver-fglrx the Ubuntu way and manually installing by making deb packages (all described [here]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")).

Every time I try with fglrx, I end up with no X Windows and a warning that no screens can be found.  The regular ATI drivers with Feisty work a lot better than in the past, but there's still some degradation; when I do anything a little graphics/memory intensive, it looks like my screen is growing hair.  (But it was fun playing with the desktop effects.)

So -- will there be any updates to fglrx to make it work as seamlessly as in Dapper and Edgy?  Will the ATI driver one day be as snappy as the fglrx driver?  (Shuttleworth seems to think not.)  Are there any secret tweaks to get this stuff going?  I can live without the desktop effects for now; I just want a decent screen.

---

### Post by rac9876 on 2008-06-09
> **dstew said:**
> This is referring to changing a setting in your computer's BIOS (basic input/output system) to help your AGP hardware to work better.

The system BIOS is the software that is stored in a read-only memory that stays intact even when the computer is turned off. When you turn on your computer, the first thing it does, before it loads the operating system from the hard disk, is to run the BIOS code to set up its hardware. The BIOS also does some system testing to make sure everything is OK before it tries to load the operating system from the disk.

You can access the Setup screens for your BIOS by pressing a certain key when the computer first starts up. It is usually one of the function keys, like F2 or F12, or sometimes the Delete key. The very first splash screen you see when you start your computer will often tell you which key to use. If it disappears before you get to use it, just restart the computer and be ready to press the key as soon as you see the splash screen.

Once you have entered your BIOS setup screen, the different settings are usually explained pretty well for you. You might need to look for a while to find the AGP settings, but they should be in there somewhere. When you are in your BIOS setup, do not change a lot of things, just the one thing you think you need to change. When you exit BIOS, it usually asks you if you want to save your changes. Tell it yes, and exit. It should reboot.
I also found that reducing the AGP aperture size from 256MB to 128MB fixed the Mesa rendering issue with an ATI Radeon 9550-based AGP card on an Asus P4P800 Deluxe motherboard, running Xubuntu 8.04 (Hardy Heron). With the larger aperture size fglrxinfo had always shown Mesa rendering; with the smaller size it shows ATI for both OpenGL vendor and OpenGL renderer. 3D graphics speed has improved tremendously. 

There was still some system instability (random hangs, windows vanishing while in use) which seems to have been improved by updating the BIOS to version 1019. It's worth checking you have the latest stable BIOS for your board.

---

