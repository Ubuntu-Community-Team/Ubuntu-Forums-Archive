---
title: "Help with Monitor/Video Card?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by volcomstn on 2007-07-25
I am very new to Linux and need some help. Yesterday i installed Ubuntu but when i did i got a very distorted image, mess up colors, and a box floating around on my monitor saying "Input not supported." According to my manual my refresh rate was too high at 85hz, when the max is 75hz and optiomal is 60hz. So i tired to change this but i couldn't change the refresh rate as it was stuck.

I read around the forum and tired a few different how to guides (like this [one]("http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate+problems")) but that didnt seem to help me and i made it worse a few times. You can see what i did to /etc/X11/xorg.conf [here]("http://ubuntuforums.org/showthread.php?t=508957&highlight=cant+get+monitor+to+work"). 

After this didn't work i asked on the forum and was directed to use Sudo dpkg-reconfigure xserver-xorg. This at first started to help but i got the wrong resolution and the colors were still not right. After changing the setting to the proper ones, i still couldn't change the refresh rate and was in the same boat. Actually a couple of times i made it worse again, where i couldnt see anything. Finally after several hours i decided to reinstall and start over before i mess anything up again.

So now i got a fresh install and i have no idea what to do. My monitor is a LCD Rosewill R912E, Recommended Resolutions 1280x1024@60hz. My video card is a ATI Radeon 9250. Is this problem due to my monitor or my graphics card? I read of others having problems with similar graphics cards but i never seemed to find a solution. The other problem is i dont know much at all (besides what i read) about linux and i cant mess with it can i cant see what i am doing most of the time. Any help at all would be very much appreciated.

---

### Post by MrHippocampus on 2007-07-25
Please post your current /etc/X11/xorg.conf so we can see whats going on :)

---

### Post by volcomstn on 2007-07-25
Well, just when i posted this i saw [this ]("http://ubuntuforums.org/showthread.php?t=414194")how to, and now when i try to log on it configuration error, or something similar to that and i don't know how to get back in Ubuntu.

---

### Post by overdrank on 2007-07-25
> **volcomstn said:**
> Well, just when i posted this i saw [this ]("http://ubuntuforums.org/showthread.php?t=414194")how to, and now when i try to log on it configuration error, or something similar to that and i don't know how to get back in Ubuntu.

That sticky is meant for newer cards. Did you get the xorg error and you cant reach the desktop. If so click ok and get to command prompt login user name and password. then enter the command 
```
sudo dpkg-reconfigure xserver-xorg
```
And hopefully this will get you back to the desktop. Good luck!

---

### Post by volcomstn on 2007-07-25
The exact error messages is, "Failed to start the x server. Its likly that it is not set up correctly." And it has a blue screen back ground. I hit ctrl + alt + f1 and got the command like (i think that is what its called). Is there anyway to use the back up file i created when i did that?

---

### Post by volcomstn on 2007-07-25
sudo dpkg-reconfigure xserver-xorg is not working.Wehn i chage the seeting to what i need and reboot i just get a black screen. Do i need to reinstall ubuntu or is there another way?

---

### Post by overdrank on 2007-07-25
> **volcomstn said:**
> sudo dpkg-reconfigure xserver-xorg is not working.Wehn i chage the seeting to what i need and reboot i just get a black screen. Do i need to reinstall ubuntu or is there another way?

Yes use the same command and select the vesa for the driver that will get you back to the desktop and the use Envy to install the drivers, It has worked for me on a ATI 9200. 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Good luck

---

### Post by volcomstn on 2007-07-25
> **overdrank said:**
> Yes use the same command and select the vesa for the driver that will get you back to the desktop and the use Envy to install the drivers, It has worked for me on a ATI 9200. 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Good luck

Ok i got back to the desktop. I installed the program you recomended and when i clicked install ATI driver the following came up..

Your graphic card has been detected as a ATI RADeon 9250.
Your graphic card is supported by the legascy driver.
ENVY ERROR: ATI's lagacy driver does not support your operative system.

Did i do something wrong?

---

### Post by overdrank on 2007-07-25
> **volcomstn said:**
> Ok i got back to the desktop. I installed the program you recomended and when i clicked install ATI driver the following came up..

Your graphic card has been detected as a ATI RADeon 9250.
Your graphic card is supported by the legascy driver.
ENVY ERROR: ATI's lagacy driver does not support your operative system.

Did i do something wrong?

Hi you did nothing wrong apparently I did. Try this "how to"
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
I know it is for beryl but use the first portion for installing the drivers for your card! Hope this helps [-o<

---

### Post by volcomstn on 2007-07-25
> **overdrank said:**
> Hi you did nothing wrong apparently I did. Try this "how to"
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
I know it is for beryl but use the first portion for installing the drivers for your card! Hope this helps [-o<

Ok so i did that guide and when i restarted i got the same error i got in post #5. Each time i hit alt +ctrl + f1 and run sudo dpkg-reconfigure xserver-xorg to go back to the setting that let me see the desktop at least. I also just wanted to thank you so much for helping me. I want to run Ubuntu so bad but i am just completely lost on what to do.

---

### Post by overdrank on 2007-07-25
> **volcomstn said:**
> Ok so i did that guide and when i restarted i got the same error i got in post #5. Each time i hit alt +ctrl + f1 and run sudo dpkg-reconfigure xserver-xorg to go back to the setting that let me see the desktop at least. I also just wanted to thank you so much for helping me. I want to run Ubuntu so bad but i am just completely lost on what to do.

Ok did you try and change the driver in your xorg to radeon like the "how to " suggested?

---

### Post by myoungf1 on 2007-07-25
A couple of things, first do you have an onboard intel video chipset on your motherboard and can you post your xorg.conf file in the /etc/X11 folder for us to look like.

---

### Post by volcomstn on 2007-07-25
> **overdrank said:**
> Ok did you try and change the driver in your xorg to radeon like the "how to " suggested?

Yes but not since i reinstalled Ubuntu. Should i do that guide again?

---

### Post by volcomstn on 2007-07-25
This is my current /etc/X11/xorg.conf

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

### Post by myoungf1 on 2007-07-25
Okay i am posting a copy of my xorg.conf for you to compare.  I have an ATI Radeon 9250 graphics card and the open source drivers that come with Ubuntu work straight out of the box.  The reason I asked if you had onboard intel video is you might have to change that in your computers bios to get anything working properly for the xserver.  I had to do that same thing with my daughters computer before it worked properly.  

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
	Identifier	"ATI Radeon 9250"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	128000
EndSection

Section "Monitor"
	Identifier	"ViewSonic 20PS"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9250"
	Monitor		"ViewSonic 20PS"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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

### Post by volcomstn on 2007-07-25
myoungf1, Hey glad to see you again. Hum yes i do have on board video. I thought about trying using that, but i wasnt sure how. Do you think i should go ahead and disable my on board video in the bios?

---

### Post by myoungf1 on 2007-07-25
Yes that should help you get your ATI card working properly.

---

### Post by volcomstn on 2007-07-25
Ok i got my motherboard manual out and i don't see anything about disabling my on board video.  I did check the BIOS, but i did see anything there. I briefly checked the internet (where i will keep looking) but havnt found what i was looking for yet. I was wondering if you knew where i should look? My motherboard is a mach speed p4m80 if that helps. Sorry if i am supposed to know this but i am trying not to mess things up on here too badly.

---

### Post by myoungf1 on 2007-07-25
Do you know your bios name and version?  That should help immensely to get some help on what settings you have.

---

### Post by volcomstn on 2007-07-25
All i could really find was "Phoenix - Award BIOS CMOS."  I couldnt really find wich version or anything.

---

### Post by myoungf1 on 2007-07-25
Okay try this website and see if it helps [http://www.buildeasypc.com/sw/bios_setup.htm#pnp_pci](http://www.buildeasypc.com/sw/bios_setup.htm#pnp_pci)

Also give this wiki a try [http://www.wikihow.com/Disable-Onboard/Integrated-Video-On-Your-Computer](http://www.wikihow.com/Disable-Onboard/Integrated-Video-On-Your-Computer)

---

### Post by volcomstn on 2007-07-25
Well i didnt see anything there. Under standard CMOS Features there is video and 4 options EGA/VGA, CGA 40, CGA 80, Mono. EGA/VGA is selected. Also when i try pluging in my monitor to my on board video i get no singal. Does that mean it is disabled?

---

### Post by myoungf1 on 2007-07-25
Yeah then your bios disabled it automatically so you should be set.  The next step is to reconfigure xserver and make sure to specify your monitor name and your video card name.  Take a look at my xorg.conf for a reference point.

---

### Post by volcomstn on 2007-07-25
myyoungf1, i am sorry but i got to leave right now, umm i will be sure and do that maybe tonight or tomorrow if not. I guess if i just keep working at it we can get it sooner or later. Thanks again. Next time i will just bump this thread instaed of starting a new one too. Thanks again.

---

### Post by volcomstn on 2007-07-25
Ever time i change anything with /ect/xll/xorg.conf and reboot it there is just a black screen. I can hear the sounds of Ubuntu starting up though. The only thing i could change was the H-Frequency and V-frequency with out a black screen appearing after i restarted. Any suggestions?

---

### Post by myoungf1 on 2007-07-26
Sorry for the late reply try this thread and see if it helps.

[http://ubuntuforums.org/showthread.php?t=509725&highlight=ati+radeon](http://ubuntuforums.org/showthread.php?t=509725&highlight=ati+radeon)

---

### Post by volcomstn on 2007-07-26
> **myoungf1 said:**
> Sorry for the late reply try this thread and see if it helps.

[http://ubuntuforums.org/showthread.php?t=509725&highlight=ati+radeon](http://ubuntuforums.org/showthread.php?t=509725&highlight=ati+radeon)

No probelm, i am just gald to get help. I tired the first method and everything works the same. I am going to go ahead and try the second method now. I was also thinking last night, would it just be better to use the on board video? Or maybe get a cheap graphics card to make this work?

---

### Post by volcomstn on 2007-07-26
Ok i am having trouble with the second one now. I download it but i get this error message when i try and run it > gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

It says "Change to the download directory. " after where you download that, but i am not sure if that is talking about the next step or not, if not i am not really sure what that means.

---

### Post by myoungf1 on 2007-07-26
did you do the sudo bash ./(run package name here)

---

### Post by volcomstn on 2007-07-26
I got this message then> bash: ati-driver-installer-8.38.7*.run: No such file or directory


I feel like i am doing something wrong but i am not sure what.

---

### Post by myoungf1 on 2007-07-26
Okay first off those drivers won't work for your card.  [http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)  go there and select the ATI installer and download it.  Once you have done that go to the terminal and type sudo bash ./ati-driver-installer-8.28.8.run

---

### Post by volcomstn on 2007-07-26
I got this error again> bash: ./ati-driver-installer-8.28.8.run: No such file or directory


I am just downloading it to my desktop, is that the problem?

---

### Post by myoungf1 on 2007-07-26
Make sure you are in your Desktop folder in the terminal type cd Desktop and then run the command again

---

### Post by volcomstn on 2007-07-26
Well that was the problem, lol. But it still didnt work i dont think. I got this error this time..> Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


---

### Post by myoungf1 on 2007-07-26
Okay for that particular problem try this thread and see if it works for you.

[http://ubuntuforums.org/showthread.php?t=312666&highlight=fglrx+install+error](http://ubuntuforums.org/showthread.php?t=312666&highlight=fglrx+install+error)

---

