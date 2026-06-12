---
title: "nvidia driver installer mess - cant start ubuntu"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Knacker on 2008-03-29
I've been frustrated by really sluggish performance from firefox (since I started using compiz and emerald theme) for a while and was led by various forums to try updating my nvidia drivers. I ran the nvidia driver installer and rebooted and now I get a message saying it's going to boot in low graphics mode, then it just stalls on a dark screen...nothing. I watched the nvidia installer back things up as it made changes, but I don't know how to recover everything. Here's what I did before everything went wrong: 

Ctrl+Alt+F1
sudo /etc/init.d/gdm stop
cd Desktop
sudo sh NVIDIA-Linux-x86-171.06-pkg1.run
[went through all the screens of the installer, including getting the nvidia configuration tool to set up my settings so that the driver would load when I rebooted]
sudo reboot

I feel like an idiot for messing with this, but I am being driven mad by the slow slow opera + firefox tabbing. Please tell me there's an easy way to fix this. Thank you so much in advance!

---

### Post by Knacker on 2008-03-29
please forgive me also if I don't reply really quickly, I have to go to work and will only be able to check the forums on my break. thank you again for any help you can spare!

---

### Post by mrpixels0 on 2008-03-29
Hi there Knacker

if the Nvidia drvier is installed and you can only login to the command line without the GDM (Gnome Desktop) then do this:

sudo dpkg-reconfigure -phigh xserver-xorg

This will allow you to setup your video driver and monitor resolution(s) to one that is in range instead of "out of range".

This has happened to me before when I enabled restricted drivers for the Binary from Nvidia instead of using the open driver that is used by default.

on resolution make sure that the max it is set for is supported by your monitor, for Example my max res is 1280 x 1024 but I use 1024 x 768 as this is not so small I cannot read the Icon test :).

once this is done you can use the Gnome tools to tweak it a bit more to your liking.

I hope this helps you out.

MP0

---

### Post by Knacker on 2008-03-29
Thank you so much for you help! I'll try this. :)

---

### Post by Nythain on 2008-03-29
also, just to help us get a little more familiar with your system, any way you can post the results of
cat /etc/X11/xorg.conf

and possibly the output/result/errors if/when you try to run
sudo /etc/init.d/gdm restart

would help to see what exactly is keeping x from loading

---

### Post by Knacker on 2008-03-29
well, i've tried a couple of things. 
first, i tried 
sudo dpkg-reconfigure -phigh xserver-xorg
and i got more blanks screen. i checked my nvidia-settings and it told me (not sure of exact message/wording) that nvidia xconfiguration was not running and that i should run nvidia-xconfig from root and restart. I did that but nothing seemed to happen when i ran nvidia-xconfig.
i've had problems with xorg.conf before, so i tried using one of the backup xorg.conf in etc/X11/; this gave me the got me to low res mode.  
so, then, from recovery mode, i tried manual reconfiguration: 
dpkg-reconfigure  xserver-xorg (I've done this before)
which landed me back at the blank screen. 
so, i'm back with the backup xorg.conf and things are working but in low-res mode

here is the stuff you asked for: 
the errors when I run sudo /etc/init.d/gdm restart: 

Starting anac(h)ronistic cron: anacron deferred while on battery power..
Starting deferred execution scheduler: atd
Starting periodic command schduler: crond
Enabling additional executable binary formats: binfmt-support
Checking battery state....
Running local boot scritps (etc/rc.local).
[then it just sits there...]

My xorg.conf file (the one that works in low-res mode): 

xorg.conf 
Section "Files"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"nVidia Corporation G80 [Quadro NVS 140M]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"UseFBDev"	"true"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
 
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection
 
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [Quadro NVS 140M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x900"	"1024x768"
	EndSubSection
EndSection
 
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by Knacker on 2008-03-29
oh man, this sucks. 
:confused:
kind and generous people of the ubuntu forums, please help me!

---

### Post by Nythain on 2008-03-29
man, only suggestion i have left at this time is to try running the nvidia installer again, see if it fixes itself by re-installing the drivers... wich im sure isnt the problem, but its about all i got at this point...

---

### Post by Nythain on 2008-03-29
oh yeah, there's an xorg error log somewhere i cant remember off teh top of my head, if someone out there could point the user in teh direction of that we might be able to get a better idea of whats stopping x from loading

---

### Post by Knacker on 2008-03-29
doesn't sound like you're too hopeful, but I'll try that. thanks for your help again. 
is there some way for me to get the attention of someone who knows this problem really well? (not doubting your ability, but you sound like you're at a loss for suggestions).
...and the only thing I really understand is that I'm pretty good at screwing this up...

is it possible that I'm installing the drivers improperly? all I did was download the installer from nvidia page and do as I wrote in my first post. is that correct? 
is it possible to download the wrong installer for my video card? sorry if these are dumb questions...i have no idea what I'm doing. 
will let you know if re-installing fixes the problem. 
thanks once more.

---

### Post by bumanie on 2008-03-29
Might sound silly, but are you trying to use the correct driver for your video card? If your card is an older model, they won't always work with the latest driver. What video card do you have?

---

### Post by Knacker on 2008-03-29
This is definitely not a silly question - I REALLY don't know what I'm doing. I have a Nvidia Quadro NVS 140m. My understanding was that the nvidia driver was generic and covered all their recent cards, but what do I know...this may not even be a recent card (though it did ship with my relatively new thinkpad t61 (less than 3months old). 
Does this clarify anything for anyone? 

I'm not sure about this, but I think the xorg.conf file that I'm using doesn't even use the restricted driver (it lists driver as nvidia, not nv...am I right?). If I configure xorg.conf and select nv as driver I can't get to login screen....

thanks again for your help, folks!!

---

### Post by bumanie on 2008-03-29
Go to here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) 
and choose 'automatically find a driver for your NVIDIA products'.
Hope it works.
PS: I searched nvidia linux for your card it came it with no matches, that's why you should try the 'automatically find a driver for your NVIDIA products'. If the card is that new, may be there is linux yet. Did the generic ubuntu drier work? If so, may be you should return to that.

---

### Post by Knacker on 2008-03-29
I looked at that page ages ago and didn't find my card. it's not there or it's called something else that I don't recognize. 

I've tried reinstalling the driver, I've tried installing an older driver (version 169.12). Neither had any effect. I tried disabiling and re-enabling restricted driver through restricted driver manager...I don't understand the relationship between these things (what is the difference or relationship between the restricted driver nvidia-glx-new that ubuntu gets and the driver that I downloaded + installed from nvidia web-site?) 

I'd love to return to the way things were. That's really all I want to do. Can someone please give me a step by step to return things to the normal driver set-up that I had when i just clicked enable in restricted driver manager? I know there are other slightly related how-to's out there, but they're all just a bit different and end up making things worse. 

The more I try to fix this myself, the worse it's going to get...what do I do? How do I undo everything? When I try to configure my xorg.conf I get a black screen. 

Thanks so much for all your help! Really grateful you guys are around.

---

### Post by Knacker on 2008-03-29
oh, and the automatically find card on the nvidia page doesn't work with linux. only windows...

---

### Post by Knacker on 2008-03-29
Okay, I've fixed it, I think. :)

I think the problem was that the ubuntu restricted (nvidia-glx) drivers were conflicting somehow with the driver i'd downloaded from nvidia. I more or less followed this how-to exactly: 
[http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/](http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/)

In case anyone ever cares, here's what I did: 

1. sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

2. sudo apt-get remove --purge nvidia-glx

3. sudo gedit /etc/default/linux-restricted-modules-common
> add the following code and save: DISABLED_MODULES="nv"

4. reboot

5. ctrl+alt+F1

6. sudo /etc/init.d/gdm stop 

7. sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
> followed prompts (accept license, yes to let installer compile custom, yes to change configuration [xorg.conf file]) [I got some errors re: a couple of things missing and etc. which I'll have to deal with at some point, I'm sure.] 

8. reboot

all looks to be well.

thanks so much to you guys for your suggestions, sympathy and ideas. these things drive me crazy, but very SLOWLY i learn. 
Anyway, again, thanks!
:)

---

### Post by interdaemon on 2008-04-01
The X server error log is:

/var/log/Xorg.0.log

What video card are you having difficulties with?

---

