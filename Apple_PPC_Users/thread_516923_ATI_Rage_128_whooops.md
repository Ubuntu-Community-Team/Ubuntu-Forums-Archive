---
title: "ATI Rage 128 whooops"
date: 2007-08-03
forum: Apple PPC Users
---

### Post by Ripfox on 2007-08-03
In the effort to get some 3d acceleration on my imac with a rage128, I borked my xorg.
I try sudo dpkg-reconfigure xserver-xorg choose ati for a driver...no go. I cannot seem to get my xserver back. Any help? :)

---

### Post by pxwpxw on 2007-08-04
Try fbdev?

---

### Post by tonyr on 2007-08-04
Not enough info here.  Which iMac?  Which ATI Rage128? If you can run **dpkg-reconfigure** you
should be able to run **lspci** to find out the ATI model.  You can also find the model by 
looking in */etc/X11/xorg.conf*. in the Device section for the video card.  Did you do modify
the Module list and/or resolutions during the reconfigure?

- tony

---

### Post by Ripfox on 2007-08-04
fbdev? Yes I chose "ati" as a driver then accepted defaults. It's a blue imac, I think it's whats called a g3 maybe...it's 333 mghz I believe.

---

### Post by FredSambo on 2007-08-04
Just make sure the follwoing values are true in you "Monitor" section of the xorg.conf:

HorizSync 60-60
VertRefresh 43-117

I think those are right, give it a try!

---

### Post by Ripfox on 2007-08-04
I get "no screens found" after I try to reconfigure xorg with the ATI driver...I tried to change the sync/refresh rates as you said but to no avail.

---

### Post by stmiller on 2007-08-04
For that rage card, change the driver to:

r128

The PPC section of  [http://forums.gentoo.org](http://forums.gentoo.org)
has some posts about getting good results with this card if you hunt.

---

### Post by tcrroadie on 2007-08-04
Check and see if there is a file called "xorg.conf.old" in your /etc/X11/ directory.  You can copy this file in place of the xorg.conf file that you are having problems with to get you back to a working xorg.conf file.  

Run this line in the shell. 

```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

Then restart your xserver with this command

```
sudo /etc/init.d/gdm restart 
```

The information that stmiller posted about the correct driver used for your ATI Rage card is also correct.  The "Device" section of your xorg.conf file should look something like this. 

```
Section "Device"
        Identifier      "ATI Rage 128"
        Driver          "r128"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"  "true"
```

For future reference, you do not always need to run "sudo dpkg-reconfigure -phigh xserver-xorg" to edit your xservers configuration file.  Simply editing your /etc/X11/xorg.conf manually with your favorite text editor such as gedit is much faster and will help reduce errors.  

You may also want to see the man page for the r128 driver.  

```
man r128 
```

---

### Post by Ripfox on 2007-08-05
Will the above provide any 3d acceleration?

Identifier: ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS

I went ahead and reinstalled...this is my xorg now:

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
	Identifier	"ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS"
	Driver		"ati"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	60-60
	VertRefresh	75-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS"
	Monitor		"iMac"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
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

---

### Post by stmiller on 2007-08-05
To see if 3D is 100% enabled, type
```

glxinfo

```
in the terminal (while you are booted into the desktop) and look for a line that says:

Direct Rendering: Yes

---

### Post by Ripfox on 2007-08-05
Yep...I use that command. Answer is no on that. :(

---

### Post by FredSambo on 2007-08-06
> Will the above provide any 3d acceleration?

OK so let me get this straight, you have video now, you just want 3D acceleration at this point, correct?

---

### Post by linear on 2007-08-06
You can try the suggestions in [this post]("http://ubuntuforums.org/showpost.php?p=2321892&postcount=8"); they may help.

---

### Post by Ripfox on 2007-08-06
> **FredSambo said:**
> OK so let me get this straight, you have video now, you just want 3D acceleration at this point, correct?

Righto.

---

