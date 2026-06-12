---
title: "A different screen resolution problem ..."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by fuglin on 2007-07-03
From various post it appears I need to add the HorizSync and VertRefresh values for my xorg.conf file as it is not possible to see a full display with the current maximum resolution of 800x600. I have installed Ubuntu on my Fujitsu-Siemens Lifebook E6575, which uses an ATI Rage Mobility M4 device. The problem is, after days of searching online and in the documentation, it has proved impossible to find out what these values are. Does anybody know?  or is there some other answer?

I have found out that the lifebook cannot read DDC information so it is not possible to diagnose the HorizSync and VertRefresh values. It seems also that the information is not to be found online, including on the Fujitsu-Siemen website.

Can I use generic HorizSync and VertRefresh values and if so what should I use?

Any advice would be much appreciated.

---

### Post by bioShark on 2007-07-03
Hi

Instead of writing the Horiz and Vertical values, write the Modeline. Here is a generator for it:

[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

c.u.

---

### Post by fuglin on 2007-07-04
Thanks for your response!

I am though not sure what to do next. I put x: 1025 y: 768 refresh: 85 in the generator (that is what I use in the Windows 2000 I have on a dual boot), and I got the following:

# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

I don't know which part I should add to xorg.conf ?

And, do I just add it after:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"

Greetings from the Faroe Islands
Roy

---

### Post by RedSquirrel on 2007-07-04
Have a look at this guide. It will show you where to put your new Modeline:

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

### Post by blastus on 2007-07-04
Given that the ModeLine you have there is correct for your monitor, you could use it as follows (note you should still know the horizsync and vertrefresh of your display and put them in accordingly)...

```
Section "Device"
    Identifier     "nVidia Corporation NV31 [GeForce FX 5600]"
    Driver         "nv"
    BusID          "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
    Modeline "1024x768_85.00" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV31 [GeForce FX 5600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_85.00"
    EndSubSection
EndSection
```

---

### Post by fuglin on 2007-07-05
Thanks for the information.

As mentioned above though, it seems not possible to find out the HorizSync and VertRefresh values for this Fujitsu-Siemens Lifebook - that is why I was looking for an alternative method. Does that mean it will not be enough to just use the Modeline text?

I am being a bit cautious about making changes as I have very limited experience yet in text only mode, if the need should arise for me to sort out a problem - I'm learning though and will figure it out eventually :)

I would add my xorg.conf file here in case it helped but I don't know yet how to include the code, short of copying and pasting it in?

---

### Post by RedSquirrel on 2007-07-06
> **fuglin said:**
> Thanks for the information.

As mentioned above though, it seems not possible to find out the HorizSync and VertRefresh values for this Fujitsu-Siemens Lifebook - that is why I was looking for an alternative method. Does that mean it will not be enough to just use the Modeline text?

I think you can use the Modeline without those values. It works without them on my system.

The important thing here is that you have generated a Modeline using appropriate input values. You say that you use 1024x768@85Hz in Windows2000, so that should be OK in Ubuntu as well I would think. It would be nice to make sure the HorizontalSync of the Modeline is within the appropriate range, but you could give it a try and see how it looks if you like.


> **fuglin said:**
> I am being a bit cautious about making changes as I have very limited experience yet in text only mode, if the need should arise for me to sort out a problem - I'm learning though and will figure it out eventually :)

Make a backup of /etc/X11/xorg.conf so that you'll have something to fall back on if your changes do not work out.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```If you are more comfortable editing files from a graphical environment than on the command line, then you can edit the xorg.conf file in GNOME and then logout. 

Then press Ctrl-Alt-F2 to go to a console. Login there. Then run:

```
sudo /etc/init.d/gdm restart
```which will take you back to the login screen. See how it looks. If it looks sort of OK, but not perfect try the "Auto Image Adjust" feature if your display has that.

If it looks BAD, then press Ctrl-Alt-F2 to go back to the console. Once there, run this:

```
sudo /etc/init.d/gdm stop
```You can restore your "working" xorg.conf with this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bad
``````
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```You can also recreate xorg.conf with this:

```
sudo dpkg-reconfigure xserver-xorg
```If you want to edit files on the command line, I suggest you use 'nano'

```
sudo nano -wB /etc/X11/xorg.conf
```You can then start gdm (the login screen) with this:

```
sudo /etc/init.d/gdm start
```> **fuglin said:**
> I would add my xorg.conf file here in case it helped but I don't know yet how to include the code, short of copying and pasting it in?

Sure just paste it in. Enclose it in CODE tags please. It's the # symbol on the toolbar when you create your post. You can also put the code tags in manually: [_code_] code in here [_/code_]. Remove the _ characters; I just put them in so that you can see what a code tag looks like. ;)

If you have any questions, just ask. And do let us know how things are going... :)

---

### Post by fuglin on 2007-07-11
Many thanks for all the advice - I have learned a few things in the process.

Unfortunately though I didn't manage to make it work.  I added the ModeLine as advised and ended up with a blank screen that appeared to be frozen. I was obliged to press the off button. I eventually managed to replace the good xorg.conf file but unfortunately, a side effect of whatever I had done was that I had lost my internet connection with its wpa security setup that had previously taken a long time to figure out. From this I learned that it's wise to write down what you try ... With no thanks to me, the connection has now mysteriously reappeared. 

Back to the screen resolution: I had originally saved a bit of text from a post (that I can't find now) with generic HorizSync and VertRefresh settings. I added them to the xorg.conf file and my laptop now (amazingly) starts in 1024x768. I am hoping this won't cause me other problems :)

I have no idea if the xorg.conf file is now as it should be and appreciate your comments (I hope I have included it properly).

Greetings from the Faroe Islands

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
	Option		"XkbLayout"	"fo"
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
	Identifier	"ATI Technologies Inc Rage Mobility M4 AGP"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31.5-55
	VertRefresh	40-70
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M4 AGP"
	Monitor		"Generic Monitor"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by RedSquirrel on 2007-07-14
> **fuglin said:**
>  I have no idea if the xorg.conf file is now as it should be and appreciate your comments (I hope I have included it properly).

It looks OK to me. It would be nice (obviously) to know the real ranges for HorizSync and VertRefresh for that laptop, but the values you have don't look too bad to me.

---

