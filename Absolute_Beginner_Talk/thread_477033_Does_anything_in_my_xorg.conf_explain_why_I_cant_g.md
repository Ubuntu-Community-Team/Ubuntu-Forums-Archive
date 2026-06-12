---
title: "Does anything in my xorg.conf explain why I cant get Beryl working?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-17
I have attached my xorg.conf file to see if any one can take a look and see if anything looks like it could cause a problem with me not being able to use Beryl.  I know it's eye candy but I would really like to see it.  Please let me know any other useful info to post that would be helpful in providing me with assistance. First please take a look at the results of comment fglxrinfo.

Thanks in advance,
VC

don@don-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6473 (8.37.6)



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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-96
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
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
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by Clay_Banger on 2007-06-17
when you run beryl what happens? is there any error messages that appear?

---

### Post by videocheez on 2007-06-17
> **Clay_Banger said:**
> when you run beryl what happens? is there any error messages that appear?

No.  There are no error messages.  My problem is that I can't see any of the cool stuff or figure out how to do any of the cool stuff that is suppose to be  available i.e.  wobly windows, cube desktop, etc.

I do see the following error however when I click system > desktop effects>
**The Composite extension is not available**  
Also, when I right click on the diamond and then click select window manager I can only select Compiz or Metacity, if I click on Beryl, the screen does something slightly funnny and defaults back to either Compiz or Metacity.


Thx for responding,

VC

---

### Post by RelativelyQuantum on 2007-06-17
I'm having a similar problem. I couldn't run Beryl in Feisty, and now it's not even available in Edgy without modification, which doesn't seem to be working.

My suggestion would be to check the following file:
```

gksu gedit /etc/apt/sources.list
```

Run this command in terminal, and then add this line to the file:

```
# deb http://ubuntu.beryl-project.org/ edgy main
```

I got this advice after posting a thread about my Beryl problems, so it's worth a try. Don't mind the url; the page is a bit weird :)

---

### Post by Clay_Banger on 2007-06-17
> **RelativelyQuantum said:**
> ```
# deb http://ubuntu.beryl-project.org/ edgy main
```
shouldnt it be:
```
deb http://ubuntu.beryl-project.org/ edgy main
```
because putting the "#" in front comments it out? and im presuming you want to use it

---

### Post by videocheez on 2007-06-17
> **RelativelyQuantum said:**
> I'm having a similar problem. I couldn't run Beryl in Feisty, and now it's not even available in Edgy without modification, which doesn't seem to be working.

My suggestion would be to check the following file:
```

gksu gedit /etc/apt/sources.list
```

Run this command in terminal, and then add this line to the file:

```
# deb http://ubuntu.beryl-project.org/ edgy main
```

I got this advice after posting a thread about my Beryl problems, so it's worth a try. Don't mind the url; the page is a bit weird :)


Okay.  I followed you advice but I must ask why am i doing this.

---

### Post by Crafty Kisses on 2007-06-18
> **videocheez said:**
> I have attached my xorg.conf file to see if any one can take a look and see if anything looks like it could cause a problem with me not being able to use Beryl.  I know it's eye candy but I would really like to see it.  Please let me know any other useful info to post that would be helpful in providing me with assistance. First please take a look at the results of comment fglxrinfo.

Thanks in advance,
VC

don@don-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6473 (8.37.6)



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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-96
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1440"	"1920x1200"	"1856x1392"	"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
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
Section "Extensions"
	Option		"Composite"	"0"
EndSection

You can try reconfiguring your X server.

---

### Post by machoo02 on 2007-06-18
Are you using the Xgl xserver instead of the regular Xserver?

---

### Post by videocheez on 2007-06-18
> **Codename said:**
> You can try reconfiguring your X server.

How do I do that? Do you have any suggestions?

[QUOTE=machoo02] Are you using the Xgl xserver instead of the regular Xserver?.[/QUOTE]
How can I tell?

VC

---

### Post by Clay_Banger on 2007-06-18
> **videocheez said:**
> How do I do that? Do you have any suggestions?
type in the terminal this, to reconfigure the xserver:
```
dpkg-reconfigure xserver-xorg
```

---

### Post by swisscow on 2007-06-18
The problem is the fglrx drivers - they don't work with composite in a straightforward way - you can thank ATI for that. You do have choices though. You can replace the fglrx with the radeon drivers and the install Beryl and run it through AIGLX , that seems to work for a lot of people, or alternatively run Beryl through XGL. I've done it both ways with success (I have the ATI X300 card) but had problems with running Google Earth afterwards - which I use  a lot.

Anyway a search for BeryL +ATI +XGL or Beryl + ATI + AIGLX will bring up a number of how to's - just take care to now which one you are following so you can backtrack if it all goes *rs* end up!

Good luck

---

### Post by RelativelyQuantum on 2007-06-18
> **videocheez said:**
> Okay.  I followed you advice but I must ask why am i doing this.

I heard that that was something to do to allow your system to use Beryl :)

I'm no expert in it, but, like I said, just something to try.

---

### Post by RelativelyQuantum on 2007-06-18
> **Clay_Banger said:**
> shouldnt it be:
```
deb http://ubuntu.beryl-project.org/ edgy main
```
because putting the "#" in front comments it out? and im presuming you want to use it

Thanks; I didn't know that :)

---

### Post by videocheez on 2007-06-18
this is good info and gives me some direction for this evening.  I have a couple questions.

[LIST=1]
[*]How do I back up my xorg.conf file?
[*]Where do i look in my xorg.conf to see if AIGLX is already installed?
[*]What are some other safety measures that I should do to make restoration easy in case I mess up something?
[*]Should I uninstall Beryl before making changes?
[/LIST]

Thanks in advance,

VC

---

### Post by Clay_Banger on 2007-06-18
> **videocheez said:**
> this is good info and gives me some direction for this evening.  I have a couple questions.

[LIST=1]
[*]How do I back up my xorg.conf file?
[*]Where do i look in my xorg.conf to see if AIGLX is already installed?
[*]What are some other safety measures that I should do to make restoration easy in case I mess up something?
[*]Should I uninstall Beryl before making changes?
[/LIST]

Thanks in advance,

VC

1.  backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

to restore your xorg.conf:
at the terminal do
```
sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
And restart your computer

---

### Post by videocheez on 2007-06-21
Just want to let you guys know that Beryl is now working pretty well and thanks for all of your help.  I actually followed the guide in the following URL:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

VC

---

