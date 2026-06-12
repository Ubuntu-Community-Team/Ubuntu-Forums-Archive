---
title: "ATI Radeon 9200SE problems... again!"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by online14230 on 2007-01-17
Hi there.

Heres my R800 worth of problems for you to look at.
Firstly, I HAVE searched. I currently have 1769 web pages stored on my PC at home, and 39 more to on my flashdisk, which I saved today. There are probably duplicates, so give or take about 50. Ive done the research, and Ive tried the tutorials. Ive re-installed, dpkg'ed, sudo apt-gett'ed and synaptic'ed my but off. I think I could probably recite the contents of my /etc/X11/xorg.conf in my sleep. Ive even tried ndiswrapper, trying to get the blasted thing to work. Believe me, if you have to go that far, youve gone TOO far. ATI drivers dont work. Ubuntu drivers dont work. Nothing works, yet.
OK. Here goes...

I installed Dapper from the shipit discs. I have a snapshot of the repositories on DVD discs.. all good. I updated and upgraded. I tried ATI drivers first, as per fitzman49's method, obviously using the correct driver... AIRKNEEWAYS, that didnt work. Dont ask me why. There were ABSOLUTELY no errors during the install, and Ive had none yet. The only time I find that something went wrong, is when I reboot. That when X refuses to start because either it cannot find the screen/display, or it is NOT configured, cant remember the exact error.. So I proceeded to restore the backed up /etc/X11/xorg.conf and away we go, happy with the Mesa driver, and 12FPS according to glx-gears -printfps. Oh yeah, no DRI. Never had it. With ALL the tuts and How-to's Ive followed. Because I was only learning, I couldnt uninstall the drivers I had installed, so I trashed the installation (not intentionally) and had to re-install. Alls good. Tried the Ubuntu drivers, same problem. I decided to search. Started saving webpages, try the methods at home. since I started looking for a solution to this problem, Ive installed and removed 4 different prop ATI drivers in God knows how many ways, with X refusing to start every single time. Ive tried the Ubuntu Free drivers so many times, Ive forgotten the reason I wanted Dapper in the first place. Incidentally, Breezy worked fine, ESPECIALLY when I wanted to watch MOVIES VIA SVIDEO on my TV. Yes, it worked on Breezy:)
Now, dos anyone have any ideas? Ill tell you what. Its 00h50 here and Im tired. Im at work. Im heading home now. Im gonna re-install... again, because now, every time I fire up dapper, X fails to start. I type in startx, and it works. Dont ask me what I did to it. Ive done too much. Im rambling because Im tired.

My machine: Dell Optiplex GX150, 320MB RAM, 200GB HDD, ALL dell stuff except the ATI Radeon 9200SE, which, incidentally, works WONDERS with XP. Ive got Porsche Unleashed, Underground, Underground 2, Most Wanted AND Carbon Collectors Edition installed and they all work beeeeeaaaaoooootifully!! My wifes gonna leave me because of Carbon :)
Anyway, back to the problem: Heres a few things to help you help me:

```
yolande@yolandes-troubles:~$ lspci -n | grep
 0300
0000:01:00.0 0300: 1002:5964 (rev 01)

yolande@yolandes-troubles:~$ lspci |grep
 VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

yolande@yolandes-troubles:~$

yolande@yolandes-troubles:~$ fglrxinfo

display: :0.0  screen: 0

OpenGL vendor string: Mesa project: www.mesa3d.org

OpenGL renderer string: Mesa GLX Indirect

OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


yolande@yolandes-troubles:~$ glxgears -printfps

487 frames in 6.0 seconds = 81.335 FPS

456 frames in 6.2 seconds = 74.016 FPS

456 frames in 5.9 seconds = 77.167 FPS

456 frames in 6.2 seconds = 73.218 FPS

456 frames in 6.2 seconds = 73.286 FPS

456 frames in 6.3 seconds = 72.769 FPS

456 frames in 6.2 seconds = 73.120 FPS

X connection to :0.0 broken (explicit kill or server shutdown).





My xorg.conf:

Section "Files"
	
FontPath	"/usr/share/X11/fonts/misc"
	
FontPath	"/usr/share/X11/fonts/cyrillic"
	
FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	
FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	
FontPath	"/usr/share/X11/fonts/Type1"
	
FontPath	"/usr/share/X11/fonts/100dpi"
	
FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	
FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

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

	Load	"v4l"

	Load	"vbe"

EndSection


Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"CoreKeyboard"

	Option		"XkbRules"
	"xorg"

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
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"DELL M781p"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor		"DELL M781p"
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


from dmesg |tail
:
[4294789.511000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294789.511000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294789.837000] [drm] Setting GART location based on new memory map
[4294789.837000] [drm] Loading R200 Microcode
[4294789.837000] [drm] writeback test succeeded in 1 usecs
```

For your benefit, Ill post my Xorg Logs.. ANYONE, please help! I REALLY wanna get rid of my VirusMagnet!

B

---

### Post by online14230 on 2007-01-17
Heres Xorg.0.log
I had to zip them to get them there :)

](*,) 
Yet again, have fun!

B.

Ill be formatting and re-installing in the hope that SOMBODY comes up with an idea for me. Just one thing: I saw a few people having, instead of fglrx or ati as their driver under the device section, theyve had "radeon"... huh? Believe it or not, today is the FIRST time Ive seen that. Ive spent 2.5 months searching, and I see that today. hrrrrmff!

B. (again :) )

](*,)

---

### Post by online14230 on 2007-01-17
Bumpity Bump :)

---

### Post by Jose Catre-Vandis on 2007-01-17
Try this:

[http://www.ubuntuforums.org/showthread.php?p=1995612#post1995612](http://www.ubuntuforums.org/showthread.php?p=1995612#post1995612)

---

### Post by Shatrat on 2007-01-17
I recommend doing what I did to solve the problem.
Eventually you reach a point where the amount of effort you are putting into the hardware is worth more than the hardware itself.  You can buy a used or just an older nVidia card like a 6600 gt or a 6800 on ebay for relatively little dough which will Demolish that card in windows gaming as well as linux, has more quality options, already supports compositing desktops like Compiz and Beryl, et cetera.  Hate to sound like an advertisement, but it's just about the best bang for the buck hardware upgrade I've had.

Im certainly glad I traded in my 9600 pro for a 6800, and I even could get my fglrx working.  Just make sure you get an AGP card and you're golden.

---

### Post by online14230 on 2007-01-18
Sorted! well, sort of...

Alls running well, all thanks to
[CENTER][SIZE="6"][/SIZE][/CENTER] ***_TSELLIOT, you POET YOU!!!_***
Thanks a million for starting that thread "post how you got your ATI card working" and thanks for being such a brilliant force in the Ubuntu community.
**_[CENTER][SIZE="7"]YOU ROCK!![/SIZE][/CENTER]_**
Back to how I got the drivers installed AND working...
See, first I got rid of all the old stuff I had lying around. I fired up synaptic and removed EVERYTHING related to ATYI, RADEON and FGLRX using the search function. Keep in mind that I have the repositories on disc...
I blacklisted fglrx by doing
/sudo gedit /etc/default/linux-restricted-modules-common
and adding fglrx between the empty quotes. theres a small howto right there in the file :)

Then, I made the debs.
bash ati-driver-installer-<version>.run --buildpkg Ubuntu/dapper

I installed them and then remembered to remove all the old debs from /usr/src
sudo rm /usr/src/fglrx*.deb

Then its kernel module compile time with
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

And alls good. Till this point, I already knew it like the back of my hand, since Id done it so many times... but I ALWAYS messed up with the xorg.conf file. Take my advice: BEFORE YOU GO FURTHER< BACK IT UP!!!

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

BELIEVE ME, IF YOU DONT AND THINGS GO WRONG, YOU'LL WANNA CRY!!!

Now its time to mess with the settings:
sudo dpkg-reconfigure xserver-xorg
sudo aticonfig --force --initial
Since I had installed a very many drivers, I had to use the --force setting to get it to work. Yes, I did both. On my first try last night, I did the dpkg thing and it didnt work. Then I did the aticonfig thing and it didnt work. then I did both :)!!!

sudo aticonfig --Overlay-type=Xv <---- DONT FORGET THIS!!!!

This is where ALL the other how-to's tell you to reboot. If you do, you'll probably end up with a broken server. Before you reboot, do this:

You need to replace libGL.so.1.2 with an older version, which you can get from [http://www.groundimpact.com/libGL.so.1.2](http://www.groundimpact.com/libGL.so.1.2) . before you reboot, close ALL open programs and cross you fingers...
It didnt work for me on the first reboot, so I did this,which I found in one of the how-to's...
sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/

I rebooted, and VIOLA! glxgears reports 4997FPS... Carbon, HERE I COME!!!

Now I have but one problem:

The screen is too bright. I dropped the monitor settings right down and it was still to bright. So I was wondering... Since I had used ATITOOL to overclock the card, would that be a problem? Would the settings I use in WinXP be causing it? Seems not, since I uninstalled ATITOOL and reset the card. Screen still to bright.Yes, I had to figure out myself that XP settings cannot and dont affect Ubuntu settings. Please dont tell anybody I tried that!! Anyway, I then used the ATI panel in Ubuntu, and dropped the color setting right to the bottom, and still too bright. Lemme tell you how bright it is: I had all the lights off in the house, and my wife walked in to bring me coffee. She, incidentally, is beginning to love Ubuntu ... she asked me why I was using a WHITE DESKTOP. Lemme tell you: ITS TOO BRIGHT. Does ANYONE, I mean ANYONE, know how to adjust gamma/color settings in Ubuntu? I tried EVERY setting I could think of, and I cant find it. PLEASE HELP ME, Im gonna go blind!!!!

---

### Post by aktiwers on 2007-01-29
Hey I have the same card, and I am about to try what you just descriped.
I hope it works :)

Anyways, I know how to adjust the gamma settings in Ubuntu, but not perment. Fire up the Terminal and type:

```
xgamma -gamma 0.1
```

THIS will make your screen dark. The number at the end is what you need to change. 1 is normal (in your case TOO BRIGHT!), and 10 is VERY BRIGHT! 0.1 is the lowest you can pick. 
If this works, maybe someone knows how to make a startup-script that runs that command for you. Good Luck! Now Im gonna test this madness! Cross your fingers! :P

---

### Post by CowzRule on 2007-01-29
How to install the drivers from '[[color=red]**ati.amd.com**[/color]]("http://ati.amd.com/support/driver.html")' for [[color=blue]**Ubuntu Dapper Drake**[/color]]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually") and for [[color=blue]**Ubuntu Edgy Eft**[/color]]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_Driver_Manually").


:D

---

### Post by online14230 on 2007-01-30
OK Girls, Ive seen this problem on another post, and there was no solution to the problem there either. Setting the gamma via xgamma doesnt work. See, I set the monitor in XP and left it like that. I shutdown and booted up Dapper, and all hell broke loose. The screen, at bootup, which is a bright yellow under normal circumstances, was white, at a res of about 1520 x 768. xgamma DOES drop gamma, but at a setting of 0.1, its STILL too bright. Im lost here. The TVOUT seems to be ok, because the swatch I downloaded is perfect on the TV, but the monitor is too bright. Dropping it to 0.1 does nothing for me. What I need is some way to adjust contrast and brightness, which I can do with Catalyst in XP. I think ATI needs to seriously address these issues, because Im currently in the market for a new NVIDIA card. Incidentally, anyone know how to limit the framerate in Dapper? Need for Speed Carbon is giving me some SERIOUS problems. The game is way too fast. I play with a manual transmission normally, and I cant even control a car properly with auto box. I need help.

---

