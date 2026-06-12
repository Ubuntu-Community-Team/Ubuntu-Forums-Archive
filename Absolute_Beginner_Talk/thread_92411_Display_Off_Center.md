---
title: "Display Off Center"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by Xanthos on 2005-11-19
I just installed ubuntu for the first time today. I edited my xorg.conf file to set my screen resolution and refresh rate to match my Windows install. However, the screen display is off center. I would simply adjust my monitor settings, however, that would make it off center when I use Windows. Is there any other way to center the display?

---

### Post by Dr. Nick on 2005-11-20
Im not sure how to do it in linux, what type of video card do you have? With nvidia and ATi most likely you can change the screen postion in windows cantrol panel, So you may set your monitor correctly for linux and then adjust it in windows instead of vice versa

---

### Post by darkmatter on 2005-11-20
[QUOTE=Xanthos]I just installed ubuntu for the first time today. I edited my xorg.conf file to set my screen resolution and refresh rate to match my Windows install. However, the screen display is off center. I would simply adjust my monitor settings, however, that would make it off center when I use Windows. Is there any other way to center the display?[/QUOTE]

There is a bug in the 2D nv driver...to fix that...use the command

```
xvidtune
```

you will get a warning...click ok...use the buttons for left, right, up, down to move your screen position...YOU MUST HIT 'APPLY' to apply the changes...

After you play for a bit and get things centered...hit 'show' in the xvidtune UI...this will print an output string...the ModeLine in the terminal...

next, open another terminal (leave the xvidtune one open) an enter

```
sudo gedit /etc/X11/xorg.conf
```

add a line to the 'Monitor' section...'UseModes'....give it a name...mine is TTX as I use a TTX monitor...it will look something like this when edited (from mine)

```
Section "Monitor"
        UseModes        "TTX"
	Identifier	"TTX-7565E"
	Option	        "DPMS"
	HorizSync	30-70
	VertRefresh	50-120
EndSection
```

and create a new section ABOVE this...and input the other terminals output (copy/paste) under ModeLine

```
Section "Modes"
        Identifier    "TTX"
        ModeLine      <insert terminal output here>
EndSection
```

Save and restart X...or reboot...and the screen will be centered...

If you install the 3D drivers...the 'Modes' section and the 'UseModes' under display will have to be commented out...

---

### Post by buzzbuzz on 2005-11-24
I've got the same problem and have tried your work around darkmatter, but come up against this [*Sorry: You have requested a mode-line that is not possible, or supported by your hardware configuration*]  even when i try to move the screen one position to the right or left. [please note that when i click on the left/right/up/down buttons, the screen doesn't actually move. i only get this error message when i click 'apply'].

at the moment the screen is at a resolution of 1280x1024 @75Hz and is just over 1cm off centre. this has been setup from system/preferences/screen resolution menu.

the screen is centered when running at 1024x768, but i prefer the previous resolution. i can move the screen centering with the monitor i'm using, but as i'm using a kvm switch, it's messes with the other pc i have connected.

the setup i have is:-

Ubuntu Breezy 5.10 [all updates as of today 24/11/05]
eMachine Pent 4, 2.66Ghz
256 MB RAM
Motherboard Intel D845GVSR 'Sea Breeze'
Graphics Card Intel 845G intergrated graphics

and this is the output from the terminal when i run xvidtune:-

:~$ xvidtune
Vendor: , Model:
Num hsync: 1, Num vsync: 1
hsync range 0:  30.00 -  83.00
vsync range 0:  56.00 -  75.00

and when i click show, this is the output:-

"1280x1024"   135.00   1280 1288 1432 1688   1024 1025 1028 1066 +hsync +vsync


am i trying to do something stupid?!! :confused:

[screenshot attached if it will help more]

---

### Post by buzzbuzz on 2005-11-29
sorry to be a pain, but can anyone tell me if i'm being stupid.....
[wait for it..........:-\" ]

---

### Post by buzzbuzz on 2005-12-09
no replies then, so I can't be stupid?? :confused: 

if anyone could help, it would be appreciated.

thanks

---

### Post by mendosa on 2005-12-10
Hi, there buzzbuzz, I don't know if I can be much help, because I am a beginner, but there might be four things in Your case:
1.Problem with the monitor, the only way of checking this is to connect your PC to another monitor.
2.Graphic card problem, the same workaround as above, or maybe broken driver.
3.I would set the values of Horizontal Sync down (by editing xorg.conf), my display is theoretically able to run 85, but it never reaches 70.
4.Something not installed properly, maybe xvidtune?(Gee, I had a big problem with nvidia drivers, been working a week, the reason was incorrect partition numbers, affecting the installation). 
BTW I think You aren't stupid, these linuxes are fine, but sometimes hard to customize, Keep Trying!!:)

---

### Post by buzzbuzz on 2005-12-12
thanks for your reply mendosa :)

i'm pretty sure the monitor and graphics card are ok, as i have my ubuntu box connected up with a kvm switch to an xp machine as well and that is working fine [graphics-wise that is!!].

i'll try re-installing xvidtune [should of thought of that, but there are so many things to think of when you're learning something new; wood for the trees an' all that!!].

if that doesn't work, i'll give xorg.conf an edit. :D

---

### Post by buzzbuzz on 2005-12-12
no luck

i've re-installed xvidtune and that still does what it did before [i still don't know if the screen is meant to actually move when you press a 'right' or a 'left' button; no-one seems to know].

so i've played around with the settings in xorg.conf [similar to what darkmatter was talking about in the earlier post], from trying to second guess the values that xvidtune was outputting and still no luck; i get the same errors and the screen is still about 1cm off from the right.

snippet from my new xorg.conf:-

Section "Monitor"
	Identifier	"photon19visi"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	56.2-75
EndSection

and yet xvidtune shows this:-

Vendor: , Model:
Num hsync: 1, Num vsync: 1
hsync range 0:  30.00 -  83.00
vsync range 0:  56.00 -  75.00

i don't know if the difference in the HorizSync between the two makes a difference?

any further ideas on what i could try?

---

### Post by olieviya on 2005-12-12
I need help - I've followed your advice, since I have the same problem but it's not working!
(It works but when I restert it goes away!!!!)

olivia@ubuntu:~$ xvidtune
Vendor: , Model:
Num hsync: 1, Num vsync: 1
hsync range 0:  28.00 -  61.00
vsync range 0:  48.00 -  65.00
"1024x768"     65.00   1024 1048 1184 1344    768  771  777  806 -hsync -vsync


AND


Section "Modes"
        Identifier    "SONY"
        ModeLine      "1024x768"     65.00   1024 1068 1204 1344    768  771  777  806 -hsync -vsync

EndSection

Section "Monitor"
        UseModes        "SONY"
	Identifier	"SONY-SDM-S51"
	Option	        "DPMS"
	HorizSync	28.00 -  61.00
	VertRefresh	48.00 -  65.00
EndSection

---

### Post by mendosa on 2005-12-13
Olieviya, this worked for me: editing xorg.conf:

Section "Monitor"
	Identifier	"T710PH"
	Option		"DPMS"
	[COLOR="Magenta"]HorizSync	[/COLOR][COLOR="SeaGreen"]30-85[/COLOR]
	[COLOR="Magenta"]VertRefresh[/COLOR]	[COLOR="SeaGreen"]50-160[/COLOR]
	[COLOR="Magenta"]Modeline[/COLOR]	[COLOR="SeaGreen"]"1024x768"     94.50   1024 1060 1156 1388    768  769  772  808 +hsync +vsync[/COLOR]
EndSection

Just delete section Modes, delete entry Use Modes in section Monitor , create pink entries, and put values given by xvidtune in place of those green. The Identifierier should be "SONY-SDM-S51" in Your case.

Buzzbuzz, the values in xorg.conf should be taken from xvidtune, so in Your case they should look like this:

[COLOR="Magenta"]HorizSync [COLOR="SeaGreen"]30-83[/COLOR]
VertRefresh [COLOR="SeaGreen"]56-75[/COLOR][/COLOR]

As far as I know, the screen will move when You click Test, or Apply in xvidtune, it won't move when You are just changing values by pressing left or right.

---

### Post by olieviya on 2005-12-13
Thanks, I'll try it right now!

---

### Post by olieviya on 2005-12-13
I just did it all over and restarted but nothing, what am I doing wrong?



Section "Monitor"
	Identifier	"SONY-SDM-S51"
	Option	        "DPMS"
	HorizSync	28.00 -  61.00
	VertRefresh	48.00 -  65.00
	Modeline "1024x768"     65.00   1024 1064 1200 1344    768  771  777  806 -hsync -vsync

EndSection

---

### Post by mendosa on 2005-12-13
Well, now I am completely stuck:???: Maybe use [COLOR="SeaGreen"]Mode[COLOR="Magenta"]Line[/COLOR][/COLOR] instead of [COLOR="SeaGreen"]Modeline[/COLOR]?
However this should't matter 'cos in previous post I gave output of my xorg.conf, with [COLOR="SeaGreen"]Modeline[/COLOR]. Maybe that's a graphic card issue? What graphic card are You using?
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)
I hope You can find the answers there, although it is normal that something that is working for one, won't work for another one.

---

### Post by olieviya on 2005-12-13
If i'm not very much mistaken I do believe it to be an Nvidia geforce4.
What am I exactly supposed to do with the link, follow all the instuctions?

---

### Post by mendosa on 2005-12-13
Try reading that thread, maybe the solution is out there, but meanwhile can You give the whole xorg.conf here? Maybe we will see the problem there.

---

### Post by olieviya on 2005-12-13
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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SDM-S51"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SDM-S51"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
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


Section "Monitor"
	Identifier	"SONY-SDM-S51"
	Option	        "DPMS"
	HorizSync	28.00 -  61.00
	VertRefresh	48.00 -  65.00
	Modeline "1024x768"     65.00   1024 1064 1200 1344    768  771  777  806 -hsync -vsync

EndSection

---

### Post by olieviya on 2005-12-13
I will now carefully read this: [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

and try my very best to fix this - thanks. I'll report back when I do get this done.:KS

---

### Post by mendosa on 2005-12-13
ok, maybe that's it: You have doubled section Monitor. That one in the bottom is not necessary, but You should copy the values from there, to the Monitor section above. I rewrited your xorg.conf, but be sure to make backup, before making changes. Here it goes:

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV17 [GeForce4 MX 440]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "SDM-S51"
Option "DPMS"
[COLOR="Magenta"]HorizSync 28.00 - 61.00
VertRefresh 48.00 - 65.00
Modeline "1024x768" 65.00 1024 1064 1200 1344 768 771 777 806 -hsync -vsync[/COLOR]
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV17 [GeForce4 MX 440]"
Monitor "SDM-S51"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by olieviya on 2005-12-13
Thank you very much!


EDIT: Works perfectly!!! Ta!

---

### Post by Chayak on 2005-12-13
I have a similar problem with my system using an nvidia card. My 'fix' is the autoadjust on my monitor that will center itself when I switch computers from my KVM

---

### Post by mendosa on 2005-12-13
Maybe this, or similar solution will make the trick with KVM:

[http://www.ubuntuforums.org/showthread.php?t=48535&highlight=kvm+problems+desktop](http://www.ubuntuforums.org/showthread.php?t=48535&highlight=kvm+problems+desktop)

---

### Post by janrinok on 2005-12-13
buzzbuzz,  I discovered that if I wanted to use a KVM, I had to install Ubuntu with the KVM connected and in use.  I'm not sure if Ubuntu measures some parameters from the display connector and therefore needs to know about the KVM, or even if my explanation is correct, but I know that it worked for me.  Perhaps I was just lucky.

---

### Post by buzzbuzz on 2005-12-19
....sorry been away for awhile.....

thanks for the posts guys and i will give it another go and see if i can sort it this time :)

janrinok thanks for the idea, but unfortunately i think the kvm isn't the problem as i did install ubuntu with it connected and working. i did have hoary loaded on it before and this screen problem only came up with breezy.

i'll let you know how i get on.......

---

### Post by MGStreak on 2008-02-27
After a *lot* of nights of trial and error and board hunting, I finally solved this problem on my machine.  Here are my specs:

O/S: Ubuntu 7.10 (Gutsy Gibbon)
Video Card: Intel Corporation 82945G/GZ Integrated Graphics Controller
Driver: 'intel'
Monitor: Samsung SyncMaster 920NW
Native Resolution: 1440X900 @ 60 hz (Widescreen)

Solution:
[http://ubuntuforums.org/showthread.php?t=203905](http://ubuntuforums.org/showthread.php?t=203905)

My comment/addendum to the solution:
[http://ubuntuforums.org/showpost.php?p=4416287&postcount=67](http://ubuntuforums.org/showpost.php?p=4416287&postcount=67)

---

