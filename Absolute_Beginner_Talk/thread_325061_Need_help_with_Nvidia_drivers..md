---
title: "Need help with Nvidia drivers."
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Zeddicus Zorander on 2006-12-24
I did do a search, but none of the results were all too helpful. I'm completely new to Linux and am trying to make the switch from Windows XP. Even if I manage to find possible answers, they usually imply that one has at least a basic understanding of how Linux works. I do not, so please go easy on me. ;)

So far I've managed to get Ubuntu 6.10 installed without any trouble (Live CD's are cool!). The first thing I did was set up my network options and Firefox. Great! Now I want to install the driver for my video card so that I can switch to 1920x1200 and not be permanently stuck at a resolution of 800x600. I've downloaded the file NVIDIA-Linux-x86-1.0-7184-pkg1.run and am having difficulty understanding the instructions in the [readme](http://download.nvidia.com/XFree86/Linux-x86/1.0-7184/README/readme.txt) they provide.

*Before beginning the driver installation, you should exit the X server. In addition you should set your default run level so you will boot to a vga console and not boot directly into X (please consult the documentation that came with your Linux distribution if you are unsure how to do this; this is normally done by modifying your /etc/inittab file).  This will make it easier to recover if there is a problem during the installation. After installing the driver you must edit your X config file before the newly installed driver will be used.  See the section below entitled EDITING YOUR X CONFIG FILE.*

1) How do I exit the X server?
2) How do I restart it again (just in case)?
3) How do I set the default run level? I can't find the /etc/inittab file!

[I]After you have downloaded NVIDIA-Linux-x86-1.0-7184-pkg1.run, begin installation by exiting X, cd'ing into the directory containing the downloaded file, and run:

sh NVIDIA-Linux-x86-1.0-7184-pkg1.run[/I]

4) The driver file is on my Desktop currently. I managed to run it (using terminal) and was told that I that the "nvidia-installer must be run as root". How do I do this?

Getting my video up and running is what has killed my enthusiasm for Linux in the past, because I always failed. With Vista due out soon I would like to try and get past this sticking point and perhaps actually make some real progress this time around learning how to make Ubuntu work for me rather than against me. Like I said, I'm a true blue noob when it comes to Linux.

Many thanks in advance all! :)

---

### Post by spockrock on 2006-12-24
first, its easier to use the repositories, unless you want the latestest nvidia driver, even then there are some but it seems you have a legacy card.

first open up synaptic, from the menu bar, system>administration>synaptic package manager

then settings>repositories.  from the ubuntu 6.10 tab, I suggest you check all the repositories, but make sure, you have the restricted repository enabled.

close, synaptic, open terminal, applications>accessories>terminal

then 
sudo apt-get update
sudo apt-get install nvidia-glx-legacy

it should install the needed dependencies

then open, your xorg, but first back it up, so
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf
```

then find the Driver "nv" line and change "nv" to "nvidia"
it should work but more can be found here.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-d3968a4d3bed6eeef4b10fd3202bcdf313b1e75d](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-d3968a4d3bed6eeef4b10fd3202bcdf313b1e75d)

---

### Post by FakeOutdoorsman on 2006-12-24
I have some suggestions that may be easier.  Ubuntuguide.org has some good instructions:
[How to install Graphics Driver (NVIDIA)]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")

Or you could try [EasyUbuntu]("http://easyubuntu.freecontrib.org/") which has an option to automatically install NVidia drivers (and many other useful things).

---

### Post by x1a4 on 2006-12-25
Hi,

I also want to install the latest Linux nVIDIA driver and know what to do, but not exactly how to do it on Ubuntu.  

Here's what I know:  

One must go down to a runlevel not running the GUI, then run the nVIDIA installer.  

Unfortunately, Ubuntu doesn't configure runlevels by default.  Earlier tonight I posted a message asking for a graphical runlevel editor so that I can edit my runlevels, before I can install the nVIDIA driver.  

I suggest you wait, and when I have a good graphical runlevel editor I'll post specific instructions after I've done it successfully.  

If you're in a hurry, here's what you do: 

1) Logout.
2) Hit Ctrl+Alt+F1
3) Login as root
4) Run 

init 3

5) You will not see a change since Ubuntu doesn't configure runlevels by default but you'll need to be in a runlevel other then 2 (Ubuntu default, or 0 and 6 as 0=halt, and 6=reboot)

6) Run

ps -A

to see all running processes.  If there are more processes than fits the screen run 

ps -A |more

5) Kill all processes associated with the GUI: 

kill -s 15 [process #]

You'll know the process number from the ps output.  

a) First kill your window manager (in my case it would be all processes starting with xfce followed by processes beginning with xfwm, as I'm running XUbuntu and hence my GUI is Xfce; if you're running Ubuntu and thus GNOME for your window manager your processes will be different, same for KUbuntu as it's running KDE) 

b) Second, kill your desktop manager (most likely gdm (GNOME Display Manager) or kdm (KDE display manager).  If you have Ubuntu or XUbuntu it'll be gdm.

c) Finally, kill Xorg.

6) Once the GUI is off, install the nVIDIA driver as per nVIDIA's instructions.  

7) Run

init 2

Your GUI should be up and running and you should briefly see the nVIDIA logo before the login screen.  

If that's too complicated for you I strongly recommend you wait a few days then send me an email at _x1a4 [at] acanac [dot] net_.  I should have an easy solution for you.  


A slightly easier way is to go down to runlevel 1 (though the nVIDIA Driver Installer will complain because runlevel 1 kills too many processes) and install it then.

Runlevel 1 is a very basic, single-user (root), no-GUI, command-line environment for emergency purposes only.  Caution should be taken when making system changes in runlevel 1.

---

### Post by Zeddicus Zorander on 2006-12-25
> **spockrock said:**
> first, its easier to use the repositories, unless you want the latestest nvidia driver, even then there are some but it seems you have a legacy card.

first open up synaptic, from the menu bar, system>administration>synaptic package manager

then settings>repositories.  from the ubuntu 6.10 tab, I suggest you check all the repositories, but make sure, you have the restricted repository enabled.

close, synaptic, open terminal, applications>accessories>terminal

then 
sudo apt-get update
sudo apt-get install nvidia-glx-legacy

it should install the needed dependencies

then open, your xorg, but first back it up, so
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf
```

then find the Driver "nv" line and change "nv" to "nvidia"
it should work but more can be found here.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-d3968a4d3bed6eeef4b10fd3202bcdf313b1e75d](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-d3968a4d3bed6eeef4b10fd3202bcdf313b1e75d)
I followed your instructions and it looks like the driver for my legacy video card is installed, at least it does based on what the xorg.conf looks like anyways. I'm not 100% sure though because I'm still limited to the three resolutions I had before. These are 1024x768, 800x600, and 640x480. After originally installing Ubuntu, the 1024x768 one wasn't functioning properly (right side of desktop went off screen), but seems to be working ok now after following your steps. Better than nothing I guess since 800x600 was hurting my eyes lol.

So, provided the driver actually is installed, how do I now force Ubuntu to let me use all my other resolutions, like 1920x1200 (native), 1440x900, 1280x800, and so forth? I'm used to having tons of desktop real estate and can't live without it.

Perhaps, if someone has the time and patience, they could please explain what some of these commands mean as well. For example, 'sudo' and 'apt-get'. I'm not even going to try and decipher that last post though because it totally lost me right off the bat. As someone whom is coming from (and trying to move away from) Windows, I must admit that it confuses me as to why one has to jump through so many hoops just to install a video driver.

Anyways, if you want the definition of "absolute beginner", for which this forum is so named, then look no farther than myself because that's definitely where I'm at lol. Thanks again everyone, your efforts are very much appreciated. ;)

---

### Post by spockrock on 2006-12-25
> **Zeddicus Zorander said:**
> I followed your instructions and it looks like the driver for my legacy video card is installed, at least it does based on what the xorg.conf looks like anyways. I'm not 100% sure though because I'm still limited to the three resolutions I had before. These are 1024x768, 800x600, and 640x480. After originally installing Ubuntu, the 1024x768 one wasn't functioning properly (right side of desktop went off screen), but seems to be working ok now after following your steps. Better than nothing I guess since 800x600 was hurting my eyes lol.

So, provided the driver actually is installed, how do I now force Ubuntu to let me use all my other resolutions, like 1920x1200 (native), 1440x900, 1280x800, and so forth? I'm used to having tons of desktop real estate and can't live without it.

Perhaps, if someone has the time and patience, they could please explain what some of these commands mean as well. For example, 'sudo' and 'apt-get'. I'm not even going to try and decipher that last post though because it totally lost me right off the bat. As someone whom is coming from (and trying to move away from) Windows, I must admit that it confuses me as to why one has to jump through so many hoops just to install a video driver.

Anyways, if you want the definition of "absolute beginner", for which this forum is so named, then look no farther than myself because that's definitely where I'm at lol. Thanks again everyone, your efforts are very much appreciated. ;)

right sorry ok this is a simple fix, open up your xorg.conf and in there there maybe a section like this

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"T910BU"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

right see where it says modes just add the desired resolution, "1920x1200", since my default depth is 24 I really only need to change the last part so it reads like this....you can add modes for the other bit depths but thats up to you.....


```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"T910BU"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

then in terminal just do 
sudo /etc/init.d/gdm restart

that should work if that fails, just remove that mode, and restart x.

---

### Post by Zeddicus Zorander on 2006-12-25
> **spockrock said:**
> right sorry ok this is a simple fix, open up your xorg.conf and in there there maybe a section like this
Hmm, based on intuition I had guessed as much. Unfortunately, despite my edits, Ubuntu still won't let me use any resolution other than the default ones. My monitor is a Dell 2405FPW. Could my problem have something to do with the fact that it is being listed as a generic monitor in the xorg.conf file?

> **spockrock said:**
> then in terminal just do 
sudo /etc/init.d/gdm restart

that should work if that fails, just remove that mode, and restart x.
Umm, my screen went black after using this command. How do I restart x? Is it safe to just hit the reset button? Hopefully I didn't kill anything lol.

---

### Post by spockrock on 2006-12-25
using google I have found what you have to do to get your 2405FPW working

```

Section "Monitor"
Identifier      "2405FPW&#8221;
DisplaySize	519 324
HorizSync	30-81
VertRefresh	56-76
Option		&#8220;DPMS&#8221;
Modeline	&#8220;1920×1200&#8243; 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

```

the important thing here is apparently the modeline, also if you change your identifier, your have to make appropriate changes through out your xorg.conf.

btw you can see his xorg.conf here [http://rdo.homelinux.org/~will/d610/xorg.conf](http://rdo.homelinux.org/~will/d610/xorg.conf)
from this site [http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/](http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/)

also if you screen went black and when you boot into ubuntu and the screen keeps going black, then from grub pick single user mode and correct your xorg.conf, meaning you can remove that mode that you just added.  If making changes to your xorg.conf seems too complicated, make the correction to your xorg.conf, get your X working again, come back here, and post your xorg.conf and I will help you setup your xorg.conf.

---

### Post by judgejudy on 2006-12-25
this howto worked for me [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Zeddicus Zorander on 2006-12-25
> **spockrock said:**
> using google I have found what you have to do to get your 2405FPW working
Thank you spockrock! For what it's worth, finding information isn't really a problem. Understanding it though, now that's a problem lol. As far as the blank screen I mentioned above, well a reboot did end up solving that. Whew! However I just successfully killed Ubuntu (permanently it looks like) with my second go at editing the xorg.conf file in order to add the modeline.

Please don't take this the wrong way, but I just don't see how so many folks can honestly believe that Linux is going to take over the world. I mean, I can see it being a success in the business market. After all, they have trained experts that are paid just to keep things running smoothly. But the average home user, and the Windows user in particular? They have only themselves to rely upon much of the time, and it's such a huge struggle to get Linux up and running correctly. They'll surely balk, and most likely run, at the first sign of trouble lol! I know I'm tempted.

I'm not a complete dunce, and I'm usually able to troubleshoot my own computer problems pretty well. Especially with the help of kind and friendly folk like those in this forum. But even I have limits and am starting to wonder if it's really worth all this effort. I mean, I really would love to be able do away with Windows altogether (Vista especially), and I know many Linux fans would love to see everyone else feel this way. But look at just the installation of a simple video driver! Everything that's been posted just in this thread, versus a simple double click on an exe file in Windows. Add to that the fact that I'm getting varying answers to my problem, serving only to confuse me even more (hey, I did say I'm a noob). I guess I have difficulty understanding why it has to be so much harder with Linux. I know part of it involves security in so far that the easiness with which things are done in Windows is part of the reason why it is so insecure. Sigh.

Sorry about that, but I just really needed to vent. Please don't take it the wrong way, I'm just frustrated is all. I'll do a clean Ubuntu install, get the legacy drivers installed via Synaptic since that seemed to work, and then post my xorg.conf file for you all to look at. Maybe someone will be able to look at it and point me towards the correct edit to add the modeline and what not.

Also, thanks again for your help and continued patience everyone. Especially you spockrock! It is very much appreciated, and I'm sorry if I've upset anyone with my venting. I'm sure I'll get this sorted out eventually, and then I'll be singing the praises of Linux to everyone out there just like the rest of you true believers. ;)

---

### Post by ZERO_SHIFT on 2006-12-25
I reccomend Automatix for getting the drivers.

---

### Post by spockrock on 2006-12-25
> **Zeddicus Zorander said:**
> Thank you spockrock! For what it's worth, finding information isn't really a problem. Understanding it though, now that's a problem lol. As far as the blank screen I mentioned above, well a reboot did end up solving that. Whew! However I just successfully killed Ubuntu (permanently it looks like) with my second go at editing the xorg.conf file in order to add the modeline.

Please don't take this the wrong way, but I just don't see how so many folks can honestly believe that Linux is going to take over the world. I mean, I can see it being a success in the business market. After all, they have trained experts that are paid just to keep things running smoothly. But the average home user, and the Windows user in particular? They have only themselves to rely upon much of the time, and it's such a huge struggle to get Linux up and running correctly. They'll surely balk, and most likely run, at the first sign of trouble lol! I know I'm tempted.

I'm not a complete dunce, and I'm usually able to troubleshoot my own computer problems pretty well. Especially with the help of kind and friendly folk like those in this forum. But even I have limits and am starting to wonder if it's really worth all this effort. I mean, I really would love to be able do away with Windows altogether (Vista especially), and I know many Linux fans would love to see everyone else feel this way. But look at just the installation of a simple video driver! Everything that's been posted just in this thread, versus a simple double click on an exe file in Windows. Add to that the fact that I'm getting varying answers to my problem, serving only to confuse me even more (hey, I did say I'm a noob). I guess I have difficulty understanding why it has to be so much harder with Linux. I know part of it involves security in so far that the easiness with which things are done in Windows is part of the reason why it is so insecure. Sigh.

Sorry about that, but I just really needed to vent. Please don't take it the wrong way, I'm just frustrated is all. I'll do a clean Ubuntu install, get the legacy drivers installed via Synaptic since that seemed to work, and then post my xorg.conf file for you all to look at. Maybe someone will be able to look at it and point me towards the correct edit to add the modeline and what not.

Also, thanks again for your help and continued patience everyone. Especially you spockrock! It is very much appreciated, and I'm sorry if I've upset anyone with my venting. I'm sure I'll get this sorted out eventually, and then I'll be singing the praises of Linux to everyone out there just like the rest of you true believers. ;)

No I completely agree, I know using xorg.conf can be archaic at first, it really does seem backwords, trust me thats how I felt setting up my dual monitor setup.  It can really getting frustrating, that being said, xorg.conf can be slightly more powerful, as you often can be limited by the gui, where as, a text config isn't but you do need to know whats going on.  That being said, the latest nvidia drivers (I am not sure if the legacy drivers have them) but the nvidia settings app, is great for those who find tinerking with xorg.conf archaic.  

Again when you bork your xorg.conf, you dont have to restart, if its bad, just boot into single user mode and if you followed my instructions and made a back up just restore the original xorg.conf.

good luck, I know it can be hard at first, but its worth it.  I agree though 100% xorg needs to make an easier way to do small things like this thats just flat out easier in windows.

---

### Post by Zeddicus Zorander on 2006-12-25
Alright, here are the steps I've done so far after reinstalling a fresh copy of Ubuntu 6.10, following primarily post number two in this thread by spockrock:

1) Check marked all repositories in Synaptic.
2) Hit the Reload button.
3) Let Synaptic update everything.
4) Rebooted PC,
5) Installed driver using 'sudo apt-get install nvidia-glx-legacy'
6) Backed up my xorg.conf file.
7) Changed nv to nvidia in xorg.conf file.
8) Rebooted PC.

Here is my xorg.conf file as it currently is. The information that's been given about modelines is very confusing, and I've already messed things up once now, so if someone would be so kind as to show me exactly what needs editing so that I can use all of the resolutions my monitor is capable of (especially 1920x1200), I would be most appreciative. Pretty please? Thank you!

```
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
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
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

```

---

### Post by spockrock on 2006-12-25
ok sorry I forgot to mention this, nvidia drivers dont use dri, so just copy and paste this section into your xorg.conf (gksudo gedit /etc/X11/xorg.conf) and I cant guarantee this will get your monitor working properly but hopefully it will.

```
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
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
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
        Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1024x768" "800x600" "640x480"
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

```
then sudo /etc/init.d/gdm restart
ok if that fails, gives you an x server error, but have a black screen with white text, then change your monitor section to look like the the secion below.....by (sudo nano /etc/X11/xorg.conf) if you get a black screen and your monitor turns off, then reboot, pick single user mode and edit then edit the xorg.conf file with (nano /etc/X11/xorg.conf)

```

Section "Monitor"
        Identifier      "Generic Monitor"
	DisplaySize	519 324
	HorizSync	30-81
	VertRefresh	56-76
	Option		"DPMS"
	Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

```

---

### Post by Zeddicus Zorander on 2006-12-26
Thanks for replying! Alright, first I tried using the command 'gksudo gedit /etc/X11/xorg.conf' and got the following error:

(gedit:4569): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

So instead I used 'sudo gedit /etc/X11/xorg.conf' to edit my xorg.conf file.

I followed your instructions and did a copy & paste of your first set of xorg.conf settings (the whole thing) overwriting all previous entires. When I rebooted, my options were sill limited to 1024x768 (60 Hz), 800x600 (60 Hz), and 640x480 (60 Hz).

Since that didn't work, I then tried your second set of edits. After a reboot, my options were changed to 1024x768 (60,72, and 75 Hz), 800x600 (60,72, and 75 Hz), 640x480 (60,72, and 75 Hz), 960x600 (60 Hz only), and 832x624 (60,72, and 75 Hz).

Going back to your first set of changes, I decided to try my own customization:

Modes		"1920x1200" "1280x1024" "1280x800" "1024x768" "800x600"

This is when I noticed something odd after rebooting. First off, the resolutions now available to me after my own edit included 1280x800 (60 Hz), 1024x768 (60 Hz), 800x600 (60 Hz), 1280x768 (60 Hz), and 640x480 (60 Hz), in that order. What was weirder is that when I chose either 1280x800 or 1280x768, my monitor reported that the real resolution it was being fed was 1024x768 and 1360x768 respectively. Selecting 800x600 or 640x480 were indeed 800x600 and 640x480 as reported by my monitor.

So there is definitely a huge discrepancy between what is in the xorg.conf file, what options you're shown when you select System>Preferences>Screen Resolution, and what is actually being sent to the monitor when you select one of the custom ones from the drop down menu.

I am at a loss as to what to do next. Being a noob sure doesn't help, especially since most of the tutorials out there only explain the steps involved in doing something, and not the why of it. Anyways, thanks again for all your help. ](*,)

---

### Post by spockrock on 2006-12-26
ok what happens when you use my first xorg but use this modeline??

Modeline "1920x1200"  154.128 1920 1968 2000 2080  1200 1203 1209 1235 -hsync -vsync


if that modeline doesnt work here is another....
Modeline "1920x1200"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync

and yet another modeline I have found
Modeline "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -VSync
this one is the same as the first but with +HSync and -VSync

---

### Post by Zeddicus Zorander on 2006-12-26
> **spockrock said:**
> ok what happens when you use my first xorg but use this modeline??

Modeline "1920x1200"  154.128 1920 1968 2000 2080  1200 1203 1209 1235 -hsync -vsync


if that modeline doesnt work here is another....
Modeline "1920x1200"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync

and yet another modeline I have found
Modeline "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -VSync
this one is the same as the first but with +HSync and -VSync
Alright, I did exactly as you asked and tried each of those modelines. In each case I was still limited to 1024x768 (60 Hz), 800x600 (60 Hz), and 640x480 (60 Hz) as my only choices. For what it's worth, I'm now positive that the legacy video drivers are indeed installed, as there is an Nvidia splash screen which pops up for a split second during boot. Lot's of people have LCD monitors these days, and most have a high native resolution. I just don't understand why this continues to be such a difficult issue with Linux. Even so, somehow a few smart (lucky?) 2405FPW users are managing to make everything work as it should, so there must be something we're simply overlooking here.

Sorry for taking up so much of your time with this. Honestly, I'm just not making much headway with learning Linux. I'm not dumb (I hope), but it's starting to feel like Linux is just way too over my big fat noob head for me to really understand. I do not relish the idea of being forced to upgrade to Vista one day though, when XP can no longer hold it's own and do what is needed, but it is looking more and more like I will not have a choice. I really wanted to avoid that, hence why I'm trying really hard this time. Sigh, this is actually my third go at Linux over the past year and a half, and I always get stuck at this particular sticking point. I fear that if I fail again this time around, I may never give Linux the benefit of the doubt again. The negative emotions are just too taxing.

](*,) :confused: ](*,) :confused: ](*,)

---

### Post by apedeaux on 2006-12-27
Hey Zed, I am in *exactly* the same situation as you.  I tried Ubuntu about half a year ago, and pretty much the only thing I could ever get to work was my network card.  The video card issue was what make me abandon it and head back to Windows with my tail between my legs.
I just got a new hard drive (merry xmas!), so I figured I would move WIndows to my new huge fast drive and put Linux on the old one to give it another shot.  
Last night I got Ubuntu installed, and started trying to get the drivers to work.  I must say, the new 6.10 version apparently has native support for Netgear wireless cards! I remember slogging through ndiswrapper guides for hours last time, so that was a pleasant surprise.  So I had hoped that the nvidia drivers would be easier as well.  It seemed like it went smoothy, I could tell 3d acceleration was on because I could drag windows around a lot faster, and I could scroll text faster (wow, not having a graphics card is rough!)  But I could not get any high resolution setting to come up in my GUI display options, just like you.

I have the same sentiment as you:  how on earth are people supposed to be able to switch over to this from Windows?  I mean, I'm a pretty computer literate kind of guy, I can usually get anything to work in Windows, but Linux seems incredibly difficult.  And most of the times that I do get stuff to work, it's not cause I figured out work to do it, it's cause I typed in a series of arcane commands that I find online, not because I know what the commands are doing. The folks on these forums are *extremely* nice and helpful, but I need to know what I'm doing, not just monkey-typing commands.

Anyway, I'm gonna be watching this thread because I'm going through the same thing, with the video card in particular but also with the overall Linux frustration.  I'm gonna go play around with it some more and check back later.

---

### Post by spockrock on 2006-12-27
> **Zeddicus Zorander said:**
> Alright, I did exactly as you asked and tried each of those modelines. In each case I was still limited to 1024x768 (60 Hz), 800x600 (60 Hz), and 640x480 (60 Hz) as my only choices. For what it's worth, I'm now positive that the legacy video drivers are indeed installed, as there is an Nvidia splash screen which pops up for a split second during boot. Lot's of people have LCD monitors these days, and most have a high native resolution. I just don't understand why this continues to be such a difficult issue with Linux. Even so, somehow a few smart (lucky?) 2405FPW users are managing to make everything work as it should, so there must be something we're simply overlooking here.

Sorry for taking up so much of your time with this. Honestly, I'm just not making much headway with learning Linux. I'm not dumb (I hope), but it's starting to feel like Linux is just way too over my big fat noob head for me to really understand. I do not relish the idea of being forced to upgrade to Vista one day though, when XP can no longer hold it's own and do what is needed, but it is looking more and more like I will not have a choice. I really wanted to avoid that, hence why I'm trying really hard this time. Sigh, this is actually my third go at Linux over the past year and a half, and I always get stuck at this particular sticking point. I fear that if I fail again this time around, I may never give Linux the benefit of the doubt again. The negative emotions are just too taxing.

](*,) :confused: ](*,) :confused: ](*,)

sorry silly question but you are restarting after you edit your xorg.conf files after you modify your xorg.conf

if not restart, ctrl-alt-backspace, or sudo /etc/init.d/gdm restart the least

---

### Post by x1a4 on 2007-01-08
Okay I figured it out, at least on my pc.  

On your keyboard press 

Ctrl+Alt+F1

At the login prompt type your username and hit enter, then your password and hit enter.  

With super-user priviledges kill your GUI: 

sudo kill -TERM | cat /var/run/gdm.pid

Using a text editor like nano or vim, open the file /etc/default/linux-restricted-modules-common like so: 

sudo nano /etc/default/linux-restricted-modules-common

and add "nv" to DISABLED_MODULES like so: 

DISABLED_MODULES="nv"

This will prevent "nv" from loading at boot time.  
("nv" is a generic Nvidia driver without 3D support)

Install the Nvidia driver: 

sudo sh /<driver_download_dir>/NVIDIA-Linux-x86-1.0-9629-pkg1.run
(where <driver_download_dir> is the directory you downloaded the driver to)

Confirm that the driver in the Device section of /etc/X11/xorg.conf is set to nvidia and not nv.

sudo nano /etc/X11/xorg.conf

Should look something like this: 
Section "Device"
    Identifier     "NVIDIA Corporation <your_card_here>"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
EndSection

When the driver is nvidia and not nv restart gdm: 

sudo /etc/init.d/gdm restart

This should work.  Good luck.

---

### Post by scj on 2007-01-08
I think there is a potential problem in your "Monitor" section of xorg.conf.  Earlier on you stated that you have a Dell 2405FPW which (according to the website I googled) has a HorizSync 30-81 and a VertRefresh 56-76.

(try this without the modeline at first (tell the computer to ignore it by placing a # in front of it) and if that fails put it back in)

One very important feature of these settings is to tell X what resolutions your monitor is capable of displaying.  Which fits your problem.

When I first started using Linux it took me hours to figure out how to configure xorg.conf properly (I wanted to use dual-monitors), and it almost turned me off Linux completely.  But the nice thing about being able to configure your video server using text is that _if_ something goes wrong you can fix it!  Another thing that I should add is that xorg.conf is one of the files I ensure to back up, and I recommend that you do the same.

I hope this helps!

---

### Post by harmeet on 2007-01-08
It is silly. How everyone has their own way of booting to command line without X runnning. It used to be so easy with inittab. I am still to find a similar way of doing it in ubuntu edgy. Here is what I did while installing nvidia drivers -

Press Alt+Ctrl+F1 and login as root, then do following -

```
mv /etc/gdm /etc/h-gdm
shutdown -r now
```

When it was restarted, I did the install, edited the xorg.conf file, tested the X sessions, then I renamed the h-gdm back to gdm and restarted.

> **x1a4 said:**
> Okay I figured it out, at least on my pc.  

On your keyboard press 

Ctrl+Alt+F1

At the login prompt type your username and hit enter, then your password and hit enter.  

With super-user priviledges kill your GUI: 

sudo kill -TERM | cat /var/run/gdm.pid

Using a text editor like nano or vim, open the file /etc/default/linux-restricted-modules-common like so: 

sudo nano /etc/default/linux-restricted-modules-common

and add "nv" to DISABLED_MODULES like so: 

DISABLED_MODULES="nv"

This will prevent "nv" from loading at boot time.  
("nv" is a generic Nvidia driver without 3D support)

Install the Nvidia driver: 

sudo sh /<driver_download_dir>/NVIDIA-Linux-x86-1.0-9629-pkg1.run
(where <driver_download_dir> is the directory you downloaded the driver to)

Confirm that the driver in the Device section of /etc/X11/xorg.conf is set to nvidia and not nv.

sudo nano /etc/X11/xorg.conf

Should look something like this: 
Section "Device"
    Identifier     "NVIDIA Corporation <your_card_here>"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
EndSection

When the driver is nvidia and not nv restart gdm: 

sudo /etc/init.d/gdm restart

This should work.  Good luck.

---

