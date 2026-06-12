---
title: "Screen resulution?!?"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by Slinker on 2005-07-03
ok. i have installed ubuntu. Everything works fine. Now the problem: The only options i have for screen resulution is 640*400, 800*600 and 1024*768 in 60hz !?!?! Both my screen and graphic card can handel a loot mor then this. Whats upp with this? =) 

The harware acceleration works fine on my ATI radeon 9800XT in Ubuntu...

Mayby ther is a better way to change resulutions in Ubuntu than system>preferences>screen resulution ?

And yes im a total noob on this Linux thing..

---

### Post by Error_Msg on 2005-07-03
Open a terminal and type dpkg-reconfigure xserver-xorg and work your way through it.

E_M

---

### Post by daniel2501 on 2005-07-03
You probably just need to edit your xorg.conf file.
You can do it at the command line:

```
sudo nano /etc/X11/xorg.conf
``` 

Or you can use a graphical text editor as root to edit the file:

```
sudo gedit
```

Under the "Screen" section you have a number of "Display" subsections. One for each color depth. Each with all the supported screen resolutions:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "v70s"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x4$
        EndSubSection


```

Just add your desired res. to the list.
**Be sure you back up your original xorg.conf file first!** 
You can restore it by booting into recovery mode and removing the edited
xorg.conf, and renaming the old one xorg.conf
```

cd /etc/X11
sudo rm xorg.conf
sudo cp xorg.conf.backup xorg.conf

```
Hope this helps!

---

### Post by frodon on 2005-07-03
ok, all the parameters for screen resolution are located in xorg.conf, so post here your xorg.conf file and we will help you : ```
gedit /etc/X11/xorg.conf
```

---

### Post by aysiu on 2005-07-03
Read this thread:

[http://ubuntuforums.org/archive/index.php/t-35137.html](http://ubuntuforums.org/archive/index.php/t-35137.html)

---

### Post by Slinker on 2005-07-03
ok, 2 things: 
1. I cant seam to write in the file 'xorg.conf' and i cant change permisions on it..?!?
2. What if i whant to change the hz then? from 60 to 85?

---

### Post by Xian on 2005-07-03
[QUOTE=Slinker]
I cant seam to write in the file 'xorg.conf' and i cant change permisions on it..?!?[/QUOTE]
Open a terminal and issue this command:
```
$ sudo gedit /etc/X11/xorg.conf
```

---

### Post by Slinker on 2005-07-03
this is my xorg.conf 
adding the resulution didnint work, yes i did a reboot =)

----------------------------------------------------------


Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
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
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by frodon on 2005-07-03
ok change that : ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-**149**
VertRefresh 43-**172**
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes **"1280x1024"** "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes **"1280x1024"** "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes**"1280x1024"**  "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes**"1280x1024"**  "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes**"1280x1024"**  "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
EndSection
```and reset xserver (Ctrl+Alt+Backspace)

I think it should work now.

---

### Post by Slinker on 2005-07-03
Everything works fine now, thank you al!

---

### Post by kairos on 2006-01-09
I have done as described,
and made sure that xorg.conf is updated with higher resulution options. 
But they do not appear in the dialog box. 
Have also restarted my  laptop (IBM Thinkpad T40).

Can anybody help me?

---

