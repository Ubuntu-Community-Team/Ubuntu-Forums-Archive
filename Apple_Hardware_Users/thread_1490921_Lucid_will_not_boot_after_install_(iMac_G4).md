---
title: "Lucid will not boot after install (iMac G4)"
date: 2010-05-22
forum: Apple Hardware Users
---

### Post by cheeseburgerpizza on 2010-05-22
I installed Lucid PPC on a G4 iMac (lamp-style, 800 mhz) using the netinstall mini cd.  The install environment booted and installed a base system without any problems.  However, when trying to boot into the installed system, I get about a second of text after the yaboot screen, then darkness, then a full screen of bright red. Note that X is not installed, so the red screen is not an xorg problem.   

I've tried booting with "Linux nosplash video=ofonly", and "Linux single" but the problem occurs in both cases.  I can use rescue mode on the cd and chroot into my system on the hard drive, but I'm not sure what steps to take from that point.  It does seem to be a functional system when I'm chrooted, I can use apt etc.

I don't want to give up on this installation and install karmic yet, so any ideas about how to fix this broken install would be greatly appreciated.

---

### Post by linuxopjemac on 2010-05-24
It still seems like an X issue. Don't know exactly what Lucid does, but I would try to use a working xorg.conf file.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
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
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV18 [GeForce4 MX with AGP8X (Mac)]"
	BusID       "PCI:0:16:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by sha.goyjo on 2010-05-25
> **linuxopjemac said:**
> It still seems like an X issue. Don't know exactly what Lucid does, but I would try to use a working xorg.conf file.


I do believe this fellow just said he hasn't installed x yet. If he is using and ubuntu mini image, it doesn't install by default. He can make an xorg.conf, but there is no xserver there to read it yet.

OP:
Do you know what model of video card is in your mac? can you look it up on everymac.com for us? Maybe we can pass on some framebuffer settings through yaboot

---

### Post by sha.goyjo on 2010-05-26
Can you try passing 
```

video=vesafb

```
To the kernel at boot time?

Let us know if that helps at all.

---

### Post by Beeblejj on 2010-07-08
> **sha.goyjo said:**
> Can you try passing 
```

video=vesafb

```To the kernel at boot time?

Let us know if that helps at all.

I also have a G4
[http://www.jaddie.com/jpg/new_imac2_dontlink.jpg](http://www.jaddie.com/jpg/new_imac2_dontlink.jpg)

The problem happens at install as well (using a DVD). It won't even go to the splash screen once I typed in "live", "live video=ofonly, "live-powerpc", and "live video=vesafb"

---

### Post by linuxopjemac on 2010-07-09
You might want to have a look at turning off KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by Beeblejj on 2010-07-17
I tried the KMS thing and no luck.
I even tried upgrading from 9.10. 

My boot only goes as far as the boot loader for the powerpc. After that it is a red screen right after it starts loading the kernel and just before the splash screen.

---

### Post by linuxopjemac on 2010-07-18
Install Debian Lenny Mint LXDE, Conal can agree on that. It will run fine on an iLamp.
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

---

### Post by Beeblejj on 2010-07-18
> **linuxopjemac said:**
> Install Debian Lenny Mint LXDE, Conal can agree on that. It will run fine on an iLamp.
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

Thank you! I will test this out. I just really like Ubuntu, because I notice amazing improvements in every upgrade.

I have tried it and it seems like it doesn't want to boot.

---

### Post by Beeblejj on 2010-08-14
I have tried it and it doesn't seem to work. I've gone back but I have another problem. Live login won't work. Reburned disc and formatted all partitions except APPLE. Nothing.

Oct 4. To date I have tried 8.10, 9.10, 10.04. Problems all round.

---

### Post by Beeblejj on 2010-11-28
It hurts me to say this but I have tried everything else, and the only one that seemed to work well is YDL (yellowdog).

I will still used Ubuntu on my other computers!

---

### Post by dpny on 2010-11-28
> **Beeblejj said:**
> It hurts me to say this but I have tried everything else, and the only one that seemed to work well is YDL (yellowdog).

I will still used Ubuntu on my other computers!

How do you like Yellowdog? I looked at it, but there doesn't seem to be much activity on the forums.

---

### Post by linuxopjemac on 2010-11-29
I can recommend MintPPC.

---

### Post by AVMan on 2011-01-19
Just to throw in my 700mhz ilamp experience:
Ubuntu 8.04, Linux Mint 9 and Debian 5.04, and YDL  all work.  Unfortunately, I would very much like to get Ubuntu 10.04 on there since it is what I'm used to. Personally, from the short time I spent with YDL, I really do not like it. It seems to not be debian based and I really like just being to apt-get anything I want, it also is overly flashy with moving tool[FONT=Verdana][COLOR=Black]bars and such that are unnecessary. 

What I have on the ilamp right now is Debain 5.04 LXDE (Not Mint 9). [/COLOR][/FONT][http://cdimage.debian.org/debian-cd/5.0.7/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.7/powerpc/iso-cd/)
[FONT=Verdana][COLOR=Black]
One of the install disks I tried on this machine was Ubuntu server 10.04, and after install and a reboot it gives me a "colored screen of death" (it seems to be a different one of every reboot) This must mean there is something else in there besides an X environment that's causing it.  Something passed from yaboot perhaps?
[/COLOR][/FONT]

---

### Post by rabbitear on 2011-04-09
This isn't a 'Zap the PRAM issue?' just upgraded to Ubuntu 10.10 on this 800mhz iMac (lamp), same screen issues.  Still working on it, but might try some other distro's while I'm at it too.

---

### Post by rabbitear on 2011-04-09
the option "nouveau.modeset=0" atleast did the trick for booting the machine but it seems to be in 16 color mode.  Maybe one of these other xorg.conf will fix that.

---

### Post by jimwg on 2011-04-09
> **rabbitear said:**
> the option "nouveau.modeset=0" atleast did the trick for booting the machine but it seems to be in 16 color mode.  Maybe one of these other xorg.conf will fix that.

I'm happy that at least one iLamp user managed to resolve an issue, but please tell me exactly how you did this? Where and how do you do the xorg.conf thing to install 10.10? All I have is a black screen with Ubuntu lettered in white above four dots, three of which are red like the works stalled out! I'm running out of blank CDs bouncing between 8.10 and 9.10 and Debian 5 & 6 installers! Really appreciate some tips! Non-techie newie here!

Thanks,

Jim
700mHz iMac

---

