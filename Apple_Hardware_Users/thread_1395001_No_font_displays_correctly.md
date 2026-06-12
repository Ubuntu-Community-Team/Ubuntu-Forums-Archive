---
title: "No font displays correctly"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by cyram on 2010-01-31
Hello.  I usually can solve problems with ubuntu with a quick search, but I can't figure this one out or anyone else who has this problem!

I recently installed Xubuntu on an old eMac PPC using the mini CD.  Everything went pretty smoothly, and the distro runs excellently except for the fonts,  Abiword, Open office, and much of the notification system refuses to display almost any font.  I've tried different window managers (XFCE, IceWM, Openbox, Fluxbox), but all have the same problem.  I've tried reinstalling and have the same problem.  

I'd really appreciate any ideas anyone has on how to fix this!

---

### Post by linuxopjemac on 2010-01-31
what kind of emac do you have and can you post your Xorg.conf file ? Maybe you have to add a Files section with Fontspaths.

```
cat /etc/X11/xorg.conf
```

---

### Post by cyram on 2010-01-31
My eMac has a 15" CRT screen.  
The output of **cat /proc/cpuinfo**[INDENT]```

processor            0
cpu                    7455, altivec supported
clock                 999.999997MHz
revision             3.3 (pvr 8001 0303)
...
model               PowerMac4,4
motherboard     PowerMac4,4 MacRISC2 MacRISC Power Macintosh
pmac-generation NewWorld
...
Memory            128 MB

```[/INDENT]The output of ```
cat /etc/X11/xorg.conf
``` results in an error.  No such file or directory.  Does this help?

---

### Post by linuxopjemac on 2010-01-31
I can only find an emac with a 1GHz processor with a 17'' screen...

---

### Post by cyram on 2010-01-31
Oh, you're right.  17"  I thought it was smaller since I was comparing it to my current one.

---

### Post by linuxopjemac on 2010-01-31
I think you own an emac ATI:
[http://apple-history.com/body.php?page=gallery&model=emac_ati&sort=date&performa=off&order=ASC](http://apple-history.com/body.php?page=gallery&model=emac_ati&sort=date&performa=off&order=ASC)

right or not ?

---

### Post by cyram on 2010-01-31
Yes, that looks like it, and all the specs seem to match it.

---

### Post by linuxopjemac on 2010-01-31
ok let's try to make a working Xorg.conf for you, you should have one in /etc/X11. Just copy and paste in an editor like nano:

sudo nano /etc/X11/xorg.conf

now copy and paste the following lines

```
Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/usr/share/fonts/X11/Type1"
# paths to defoma fonts
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "InputDevice" 
Identifier "Generic Keyboard" 
Driver "kbd" 
Option "XkbRules" "xorg" 
Option "XkbModel" "pc105" 
Option "XkbLayout" "gb" 
Option "XkbOptions" "lv3:lwin_switch" 
EndSection

Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
EndSection

Section "Device" 
Identifier "Configured Video Device" 
BusID "PCI:0:16:0" 
Option "UseFBDev" "true" 
Option "ConnectorTable" "100,1,0,1,108,2,0,1" 
Option "ReverseDDC" "true" 
Option "AGPMode" "4" 
EndSection

Section "Monitor" 
Identifier "Configured Monitor" 

Modeline "1280x960_72.00" 124.54 1280 1368 1504 1728 960 961 964 1001 +HSync +Vsync

Option "PreferredMode" "1280x960_72.00" 

EndSection

Section "Screen" 
Identifier "Default Screen" 
Monitor "Configured Monitor" 
EndSection

```

after the paste you end with CTRL-X and "y" to save the changes

then restart X:

```
sudo /etc/init.d/gdm restart
```

---

### Post by linuxopjemac on 2010-01-31
if you like we can also try the ATI driver for this machine....

---

### Post by cyram on 2010-01-31
I copied the xorg.conf to the right place, restarted, and it didn't work.  Still no fonts will display.   I guess the ATI driver is next.  I didn't think that driver was released for ppc...

---

### Post by linuxopjemac on 2010-01-31
The following Xorg.conf is actually for its successor, the emac 1.25 GHz with a Radeon 9200, you have a Radeon 7500....We can just try if it works...

```
Section "ServerLayout"
	Identifier	"eMac Configuration"
	Screen 0	"Screen0"		0 0
	InputDevice	"Apple Mouse"		"CorePointer"
	InputDevice	"Apple Keyboard"	"CoreKeyboard"
EndSection

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/usr/share/fonts/X11/Type1"
# paths to defoma fonts
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection


Section "InputDevice"
	Identifier	"Apple Keyboard"
	Driver		"kbd"
	Option		"XkbModel"		"macintosh"
	Option		"XkbLayout"		"us"
	Option		"XkbOptions"		"grp:caps_toggle"
EndSection

Section "InputDevice"
	Identifier	"Apple Mouse"
	Driver		"mouse"
	Option		"ZAxisMapping"		"4 5"
	Option		"Protocol"		"IMPS/2"
	Option		"Device"		"/dev/input/mice"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	71-73
	VertRefresh	70-140
	Modeline	"1024x768" 99.190000 1024 1072 1168 1376 768 769 772 810 +HSync +VSync
	Modeline	"1280x960" 122.240000 1280 1328 1424 1696 960 961 964 1002 +HSync +VSync
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200]"
	BusID		"PCI:0:16:0"
	Driver		"ati"
	Option		"monitor-DVI-0"		"iMac"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies Inc RV280 [Radeon 9200]"
	Monitor		"iMac"
	DefaultDepth    24
	SubSection "Display"
		Depth   24
		Modes   "1280x960" "1024x768" "800x600"
	EndSubSection
EndSection
```

---

### Post by cyram on 2010-01-31
I have more resolutions available, but still the fonts all give me gibberish.  Is there maybe a way to reinstall all of the fonts from a different source?  Maybe the ones I have are corrupted somehow...

---

### Post by linuxopjemac on 2010-01-31
I am a bit lost to be honest, going through the forums, as I remember a similar case as you, I finally found it:

[http://ubuntuforums.org/showthread.php?t=1323126&highlight=text](http://ubuntuforums.org/showthread.php?t=1323126&highlight=text)

you might want to contact him if he solved it.

---

### Post by cyram on 2010-01-31
I'll try to contact him.  Thanks for your help!

---

### Post by linuxopjemac on 2010-01-31
I can only tell you what I have installed with respect to fonts:

[ATTACH]145519[/ATTACH]

[ATTACH]145520[/ATTACH]

[ATTACH]145521[/ATTACH]

---

