---
title: "no movies on laptop -&gt; heading to windows"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by puuma2 on 2007-09-02
Please help, I have left linux 3 times as I struggle getting it to work, I am above average with Windows but this is doing my head in: 

I have an acer 2420 laptop with ubuntu installed, I have internet working and email, however I can not get downloaded Mpegs to play .. I think I have added all the extras to Mplayer but nothing helps, I have also added VLC player but all have same result as follows... 

Click on movie see 2 secs of movie then blank screen sound continues but no film. 

I am getting very confused when ppl try to help they speak above my ability I am serious about going back to windows, I do not know where terminals are etc

---

### Post by cypry on 2007-09-02
Maybe this can help:
[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by stoer on 2007-09-02
Hi,
before you give in totally, 
Don't forget that you need to install the correct codecs in windows to get playback aswell,  in ubuntu it's exactly the same.
Before trying Automatix, I would take a look at the following link for the reccomended approach.
All film formats work in linux, it's just a case of installing the right codecs...

---

### Post by PmDematagoda on 2007-09-02
Did you try playing any mpeg's found on the computer?

---

### Post by overdrank on 2007-09-02
> **puuma2 said:**
> Please help, I have left linux 3 times as I struggle getting it to work, I am above average with Windows but this is doing my head in: 

I have an acer 2420 laptop with ubuntu installed, I have internet working and email, however I can not get downloaded Mpegs to play .. I think I have added all the extras to Mplayer but nothing helps, I have also added VLC player but all have same result as follows... 

Click on movie see 2 secs of movie then blank screen sound continues but no film. 

I am getting very confused when ppl try to help they speak above my ability I am serious about going back to windows, I do not know where terminals are etc

Hi and welcome the terminal is located under applications, accessories, terminal. You may look at this links and they may help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
If you have more questions just ask. Good luck! :guitar:

---

### Post by Grimgoil on 2007-09-02
As said before, you need codec to play the videos, did you initially open the movies in the preinstalled totem Gstreamer, it automatically refers you to the coodec installer and all you need to do is check the 3 available codecs. after that VLC and other programs will work.

 I recommend sticking with Totem anyways, In windows you need to install one of those huge codec packs and you need to configure a whole lot of things once you want to watch an actual dvd in your drive. (that made me return to ubuntu after going back to windows with similar problems you have)

---

### Post by mysticmatrix on 2007-09-02
> **puuma2 said:**
> Please help, I have left linux 3 times as I struggle getting it to work, I am above average with Windows but this is doing my head in: 

I have an acer 2420 laptop with ubuntu installed, I have internet working and email, however I can not get downloaded Mpegs to play .. I think I have added all the extras to Mplayer but nothing helps, I have also added VLC player but all have same result as follows... 

Click on movie see 2 secs of movie then blank screen sound continues but no film. 

I am getting very confused when ppl try to help they speak above my ability I am serious about going back to windows, I do not know where terminals are etc

You are not using any Beryl/Compiz/Compiz Fusion/DEsktop Effects while trying to watch your videos, do you?

If switching off Compositing/Eye Candy makes you able to watch the video, then its problem in Effects(which have a known workaround), and not with VLC or Totem or Codecs

---

### Post by MenZa on 2007-09-02
Personally, I recommend you use VLC and download the codecs.

A whole set of (restricted) codecs can be downloaded with the following command:

```

sudo aptitude install gstreamer0.10-*

```

This will install lots and lots of codecs (including MPEG support), along with a bunch of documentation packages and so on for gstreamer.

If you're looking at installing support so that you can view DVDs, have a look at [Medibuntu](http://medibuntu.org).

---

### Post by PmDematagoda on 2007-09-02
Why don't you try Ubuntu Ultimate 1.4? It is Feisty Fawn with a lot of software preinstalled including codecs.

---

### Post by MenZa on 2007-09-02
> **PmDematagoda said:**
> Why don't you try Ubuntu Ultimate 1.4? It is Feisty Fawn with a lot of software preinstalled including codecs.

It's unnecessary. Everything is easily available by running a few commands in the "vanilla" Feisty.

---

### Post by Gone fishing on 2007-09-02
I know that there are so good objections to automatix, but I must admit that to get videos working, I just download automatix and let it install the video codecs etc and it just works.

---

### Post by MenZa on 2007-09-02
> **Gone fishing said:**
> I know that there are so good objections to automatix, but I must admit that to get videos working, I just download automatix and let it install the video codecs etc and it just works.

As I---and others---have stressed so many times, Automatix is a dangerous tool, and if something breaks while you use it, there's really nothing we can do to help you.

Think of using Automatix as "voiding your warranty". Automatix is just a quickly hacked-up package manager attempting to simplify certain tasks, and only doing half what it's supposed to.

Read the link in my footer and check out the [tutorials](http://ubuntu-tutorials.com/) over at [Ubuntu-Tutorials.com](http://ubuntu-tutorials.com/). They're intending on writing a How-To on how to do every single task manually that Automatix would do for you.

---

### Post by puuma2 on 2007-09-02
right thanks guys, I installed automatix, I have downloaded what I think should work I found how to work terminal, I can now see films and hear them but the quality is soooo poor they play great on windows but here its like a very poor quality you know like a poor copy or wrong driver,, any ideas ?? thanks for your help

---

### Post by overdrank on 2007-09-02
> **puuma2 said:**
> right thanks guys, I installed automatix, I have downloaded what I think should work I found how to work terminal, I can now see films and hear them but the quality is soooo poor they play great on windows but here its like a very poor quality you know like a poor copy or wrong driver,, any ideas ?? thanks for your help

Hi and what video card do you have? You can use the command lspci in the terminal and tell us.

---

### Post by puuma2 on 2007-09-02
It is a laptop so it is integrated, 
Notebook: Acer TravelMate 2420
Processor: Intel Celeron M 370 (1500 MHz)
Graphics adapter: Intel Graphics Media Accelerator 900 (128 MB)

Do not know what you meant by "you can use the command lspci in the terminal and tell us"

---

### Post by puuma2 on 2007-09-02
bash: Ispci: command not found
john@laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML
Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile
915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML
Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation
82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family)
AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface
Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6
Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family)
SMBus Controller (rev 03)
06:05.0 Ethernet controller: Atheros Communications, Inc. AR5005G
802.11abg NIC (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd.
RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
(rev 01)
john@laptop:~$

---

### Post by Gone fishing on 2007-09-02
If you are using beryl or compiz I suggest reloading metacity  

metacity --replace 

before trying to watch a film.

---

### Post by puuma2 on 2007-09-02
> **Gone fishing said:**
> If you are using beryl or compiz I suggest reloading metacity  

metacity --replace 

before trying to watch a film.

I do not know what I am using !!! sorry if I seem stupid I just loaded this today and it is all above my head, each reply brings frustration as I do not have the knowledge you guys have.
I do not know what beryl or compiz is

---

### Post by powershaker on 2007-09-02
Poor thing.  Why don't you give up on LINUX and WINDOWS all together, and install Mac OS X.  Save yourself some headaches.

---

### Post by Gone fishing on 2007-09-02
You will be using metacity the standard Window manager rather than the fancy 3D effects when you say poor quality is that sound or video? If it's video how poor, jerky?

---

### Post by overdrank on 2007-09-02
> **puuma2 said:**
> I do not know what I am using !!! sorry if I seem stupid I just loaded this today and it is all above my head, each reply brings frustration as I do not have the knowledge you guys have.
I do not know what beryl or compiz is

HI and no need to feel sorry for not knowing. If you don't know what beryl and compiz are then it is safe to say you don't have them installed.
Can you post the out put of this command in the terminal 
```
gksudo gedit /etc/X11/xorg.conf
```
And if you will use the code wrap text it will save space on the response. It is located at the top of the response window where the controls for the text are.

---

### Post by MenZa on 2007-09-02
> **overdrank said:**
> HI and no need to feel sorry for not knowing. If you don't know what beryl and compiz are then it is safe to say you don't have them installed.
Can you post the out put of this command in the terminal 
```
gksudo gedit /etc/X11/xorg.conf
```
And if you will use the code wrap text it will save space on the response. It is located at the top of the response window where the controls for the text are.

If you just want  the xorg.conf---why open it in gedit? Instead use *cat /etc/X11/xorg.conf*.

---

### Post by puuma2 on 2007-09-02
> **Gone fishing said:**
> You will be using metacity the standard Window manager rather than the fancy 3D effects when you say poor quality is that sound or video? If it's video how poor, jerky?

the video is poor it is like half the colors are missing, shadowy, etc

---

### Post by puuma2 on 2007-09-02
gksudo gedit /etc/X11/xorg.conf does not work tells me it is unsupported 

the second suggestion says no such directory

---

### Post by puuma2 on 2007-09-02
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
	Load	"i2c"
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
	Option		"XkbLayout"	"gb"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Gone fishing on 2007-09-02
Those should work are you using the right case  i.e. 

cat /etc/X11/xorg.conf
not 
cat /etc/X11/Xorg.conf
 
etc

---

### Post by puuma2 on 2007-09-02
c above got it to work thats the text not the video !!!
thanks by the way !! I feel as if my it skills have gone back 20 years.. have I got something wrong ?

---

### Post by overdrank on 2007-09-02
> **puuma2 said:**
> c above got it to work thats the text not the video !!!
thanks by the way !! I feel as if my it skills have gone back 20 years.. have I got something wrong ?

HI you may try this 
[http://ubuntuforums.org/showthread.php?t=540981&highlight=sudo+apt-get+install+xserver-xorg-video-intel](http://ubuntuforums.org/showthread.php?t=540981&highlight=sudo+apt-get+install+xserver-xorg-video-intel)
Good luck!

---

### Post by puuma2 on 2007-09-02
tried the intel thing, my config says I am using intel mobile drivers, .. the screen looks like you would get if you run windows on safe mode and tried to watch a film.. it is very white with hardly any colour

---

### Post by puuma2 on 2007-09-02
just rebooted machine and now videos are not working at all !!!!!!

soon as I click on video name it closes down player, how do I get it back ?

---

### Post by biosckon on 2007-09-02
try installing from repository VLC.

it'll appear in Applications->Sound&Video->VLC media player

launch it and to go "Settings->Preferences->Video->Output modules"
at the bottom right conner select "Advanced options"
this will display "video output module" selection
select "X11 video output"
click "Save"
close VLC

then right click on your video file and select "open with->vlc media player"

---

### Post by puuma2 on 2007-09-02
thank you, that got back my video ! 
now all I need is a way to stop the picture quality looking like a poor copy ! any ideas ??

---

### Post by biosckon on 2007-09-02
hi puuma2

sounds like you have problems with intel video driver
original video driver called: "xserver-xorg-video-i810" is not very good

try this one.

First remove old driver:
1. launch synaptic. goto System->Administration->Synaptic Package Manager
2. press Search and type 
```
video-i810
``` 
3. mark it for removal 
4. press Apply
5. close synaptic :)

Install new driver:
1. go to [http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943) 
and download file 
```
xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb
``` 
from the first post
2. this is installation package for new intel video driver. double click it. 
3. once installation is complete. launch terminal. Goto Applications->Accessories->Terminal
4. type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```
```
sudo gedit /etc/X11/xorg.conf
```
5. find the line that says:
```
Driver "i810"
```
change it to
```
Driver "intel"
```
"intel" all small letters
6. save file and close all open applications and restart X server by pressing ctrl+alt+backspace

well and pray it works :-) tell us how it went!
do not give up on ubuntu it is great linux distro and it has a very supportive community

---

### Post by biosckon on 2007-09-02
[COLOR="Red"]IMPORTANT before you uninstall old intel driver do this[/COLOR]
in the terminal window
1. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-i810
2. sudo gedit /etc/X11/xorg.conf
3. change
```
Driver "i810"
```
to 
```
Driver "vesa"
```
4. save changes and restart X server by pressing ctrl+alt+backspace

sorry did not think of it first

the screen will look a bit funky but as long as your GUI working you should be ok

---

### Post by puuma2 on 2007-09-03
Thank you !! the changes to the i810 to the new intel worked, I have choices in the resolution now.. 

faith may be back in Linux .. few years time I might be giving out advice.

---

