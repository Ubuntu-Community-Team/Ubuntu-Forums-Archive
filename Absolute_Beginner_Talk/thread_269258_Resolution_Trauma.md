---
title: "Resolution Trauma"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by IusedTObeSOMEONEelse on 2006-10-01
I have been reading all the resolution post but I still can't keep up. I happened to "find" a monitor yesterday an I want to use it as it's bigger than what I had. Problem is that every thing seems giant size and some times all doesn't fit in window when should. Only given two resolution sizes 640x480 & 800x600. Please guy's, being the "Dumb Blonde" that I am take it easy on me. I am still learning my way around. Simple instructions.

---

### Post by bigken on 2006-10-01
in a terminal type **sudo dpkg-reconfigure xserver-xorg** use the space bar to select your required resolutions ;)

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
Thanks for reply, here's what comes up                                                     Password:
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

---

### Post by NESFreak on 2006-10-01
> **MustangSallydd said:**
> Thanks for reply, here's what comes up                                                     Password:
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

its xorg not org

NESFreak

---

### Post by bigken on 2006-10-01
copy and paste this [B]sudo dpkg-reconfigure xserver-xorg 

you typed xserver-org :rolleyes:
[/B]

---

### Post by bulldog on 2006-10-01
> **MustangSallydd said:**
> Thanks for reply, here's what comes up                                                     Password:
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

Well as you are a Edgy test user you should know the basic's of your install :D

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
ok, got it. Now it wants to ask me a lot of ??, but I am not sure of answers. I do know the monitor is Dell model #D1728D-LS and I am not sure of computers specs as I had it put together quite a while back to play w/linux. I tried googling earlier for info on monitor but got stuck on that one also #-o

---

### Post by bigken on 2006-10-01
just hit enter all the way except for your video driver and screen resolutions

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
And what do I put for driver and resolution stats?

---

### Post by bigken on 2006-10-01
what is your video card and select what ever screen resolutions your monitor will accept ;)

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
um... how do I find what video card I have, I know it's an Intel some thing...

---

### Post by bigken on 2006-10-01
do you still have windows on the drive if so boot into windows and go to control panel system device manager and look and see what is showing in the hardware panel or right click the desktop and select properties

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
Thanks for sticking w/me bigken. **NO** I don't have that other os!!                   ok got it  Intel 82810E  DC-133 CGC    Intel 82810EmDC-133 GMCH

---

### Post by bigken on 2006-10-01
for now just select vesa as your video driver ok the when you find what hardware you have you can run the dpkg again and select the right driver

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
See last post for edit !!

---

### Post by bigken on 2006-10-01
ok I think you need to select i810 give it a go

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
ok, I'm at screen resolution and I believe I have a 15 inch screen. What do I select for screen resolution?

---

### Post by bigken on 2006-10-01
ok select 480 by what ever it is 800 by 600 1024 by 768 ;)

640x480

800x600

1024x768

are you using a crt or lcd monitor if its a crt i doubt it will acept anything higher than 800x600

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
This is what's there: 1920x1440, 1920x1200, 1856x1392, 1892x1344, 1680x1050, 1600x1200, 1440x900, 1400x1050

---

### Post by bigken on 2006-10-01
use the arrow keys to scroll down and use the space bar to select 

640x480

800x600

1024x768

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
As you may have figured out I'm not the "Brightest Bulb on the Tree" sorry! None of the 3 y9ou posted are there, only what I put in my last post. Forgive my humor!

---

### Post by bigken on 2006-10-01
they must but be not to worry just go with default lol :rolleyes:

hit enter

---

### Post by bigken on 2006-10-01
> **MustangSallydd said:**
> As you may have figured out I'm not the "Brightest Bulb on the Tree" sorry! None of the 3 y9ou posted are there, only what I put in my last post. Forgive my humor!


are you a true blonde pmsl

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
Ok, done with it. Any thing else I should do now? Whats next or is that it. Thanks

---

### Post by bigken on 2006-10-01
that should be it I hope ;)

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
What about video adapter? Monitor is Dell Model D1728D-LS Every thing is still giant sized

---

### Post by bigken on 2006-10-01
did you select the i810 as your video adapter also have you tried 

system/preferences/screen resolution

---

### Post by mips on 2006-10-01
Here are your monitor specs: [http://support.dell.com/support/edocs/dta/04036/00000001.htm](http://support.dell.com/support/edocs/dta/04036/00000001.htm)

Do me a favour, post the contents of your **/etc/X11/xorg.conf** file here

I will edit what needs to be corrected and post it back so you can copy and paste.

---

### Post by bigken on 2006-10-01
> **mips said:**
> Here are your monitor specs: [http://support.dell.com/support/edocs/dta/04036/00000001.htm](http://support.dell.com/support/edocs/dta/04036/00000001.htm)

Do me a favour, post the contents of your **/etc/X11xorg.conf** file here

I will edit what needs to be corrected and post it back so you can copy and paste.

cheers ](*,)

---

### Post by mips on 2006-10-01
Sorry, that should read **/etc/X11/xorg.conf**   I left out a /

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
~$ /etc/X11xorg.conf
bash: /etc/X11xorg.conf: No such file or directory

---

### Post by mips on 2006-10-01
ok.

You need to open the file with a text editor.

**gedit /etc/X11/xorg.conf**  from the command promt should work, else use nautilus.

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied

---

### Post by mips on 2006-10-01
](*,)Sorry I'm leaving out the obvious things here.


**[COLOR=Red]sudo[/COLOR] gedit /etc/X11/xorg.conf  **

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
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
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
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
		Modes		"1024x768" "800x600" "640x480"
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

---

### Post by mips on 2006-10-01
First lets make a backup of your xorg file just in case.

```
sudo cp /etc/X11/xorg.conf /etc/X11/Xorg.conf.backup20061001
```Next lets edit the original file:
[COLOR=black]
[/COLOR]```
sudo gedit /etc/X11/xorg.conf
```Now, I'm not gonna repaste the entire file here. I'm only pasting the two section you have to change. The rest of the file stays the same and must be retained. 

The two sections of the file we are going to edit are, **Section "Monitor" **& [B]Section "Screen"

[/B]Ensure those two sections look like this:
```

Section "Monitor"
    Identifier "Generic Monitor"
    Option "DPMS"
    HorizSync 30-65
    VertRefresh 50-120
    DisplaySize 306 230
EndSection


Section "Screen"
    Identifier "Default Screen"
    Device "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
    Monitor "Generic Monitor"
    DefaultDepth 24
    SubSection "Display"
        Depth 1
        Modes "1024x768" "1024x768 ""800x600" "640x480" "720x400"
    EndSubSection
    SubSection "Display"
        Depth 4
        Modes "1024x768" "1024x768 ""800x600" "640x480" "720x400"
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1024x768" "1024x768 ""800x600" "640x480" "720x400"
    EndSubSection
    SubSection "Display"
        Depth 15
        Modes "1024x768" "1024x768 ""800x600" "640x480" "720x400"
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1024x768" "1024x768 ""800x600" "640x480" "720x400"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1024x768" "1024x768 ""800x600" "640x480" "720x400"
    EndSubSection
EndSection
```

**[COLOR=Red]Save[/COLOR] the file & Reboot**

---

### Post by mips on 2006-10-01
If you want you can try a higher resolution like 1280x1024 by simply adding that in the front of the Modes line above. I dunno whether it will work or not but could be worth a try.

---

### Post by mips on 2006-10-01
Does it work ?

---

### Post by IusedTObeSOMEONEelse on 2006-10-01
Sorry took so long. wanted to be real careful. I am all set. Much thanks to "mips" & "bigken"  :-D   Now I gotta work on wine for the hundreth time

---

### Post by mips on 2006-10-01
[http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
[http://doc.gwos.org/index.php/Wine](http://doc.gwos.org/index.php/Wine)

[http://www.getautomatix.com/](http://www.getautomatix.com/)  will do it in one click but you don't learn much.

---

### Post by mips on 2006-10-01
> **MustangSallydd said:**
> Sorry took so long. wanted to be real careful. I am all set. Much thanks to "mips" & "bigken"  :-D   Now I gotta work on wine for the hundreth time

No problem. Did you try 1280x1024 resolution ? Should look ok on a 17" monitor.

---

