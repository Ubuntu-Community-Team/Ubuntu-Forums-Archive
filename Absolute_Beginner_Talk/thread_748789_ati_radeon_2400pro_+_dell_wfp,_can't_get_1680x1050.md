---
title: "ati radeon 2400pro + dell wfp, can't get 1680x1050 resolution"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by byrmark on 2008-04-07
OK, I'm new, but I tried to read a bit before posting.  I want the 1680x1050 resolution that I get under windows xp (I have a dual boot).  However, when I try to adjust it I only have the option of 1280x1024 or lower resolution.  I tried the following

1.)  I tried to rerun the autodetect script.

2.)  I looked to see if there were undetected monitor specs

3.)  Also, I tried the following 

cvt -v 1680 1050 60.0Hz

# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

This has the value I want 1680x1050, but???

4.)  I also looked at the output from

less /var/log/Xorg.0.log

Don't know what I'm looking at here, but nothing really stood out as funny.

So I thought maybe I would download the driver from 
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

however, under both the linux86 and linux86_64 link, I get the same download.  Is that weird?  Should they have two links for the same thing?  They both work the same?  Should I try it?  Is there some other solution I should try?

---

### Post by overdrank on 2008-04-07
> **byrmark said:**
> OK, I'm new, but I tried to read a bit before posting.  I want the 1680x1050 resolution that I get under windows xp (I have a dual boot).  However, when I try to adjust it I only have the option of 1280x1024 or lower resolution.  I tried the following

1.)  I tried to rerun the autodetect script.

2.)  I looked to see if there were undetected monitor specs

3.)  Also, I tried the following 

cvt -v 1680 1050 60.0Hz

# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

This has the value I want 1680x1050, but???

4.)  I also looked at the output from

less /var/log/Xorg.0.log

Don't know what I'm looking at here, but nothing really stood out as funny.

So I thought maybe I would download the driver from 
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

however, under both the linux86 and linux86_64 link, I get the same download.  Is that weird?  Should they have two links for the same thing?  They both work the same?  Should I try it?  Is there some other solution I should try?

Hi and you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by byrmark on 2008-04-07
Thanks, but ...

I tried envy too.  It had no different effect.  

I also tried xrandr which a friend recommended.  It did not give 1680x1050 as an option for a change.

My friend said it must be a detection problem.  But I don't know what to do about that.

---

### Post by byrmark on 2008-04-08
Just an update.   I found the following page which seems to indicate that the problem has not yet been resolved.  

[http://wiki.cchtml.com/index.php/Troubleshooting#No_high-resolution_video_modes_available](http://wiki.cchtml.com/index.php/Troubleshooting#No_high-resolution_video_modes_available)

Just in case anyone else has had the same problem.

This actually surprises me since this card has been out for a while.  I am open to other suggestions like buying a new card and plugging it in so that I can get the desired resolution.  Anyone know of a good card that would work?

---

### Post by stchman on 2008-04-08
> **byrmark said:**
> OK, I'm new, but I tried to read a bit before posting.  I want the 1680x1050 resolution that I get under windows xp (I have a dual boot).  However, when I try to adjust it I only have the option of 1280x1024 or lower resolution.  I tried the following

1.)  I tried to rerun the autodetect script.

2.)  I looked to see if there were undetected monitor specs

3.)  Also, I tried the following 

cvt -v 1680 1050 60.0Hz

# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

This has the value I want 1680x1050, but???

4.)  I also looked at the output from

less /var/log/Xorg.0.log

Don't know what I'm looking at here, but nothing really stood out as funny.

So I thought maybe I would download the driver from 
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

however, under both the linux86 and linux86_64 link, I get the same download.  Is that weird?  Should they have two links for the same thing?  They both work the same?  Should I try it?  Is there some other solution I should try?

Use Envy to install the prorietary ATI driver for your video card.  When you install Envy have it remove the previously installed ATI driver.  This may result in your PC booting into a CLI mode.  No fear.  You can run Envy from the command line via

```
sudo envy -t
```

After that select install the ATI driver.

Let Envy modify your xorg.conf and reboot the PC.  If your resolution still is not the desired then put

"1680x1050" as the first resolution in the line of resolutions in your xorg.conf, don't forget the quotation marks.  Reboot the workspace via CTRL-ALT-BKSP.  This should do what you want.

---

### Post by byrmark on 2008-04-08
I tried the envy suggestion.

It seems that the uninstall completely removed my xorg.conf file.  I replaced it with the old one and tried to install the ATI driver using envy.  The following is in my conf file:



Section "Monitor"
	Identifier	"DELL 2208WFP"
	Option		"DPMS"
	Horizsync	30-83
	Vertrefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"DELL 2208WFP"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

This all looks OK to me??  However, I still only have the 1280x1024 option as the highest resolution in the system preferences and also the administration screens and graphics.  

Did I do something boneheaded???

---

### Post by twist2b on 2008-04-08
easiest way...... goto into recovery mode from GRUB
type these:
apt-get install nvidia-glx-new
envy should have already gotten all the goods...... but just incase
NOW VERY IMPORTANT
type:
"dpkg-reconfigure xserver-xorg"
without quotes
go through the steps make sure in the beggining you choose "nvidia"
close to the end it gives you resolution choices
there will be lots but press space of the one you want and some close ones.
then press enter
finnish up
it works perfect 100% guarantee
ENJOY!


edit -- I'm sorry your using AMD, i read wrong
SO
dont select nvidia select AMD
also I think it might be
apt-get install AMD
or something, you need to check that

---

### Post by stchman on 2008-04-08
> **twist2b said:**
> easiest way...... goto into recovery mode from GRUB
type these:
sudo apt-get install nvidia-glx-new
envy should have already gotten all the goods...... but just incase
NOW VERY IMPORTANT
type:
"dpkg-reconfigure xserver-xorg"
without quotes
go through the steps make sure in the beggining you choose "nvidia"
close to the end it gives you resolution choices
there will be lots but press space of the one you want and some close ones.
then press enter
finnish up
it works perfect 100% guarantee
ENJOY!

He has an ATI card not an Nvidia card.

---

### Post by stchman on 2008-04-08
> **byrmark said:**
> I tried the envy suggestion.

It seems that the uninstall completely removed my xorg.conf file.  I replaced it with the old one and tried to install the ATI driver using envy.  The following is in my conf file:



Section "Monitor"
	Identifier	"DELL 2208WFP"
	Option		"DPMS"
	Horizsync	30-83
	Vertrefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"DELL 2208WFP"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

This all looks OK to me??  However, I still only have the 1280x1024 option as the highest resolution in the system preferences and also the administration screens and graphics.  

Did I do something boneheaded???

There are usually a list of Defaultdepth modes as well.

What driver is listed for the ATI card in your xorg.conf?  It should be fglrx.  If it is ati change it to fglrx.  Did you let Envy modify the xorg.conf for you?

---

### Post by byrmark on 2008-04-08
PS I tried to use your manual instructions STCHMAN.  Unfortunately, there is one line which I am not sure how to modify appropriately

bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy

I'm using 7.10.  I tried gutsy where edgy is, but got the following

Creating directory fglrx-install
Verifying archive integrity...Error in MD5 checksums: c9edda16710ccacd332d20c0b3424717 is different from 095ee06415d8206d9118db8160b78f66

This is also in the script.  I am fairly sure it is my ignorance that keeps me from recognizing the proper modification.

---

### Post by byrmark on 2008-04-08
Here is my whole xorg.conf

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"vesa"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2208WFP"
	Option		"DPMS"
	Horizsync	30-83
	Vertrefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"DELL 2208WFP"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
EndSection

I seems it is not using the right one.  I did try to let envy modify my xorg.conf.  However, since it had been completely removed by the uninstall that I ran, there was none.  I then installed the old one and ran install (ati).  I then just rebooted the machine.  This is what I ended up with (above).

---

### Post by byrmark on 2008-04-08
Problem solved (finally)

Thank you  STCHMAN

THANK YOU!

I added the following lines by hand to the xorg.conf file and the reran envy.  

Section "Extensions"

    Option  "Composite" "Disable"

EndSection

This time envy worked for me.  

THANKS AGAIN!

---

### Post by stchman on 2008-04-08
> **byrmark said:**
> PS I tried to use your manual instructions STCHMAN.  Unfortunately, there is one line which I am not sure how to modify appropriately

bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy

I'm using 7.10.  I tried gutsy where edgy is, but got the following

Creating directory fglrx-install
Verifying archive integrity...Error in MD5 checksums: c9edda16710ccacd332d20c0b3424717 is different from 095ee06415d8206d9118db8160b78f66

This is also in the script.  I am fairly sure it is my ignorance that keeps me from recognizing the proper modification.

That procedure is made for Edgy only.  I state that in the section.  I need to remove that as I recommend Envy or the Restricted Driver Manager for ATI or Nvidia driver installation.

---

### Post by stchman on 2008-04-08
> **byrmark said:**
> Problem solved (finally)

Thank you  STCHMAN

THANK YOU!

I added the following lines by hand to the xorg.conf file and the reran envy.  

Section "Extensions"

    Option  "Composite" "Disable"

EndSection

This time envy worked for me.  

THANKS AGAIN!

Glad I could be of help.  Also change your driver from

"vesa"

to 

"fglrx"

This will give you 3D acceleration.  The vesa driver is too basic.

---

### Post by edalquist on 2008-07-23
I'm having a problem with the same config. I have a ATI Radeon HT 2400 XT and a Dell 2208WFP.

With the default 8.04 amd64 install I get a blank screen after boot. ctrl+alt+F1 gets me a functional CLI though.

I tried using envyng to install the ATI driver. This gets me the start of a GUI but as when GDM starts to draw its UI the machine hard freezes (no screen switching, no ssh, no ping) and I have to reboot.

I don't quite follow what was done from the above threads, should I try doing a manual install of the ATI driver? Or is there a complete xorg.conf that could be posted along with a note about what driver is being used?

Thank you,
-Eric

---

### Post by soxs on 2008-07-23
To change your display resolution instantly use:
```
sudo xrandr -s 1680x1050
``` (Don't use messy gtk tools, they suck)

---

### Post by edalquist on 2008-07-23
That xrandr requires it is run from the same session that has the display open. I can't actually interact with that display since it is blank. I can only log in via ssh or via switching to a different display via ctrl+alt+F1

---

### Post by soxs on 2008-07-23
I am currently doing a script which will give the community back what I learned about installing the fglrx driver. It will take some more time to make sure it won't kill your system, so you'll have to wait till at least tmorrow. PM if interested...

You may have a look at **[COLOR="Orange"]_[B][COLOR="YellowGreen"](method 2)[/COLOR]**_[/COLOR][/B]:
[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

---

### Post by edalquist on 2008-07-23
Thanks for the link. I did a clean install (had rather mucked things up with many different attempts to get a driver working) and then followed the instructions here:

[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

My xorg.conf is:
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbVariant" "intl"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

This is for a ATI Radeon HD 2400 XT running through a single Dell 2208WFP display (22" wide screen flat panel).

Thanks for the help!

---

### Post by soxs on 2008-07-24
Did the method the howto suggested work? (I guess so^^)

---

