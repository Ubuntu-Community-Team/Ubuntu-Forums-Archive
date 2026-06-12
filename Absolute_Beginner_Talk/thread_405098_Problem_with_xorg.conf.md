---
title: "Problem with xorg.conf"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by roise_r on 2007-04-09
hello, and sorry for these absolute newbie questions... but i got my self totally confused...

i am real noob in ubuntu . i started using it a couple of days ago, when i decided that i would better not touch a computer anymore, then using windows as my OS. i am doing OK since am i not a total noob in computers, i can manage my self around windows pretty well. i came to realize though, that things in linux are "little bit different". for example: i am reading and reading for the last 3 hours about how to install just the driver for my video card which is 'VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)'   i searched, and read differnt topics around forums, and it seems that i have to compile the drivers my self????  i dont want to compile, i just want to install some drivers that would stop my screen from scrolling everytime that i open a new window:) i.e. put some 3d to work..:) so i read about DRI, and recompiling the kernel and stuff...?! isn't there a way just to intall the drivers in a .deb packedge...? or should i ask, what is the easiest way for a total noob to install video drivers for ubuntu :) i also have another computer that i want to install video drivers nvidia FX6200. and pls, in the Gods name, how to check what is my xorg.conf and kernel version. here is my xorg.conf file:

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
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option "EnableAGPDMA"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
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

### Post by jhenager on 2007-04-09
You won't get banned for asking questions here.
I wouldn't think you would need to install any drivers. I have a motherboard with the Unichrome chip, and I didn't have any problem.
Can you elaborate on the scrolling?
AS for 3D or DRI, the Unichrome chip isn't capable of those kinds of tricks, as far as I know. Compiling a kernel might be getting ahead of yourself a bit right now.

---

### Post by ComplexNumber on 2007-04-09
**roise_r**
i changed your thread title. you will definitely not, under any circumstances, get banned for asking questions :). all questions are good and acceptable questions.


are you wanting to run beryl?
also, i agree with the above poster - compiling your own drivers is pretty much advanced stuff. from personal experience, i've never had to do that.

i believe that the fx6200 driver can be installed as a deb through synaptic. 

1) you need to install the nvidia-glx package for hardware acceleration. fire up synaptic, click on 'Settings' in the menu, then click on 'Repositories'. do you have all the reposoitories ticked in the first tab? if not, tick them all, then reload.
then look for "nvidia-glx" and install that.

2)  [this]("http://ubuntuguide.org/wiki/Ubuntu:Edgy/EyeCandy") thread may be helpful.


please post back and let us know how you get on, or post back with any queries.

---

### Post by roise_r on 2007-04-09
ok, first things first... 

1.actually i was looking more for help on the VIA S3 unichrome card, as it is my home laptop that i use... the FX6200 is my work computer, and for now i am afraid that i will have to use windows cause there are a couple applications that i need some time to migrate them to linux... 
2. as i was reading about how to install all this,  i came across different posts saying that actually via S3 unicrome chipset supports the DRI and 3d and all related stuff :), the problem is that i must work my way to the end result - having hardware acc... it is not automated like in the fx6200 case. :
 
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=101](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=101)

[http://doc.gwos.org/index.php/VIAUnichromeDRI](http://doc.gwos.org/index.php/VIAUnichromeDRI)

[http://ubuntuforums.org/archive/index.php/t-75377.html](http://ubuntuforums.org/archive/index.php/t-75377.html)

[http://ubuntuforums.org/showthread.php?t=75393](http://ubuntuforums.org/showthread.php?t=75393)

[http://sourceforge.net/docman/display_doc.php?docid=26963&group_id=102048](http://sourceforge.net/docman/display_doc.php?docid=26963&group_id=102048)

 is this what i am looking for?

3. as for the scrooling, i mean real scrooling as in widows when acc is not turned on... everything you do scroolz! :) moving up and down on pages - scrools, surfing the internet - scroolz. for example if i open a page that has flash animations - it WILL scroll a lot, while the animations are moving, even if i minimize firefox, Scrool meaning that even the mouse noticeably scrools. i would have to change to different tab without animations so everything would get unscrooled:) you can trust me when i say that there isnt any acc running... even though, by default, in the xorg file the name of my card was written, it was not some vesa driver. 

4."AS for 3D or DRI, the Unichrome chip isn't capable of those kinds of tricks, as far as I know."
as ashamed as i am about saying this, but in windows, i get by default the acc and 3d things. i dont have to install anything. i check it by going to : start->run->dxdiag->display tab... all three accs are ON.  I am not saying this in the means that Windows is better "in Gods name NO!... but just to focus that it is not true that this video card doesn't support 3d.

5.i read about beryl, and sounds really neat. i surely would like to check it out, but i also read the compatibility list and my video is not among them :(... maybe in my work machine... plus, i think i need to fix the driver thing first before installing something that requires 3d acc for sure:)

6.so how to check my xorg version if it has one, couse i can change it content whenever i like :), what about kernels version

7. what is the strongest way to check in any given moment if the 3d acc is enabled... just like in the dxdiag utility (sorry again for comparing with windows)

8.what is the difference between:
dpkg-reconfigure xserver-xorg		and        
dpkg-reconfigure -phigh xserver-xorg

9. under which vendor should i search my drivers:  VIA or S3 or UniChrome... casue some sources, for example, have all three drivers as different files : ) which kinda confuses me : )  

10. what about this build essential...? apt-get install build-essential         what does this do?
10x again ... :)

---

### Post by ComplexNumber on 2007-04-09
hmmm there's a lot there to take in. ok, i'll see what i can do.

oh dear, it seems like it isn't properly supported ([click]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046&view=next")). unfortunately, manufacturers are more keen to make the drivers for windows because most PC's run windows.

there isn't really an xorg version - its more the

to check if its enabled, you can run glxinfo and 'glxgears -printfps' on the command line.

for your driver, i woulds search for "via" and  "VT8378".

the build-essential packages is need to compile packages, i believe.

---

### Post by rlgoddard on 2007-05-29
Hi roise_r,

I also have a VIA Unichrome graphics chip (VT8378 as well) and have been exploring ways to enable 3D under Ubuntu.  There isn't any way to do so, unfortunately.  I am in the process of acquiring an nvidia fx6200 graphics card myself to replace the integrated (and crappy) graphics chip.

---

