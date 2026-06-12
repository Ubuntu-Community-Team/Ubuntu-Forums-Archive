---
title: "I messed up xorg.conf"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Taters on 2007-11-17
Well... I was trying to edit xorg.conf to work with Beryl (I was following a tutorial.) It told me to restart, so I did. I was greeted with a text based greeting, followed quickly with a blue screen of confusion that talking about X windows or something. 

I'm running off of a live cd right now, here is the edited version of xorg.conf file:
[QUOTE=xorg.conf]
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
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
**	Load		"dbe"**
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
[B]
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection
[/B]
[B]Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection[/B]

[B]Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection[/B]

Section "Device"
	[B]Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPMode"	"4"
	Option		"AGPFastWrite"	"true"
	Option		"DisableGLXRootClipping"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"EnablePageFlip"	"true"[/B]
EndSection

Section "Monitor"
	Identifier	"HP v75"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200]"
	Monitor		"HP v75"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	**Option		"AIGLX"	"true"**
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

[B]Section "Extensions"
	Option		"Composite"	"Enable"
	Option		"Composite"	"0"
EndSection[/B]
[/QUOTE]

The bolded stuff is the stuff that was edited. I have a command line going on in my freshly broken 7.04 release, so is it possible to edit the file back? Or can I edit it from the live CD?

Please help.

---

### Post by SOULRiDER on 2007-11-17
First off, Beryl is ancient (well not really, but it merged with compiz some time ago)!

Reboot and go into recovery mode, then reconfigure your xorg.
```
sudo dpkg-reconfigure xserver-xorg
```

Once your system is back up you can install compiz fusion by using this guide:
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by jken146 on 2007-11-17
You can edit it from the live CD.  It is at /etc/X11/xorg.conf but you will probably want to make a backup first!  If you can boot into recovery mode you might want to try
```
dpkg-reconfigure xserver-xorg
```
and answer the questions to get your X configuration back to normal.

---

### Post by defrex on 2007-11-17
You can edit from the live cd. The drive should have auto-mounted, so just look for the one with all the ubuntu files on it. You'll find your xorg.conf in /media/sda1/etc/X11/ where sda1 is the name your drive is mounted under.

If you still have problems after restoring it to the way it was before, try booting up your system and going to the command line. Run *sudo dpkg-reconfigure xserver-xorg*. that will do a general reconfigure of your xorg.conf, bringing it back to a usable state.

Also, Beryl is out of date. You want to use Conpiz Fusion.

---

### Post by Taters on 2007-11-17
Okay... I entered in that in, and it created a copy of the bad file, I have a good copy, but I have no means of putting it in. The live cd won't let me save/edit system files on the hard disk.
oh, and thank you for the tutorial link.

---

### Post by taurus on 2007-11-17
You can write to your harddrive if you use sudo/gksudo before the command.  Assuming you mounted your harddrive, /dev/sda1, to /mnt/ubuntu, and the good copy of xorg.conf is called xorg.conf.bak, you would do

```
sudo cp /mnt/ubuntu/etc/X11/xorg.conf.bak /mnt/ubuntu/etc/X11/xorg.conf
```

---

### Post by Taters on 2007-11-17
Would this work:
```
sudo cp /media/disk/etc/X11/xorg.conf.bak /media/disk/etc/X11/xorg.conf
```

---

### Post by mali2297 on 2007-11-17
What guide did you use when editing xorg.conf? I have used this tutorial successfully:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Although this was some time ago, I managed to get Beryl working nicely with my ATI X700 card.

You should have the *radeon* driver instead of *fglrx* if you want to use AIGLX. Which graphics card do you have?

Also, this says first that composite should be enabled, then that it shouldn't.
```

Section "Extensions"
Option "Composite" "Enable"
Option "Composite" "0"
EndSection

```
Comment out one of the lines.

---

### Post by Taters on 2007-11-17
> **mali2297 said:**
> What guide did you use when editing xorg.conf? I have used this tutorial successfully:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Although this was some time ago, I managed to get Beryl working nicely with my ATI X700 card.

You should have the *radeon* driver instead of *fglrx* if you want to use AIGLX. Which graphics card do you have?

Also, this says first that composite should be enabled, then that it shouldn't.
```

Section "Extensions"
Option "Composite" "Enable"
Option "Composite" "0"
EndSection

```
Comment out one of the lines.

That was the tutorial I was following. I have an ATI Radeon Xpress 200 card.

---

### Post by taurus on 2007-11-17
> **Taters said:**
> Would this work:
```
sudo cp /media/disk/etc/X11/**xorg.conf.bak** /media/disk/etc/X11/xorg.conf
```

If your original config file is called xorg.conf.bak.  Otherwise, you can check on the date from the output of this command.

```
ls -la /media/disk/etc/X11
```

---

### Post by Taters on 2007-11-17
> **taurus said:**
> If your original config file is called xorg.conf.bak.  Otherwise, you can check on the date from the output of this command.

```
ls -la /media/disk/etc/X11
```

Thank you. I think that did it. I'll check now.

---

### Post by mali2297 on 2007-11-17
> **Taters said:**
> That was the tutorial I was following. I have an ATI Radeon Xpress 200 card.

This one?
> 
2D Acceleration Only
    * Xpress 200M Northbridge integrated GPUs

In that case, I think you should check out the link that Soulrider gave you and try XGL instead of AIGLX.

---

### Post by Taters on 2007-11-17
Well, one, thank you Taurus, it worked, nothing is missing.

And two, there is a difference between the Radeon 200 and the 200m, I just haven't found out what it is yet. But I'll try out compiz-fusion now. Hurray for getting cut by the bleeding edge!

---

