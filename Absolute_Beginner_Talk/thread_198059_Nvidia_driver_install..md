---
title: "Nvidia driver install."
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by yavez on 2006-06-16
I think I've followed every guide there is by now in my quest to get my Nvidia Geforce 6200 card to work.

Every single time I try, with every different method I'm met with either a black screen or a big blue screen that tells me X could not be started.

This is the last guide I used: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

The official guide, and still the same problem.  I followed this guide to the letter and after the BSOX (Blue Screen of X) I logged into a recovery console and did sudo pico /etc/X11/xorg.conf to see what was happening.  Well, I was greeted with this mess below:  


Section "Device"

           Identifier      "ATI Technologies, Inc. Radeon RV100 [Radeon7000/Ve$
           Driver          "nvidia"
           Option         "DPMS"
           HorizSync     "28-51"

So, as advised I ran sudo dpkg-reconfigure xserver-xorg from the recovery console.  And now X doesn't crash out, I just get a black screen.

Here's the section Device from the dpkg-reconfigure:

Section "Device"

           Identifier      "NVIDIA corporation NV40"
           Driver          "nvidia"
           BusIKD         "PCI:1:0:0"
           Option         "UseFBDev"

What can I do to get my NVIDIA card working?  Anybody know why I'm having so much trouble, even with the offical guides?  I don't fancy recompiling kernels or anything like that.

---

### Post by rattking on 2006-06-16
Hello I have the same card working fine
first i would try commenting out the line Option "UseFBDev" with a # like so
#Option "UseFBDev"
and change BusIKD "PCI:1:0:0" to
BusID "PCI:1:0:0"
then restart X with the command
sudo /etc/init.d/gdm restart
if you use gnome (ubuntu)
sudo /etc/init.d/kdm restart
for kde (kubuntu)
if that doesnt do it lets make sure the nvidia kernel module is loaded 
sudo modprobe nvidia
and restart X
let me know if that does it

---

### Post by sumadartson on 2006-06-16
Correction, should read before posting.

One question...
```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon RV100 [Radeon7000/Ve$
Driver "nvidia"
Option "DPMS"
HorizSync "28-51"
```

Why does this say that it's an ati card. What does your lspci say?

---

### Post by yavez on 2006-06-16
It is an NVIDIA card.  I have it running fine both in Windows and using the Kororra live cd, and on a previous install of PCLOS.

The weird ATI listing in the xorg.conf was there after I followed the offical guide here: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Don't ask me how it got there, as I didnt edit the config at all.

The BusIkd was just a typo, as I was typing on a laptop what was appearing on the screen as I read it, sorry.

I'll give your suggestions a try and reprot back.  I won't let this beat me.

---

### Post by sumadartson on 2006-06-16
Yeah, sorry 'bout that. See post, I edited it. Wasn't exactly paying attention :sad: .

---

### Post by brentoboy on 2006-06-16
breezy or dapper?

---

### Post by yavez on 2006-06-16
Both linux-restricted-modules-2.6.15-3.386 and nvidia-glx are installed as per the official guide

I've just reinstalled them just in case.

I've activated nvidia with the command sudo nvidia-glx-config enable

I've just checked the xorg.conf before I do what you suggested and it reads like  this:

Section "Device"
           Identifier    "NVIDIA Corportaion NV40? [Unknown nVidia Card]
           Driver        "nvidia"
           BusID        "PCI:1:0:0"

Going to restart now.  Fingers crossed :)

EDIT: I'm on Dapper.  Weird, NVIDIA worked fine on Breezy for me.  This is also a clean install, only the required updates have been installed and nothing else.

---

### Post by yavez on 2006-06-16
Okay, so its still the same.

After restarting with sudo /etc/init.d/gdm restart I'm greeted with a text prompt to login.

I login and try to restartx and I'm met with a completely black screen, no activity behind it, nothing.

This is driving me nutso!:confused: :confused: :confused:

---

### Post by sumadartson on 2006-06-16
Can you post a) your xorg.conf, b) the last bit of /var/log/Xorg.0.log and c) the output of lispci?

---

### Post by yavez on 2006-06-16
I can try... I'm not sure how I can do it from a recovery console.. but I've got the windows (spit) laptop here and I'll type it in.

---

### Post by yavez on 2006-06-16
[QUOTE=yavez]I can try... I'm not sure how I can do it from a recovery console.. but I've got the windows (spit) laptop here and I'll type it in.[/QUOTE]

Edit: actually that's going to be near to impossible, how freaking long are these things?  Is there anything specific I should be looking for?

---

### Post by sumadartson on 2006-06-16
Hehehe... that's actually quite true.

Do you have shared diskspace, or a usb-stick you can use to copy the files to?

The output of lspci can redirected to a file by using

```
lspci > stuff.it.in.this.file.txt
```

The "lspci" is your command, ">" directs it to a file. Namely "stuff.it.in.this.file.txt", in this case.

The other two files can be copied.

---

### Post by yavez on 2006-06-16
I've got a usb stick...and okay, any ideas where that would be mounted through the recovery console?  And would I just cp the other two files over to the same location?

Thanks for the help by the way.  I really want to spend more time in Linux and not be reliant on Windows.

---

### Post by sumadartson on 2006-06-16
```

Thanks for the help by the way. I really want to spend more time in Linux and not be reliant on Windows.
```

Hey, don't thank me yet. I'm not even sure if I can really help you :D

There are instructions on how to manually mount a usb stick somewhere. Lemme check...

```
pmount /dev/sda1
```

And your device should than be mounted in on /media/sda1 .

---

### Post by yavez on 2006-06-16
mount: wrong fs type, bad option, bad superblock on /dev/sdd1 (that's where it showed up when I plugged it in)  missing codepage or other erorr

Man, this install really is screwing with me something rotten!

My /dev/sda1 is where I have Ubuntu mounted (its a SATA hard drive)

---

### Post by sumadartson on 2006-06-16
Just copy the files the location where your usb-stick is mounted.

Tip : there are two things that will really help you in figuring stuff out. The first are man pages. Just type 

```
man command
```

For a certain command, and it will give you a guide to that particular command. For pmount, you would type

```
man pmount
```

The other is the apropos command. If you know nothing about a subject, go

```
apropos term
```

For (hopefully) relevant commands. In your case... try for instance

```
apropos mount
```

---

### Post by yavez on 2006-06-16
Okay, I managed to get all three files off by manually mounting the usb stick.

Here's the xorg.conf:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"gb"
	Option		"XkbOptions"	"gb"
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
	Identifier	"NVIDIA Corporation NV40? [Unknown nVidia Card]"
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
	Device		"NVIDIA Corporation NV40? [Unknown nVidia Card]"
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


and the result of the lspci:

> 0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
0000:00:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
0000:00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:00:09.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)


The Xorg.0.log is massive, which part would you like me to post?

---

### Post by sumadartson on 2006-06-16
Hmmm... I don't have a quick solution for that.

According to [https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/26338](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/26338)

It seems to be related to adding/removing users on your system, oddly enough.

Perhaps an oldfashioned mount will accept it?

That is... (if I'm correct, google it otherwise)

```
mount -t vfat /dev/sdd1 /media/somedirectory
```

---

### Post by sumadartson on 2006-06-16
Hahahaha... nice timing! :D

---

### Post by yavez on 2006-06-16
LOL.  Yeah, that's what I figured out.. eventually.  Man, the more you learn the more you forget :)

---

### Post by sumadartson on 2006-06-16
The odd thing is, I can't find anything wrong with your lspci, or with your xorg.conf.

Have you scanned the last part of your Xorg.0.log for obvious error reports? Just go

```
less /var/log/Xorg.0.log
``` and see if you can make any sense of what it says...

I have to admit... I'm confused about this as well... Your config seems fine at first glance.

---

### Post by yavez on 2006-06-16
I'm getting a lot of (hysnc out of range) and (vrefresh out of range) and 
Error opening /dev/wacom : No such file or diretcory
(EE) xf86OpenSerial : Cannot open device /dev/wacom
                 no such fie or directory

But I've got my wacom tablet unplugged.

Damn it all to hell! (In Charlton Heston voice)

---

### Post by rattking on 2006-06-16
I see in your lspci output
Advanced Micro Devices [AMD] K8 [Athlon64/Opteron]
and in an earlier post you mentioned installing 
linux-restricted-modules-2.6.15-23-386
are you sure that your running the 386 kernel?
uname -r
will print the kernel version your running
I am not even sure what kernel 64bit machines use.. maybe installing the k7 kernel will help? but thats just a guess

---

### Post by yavez on 2006-06-16
uname -r output:

2.6.15-25-386

---

### Post by sumadartson on 2006-06-16
Hmmm... In addition to the kernel stuff...

The wacom stuff should not be a problem. However, the vertsync stuff does seem serious. 

What kind of monitor do you have? And does its manual say anything about refresh rates? To compare, I have two cheap crts with the following config: 

```

Section "Monitor"
        Identifier   "PHILIPS 107T 1"
        HorizSync    30.0 - 60.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
EndSection

```

In comparison, your refresh rates seem very low and your monitor isn't named by type.

---

### Post by yavez on 2006-06-16
It's a Goodmans 17" TFT, don't have the manual.  I'm going to try and set the refresh rates to something more sane, and see if that helps.

Set them in line with your settings above, and I still get the black screen, no activity.

This is definitely going to drive me insane.

On another note, sudo modprobe nvidia gives me no output at all.   I can't figure any of this out at all.

---

### Post by sumadartson on 2006-06-16
lsmod doesn't show you anything either?

Hmmm...

---

### Post by yavez on 2006-06-16
After running less /var/log/Xorg.0.log again I noticed a this:

(WW) NV(0) : Bad V_BIOS Checksum

If this is a major thing then why do both Korrora live cd and PCLinuxos work fine with Nvidia drivers?

I'm not seeing anything I shouldn't in lsmod output

What I don't get is how easy this was to accomplish on both Hoary and Breezy.  It was a simple five minute job, just follow the guide and it worked (same video card, same hardware).  I'm at about the point now where I'm wondering if i shouldn't use Kororra (and then I think I'd have to deal with Gentoo as a base and that's just going to be a whole lot harder than apt-get and .debs)

---

### Post by yavez on 2006-06-16
Okay, so here's the xorg.conf file from the Kororra live cd I ran (worked flawlessly with nvidia and full xgl effects)

Xorg.conf

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (root@goliath32)  Wed Mar 15 06:44:49 Local time zone must be set--see zic manual page 2006

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath         "/usr/share/X11/rgb"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/misc"
    FontPath        "/usr/share/fonts/75dpi"
    FontPath        "/usr/share/fonts/100dpi"
    FontPath        "/usr/share/fonts/TTF"
    FontPath        "/usr/share/fonts/Type1"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
    Load           "record"
    Load           "xtrap"
    Load           "freetype"
    Load           "type1"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/mouse"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
DefaultColorDepth 24
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection


Anybody notice anything that might be applicable from this to my own xorg.conf (i'm quite new to editing config files as a whole)

---

### Post by rattking on 2006-06-16
i google around a bit and ati users seem to have that same problem with 
Load "dri"
enabled in Section "Module"
nvidia cant use dri anyways and  its not in the working live distro so try commenting it out

---

### Post by yavez on 2006-06-16
Same result with DRI commented out.

I googled those solutions earlier as well, before I posted here.  This time I'm beat.

Well I give up (throws hands in the air).. I just haven't got the time to work through this anymore and I think I've already pushed the limits of people's patience in this thread. 

Thanks everyone for your help.  If I ever figure this out I'll be sure and come back to post the outcome.

Happy Linuxing :)

EDIT:  I'm going to install PCLINUXOS and see just exactly how the xorg.conf is setup in that.

---

### Post by rattking on 2006-06-16
i would be interested to know if Kororra or PCLINUXOS are using a 386, 686, k7, or k8 kernel when it does work

---

### Post by yavez on 2006-06-16
I'm about 10 minutes away from the download of PCLINUXOS (couldn't find the one I already had).  I'll report back when I get it running.

---

### Post by yavez on 2006-06-16
Just booted PCLINUXOS which was fine only two months ago.  Now i'm met with a black screen on that before I can even log in.   Linux is turning against me, I know it, the penguins are ganging up on me :)

EDIT: I can boot into it if I use the cheatcode livecd xdrv=nv, which corresponds to the stock install of Ubuntu when nv is used instead of nvidia.  What is it about Linux and binary video drivers that screws thing so much?  There must be a more eloquent solution than all these cheat codes and hand-editing of config files.

Screw it, I'm buyin a mac :)

---

### Post by sumadartson on 2006-06-17
> Screw it, I'm buyin a mac 

You do know you can run linux on those, don't you? :D

By the way, I was wondering... If you do a 
```
dpkg-reconfigure xserver-xorg
```
Do you get a working X again?

Backup your current Xorg first!

---

### Post by tseliot on 2006-06-17
Please, try my guide and read also the problems section and/or try my script:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by u.b.u.n.t.u on 2006-06-17
I just did a fresh install of ubuntu. I entered this code in the terminal.

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

I rebooted and had 3D.

---

### Post by yavez on 2006-06-18
Fresh install, took out the SATA drive just incase that had something to do with it (I had ubuntu booting off that).  Did as U.B.U.N.T.U said and what do you know...nothing happened.  No NVIDIA splash screen, nothing.  God, I really don't want to buy a mac, but the penguins are making me do it :)

So I remembered sudo nvidia-glx-config enable.  I did that, rebooted, and et voila... bugger all working.. another black screen... I just don't get it.  What's changed in Dapper that would make it all go wrong?

---

### Post by tseliot on 2006-06-20
[QUOTE=yavez]Fresh install, took out the SATA drive just incase that had something to do with it (I had ubuntu booting off that).  Did as U.B.U.N.T.U said and what do you know...nothing happened.  No NVIDIA splash screen, nothing.  God, I really don't want to buy a mac, but the penguins are making me do it :)

So I remembered sudo nvidia-glx-config enable.  I did that, rebooted, and et voila... bugger all working.. another black screen... I just don't get it.  What's changed in Dapper that would make it all go wrong?[/QUOTE]
Try point 4 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

If that doesn't work try point 13

---

### Post by yavez on 2006-07-26
My continuing adventures with the NVIDA driver continue.  I've tried everything in this threat, but here's something new.

If I do lspci | grep -i nvidia I get this printed out:
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)

So I then follow the guide here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) word for word and in my xorg.conf I get this:

> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"

and this:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"

Why does it think my Geforce 6200 is an ATI?  Could this have something to do with why I can't install nvidia accelerated drivers and get XGL working?

Anybody got any ideas, because I've tried everything (bar buying a Mac :))

---

### Post by yavez on 2006-07-26
Got it!

Not sure how or why (but it must have had something to do with option 4 mentioned in the above guide, because I tried it again)

Now I get the NVIDA splash and the desktop loads.  Still got a max resolution of 1024x768, but I'm sure I can figure that out sooner or later.

Thanks to everyone who posted, for your time, and your consideration.

Your help has made me very happy :) :) :)

---

### Post by iainmcc on 2006-07-26
Just joined up, sorry if someone has already answered... (I have exactly the same problem with my GeForce4 420 Go, including the ATI Radeon weirdness and so will be posting my own info, starting from a totally clean install -- my system is now unbootable)...

If you have a Windows machine available, do an unconditional format, in either FAT or FAT32. pmount should then be able to mount this as either 'msdos' or 'vfat'...

Otherwise, do a mkfs vfat on the stick before trying to mount it -- note that there is sometimes a (not necesarily complete or even valid) partition table on these things , which may or may not confuse pmount.

> **yavez said:**
> mount: wrong fs type, bad option, bad superblock on /dev/sdd1 (that's where it showed up when I plugged it in)  missing codepage or other erorr

Man, this install really is screwing with me something rotten!

My /dev/sda1 is where I have Ubuntu mounted (its a SATA hard drive)

PS, my machine (Toshiba laptop) has the root fs at /dev/hda1 on a standard notebook drive, and usb sticks show up at /dev/sd*.

---

### Post by yavez on 2006-07-26
It's all working now.  Nvidia.  XGL.  I'm very sure that it was the option 4 in the earlier post that did the trick for me.  Let us know how you got on, and I'll go over anything I did if it helps out.  Wohoo, Ubuntu is now my default operating system, with eyecandy only other operating systems dream of :)

---

