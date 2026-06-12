---
title: "Powerbook G3 with 9.10: lines &amp; stripes &amp; flicker"
date: 2009-11-23
forum: Apple Hardware Users
---

### Post by eddib on 2009-11-23
Hi everybody,

I just tried to install Ubuntu 9.10 on my old but trusty Powerbook G3 Pismo (firewire, 400 MHz). I wanted to try something else because OS X Tiger is too slow. I want to use the laptop as a music player and maybe to browse the web a little (how is chrome running on ubuntu?).

I downloaded the alternate install CD (I also tried the Live CD, but I can't get this burned onto a CD, iso is too big for a CD, and no DVD drive in my Powerbook).

Installation went fine, but now, when I boot up, I get these white and grey lines and flicker on the screen, and that's it.
There's a short video of my Powerbook booting [here]("http://www.youtube.com/watch?v=cu8XzmXkGYs")

I'm completely new to Ubuntu on a Mac, I need some help fixing this and step-by-step instructions would be best.

My main problem is that I cannot get into the terminal to try stuff out.

Any help would be greatly appreciated (and, I'm sorry, but being a newbie, please give me detailed instructions)

Thx,

Eddi

PS: I tried the 8.10 alternate install CD, same problem

---

### Post by linuxopjemac on 2009-11-24
Is there a way to boot your machine into a non-graphical mode ? I am on Debian and I can do a CTRL alt F1 to get into a terminal. This is disabled in Ubuntu as far as I can remember. You need to get a working Xorg.conf. I have the same machine as you do, but I am on Lenny as I said. I will post the Xorg.conf for your machine later.

---

### Post by linuxopjemac on 2009-11-24
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us,th"
#	Option		"XkbVariant"	"nodeadkeys"
#	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
EndSection

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"false"
	Option		"SWcursor" 		"true"
	Option 		"ForcePCIMode" 		"true"
#	Option 		"XAANoOffscreenPixmaps"

EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Standardbildschirm"
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
#	InputDevice	"Synaptics Touchpad"
	Option "AIGLX"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by linuxopjemac on 2009-11-24
What you need to do is start from the LiveCD and chroot into your installed system. To chroot into your system:

```
sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sda4 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
```

Then you need to edit the Grub configuration file to have an option to boot from your hard disk into a non-graphical mode. See the following link how to do that.

[http://forums.debian.net/viewtopic.php?f=16&t=34858](http://forums.debian.net/viewtopic.php?f=16&t=34858)

I hope it gives you enough direction to get this old Pismo going. If all fails and you are stuck you can always switch to Debian Lenny. It will certainly work.

This is also a good link:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

---

### Post by eddib on 2009-11-24
Hi Jan from Holland, 

thanks for the fast replies.
I don't have my pismo here with me, but I will look into this.

Great community here :p

grts,

eddi

---

### Post by llamabr on 2009-11-24
In the end, if this never works, you might try switching to Debian.  I've been running Debian (currently Lenny) on my g3 ever since ubuntu dropped ppc support.  And everything works exactly as you'd expect, right from the install.

---

### Post by eddib on 2009-11-25
> **llamabr said:**
> In the end, if this never works, you might try switching to Debian.  I've been running Debian (currently Lenny) on my g3 ever since ubuntu dropped ppc support.  And everything works exactly as you'd expect, right from the install.

Hi llamabr, 

I've decided to go with Debian, since I need to download a new image anyway (I need the Ubuntu Live CD to do the stuff posted above). Download limit here sucks, so better safe than sorry, Debian it is. I'll post here if all's well.

And thanks again.

---

### Post by linuxopjemac on 2009-11-25
You will have video problems too with Lenny. You have to copy and paste the Xorg.conf file I gave you and then it'll work.

---

### Post by eddib on 2009-11-25
DONE!

I installed the latest debian, but that gave me the same result (the lines and the flicker).
Luckily I did manage to get into the terminal with CTRL-ALT-F1.
I edited the xorg.conf and now it boots fine.

now for a music player and google chrome (or chromium)/opera.

---

### Post by linuxopjemac on 2009-11-25
CONGRATULATIONS ! :biggrin:

---

### Post by Firepowerforfreedom on 2010-01-05
I got the same result with my Pismo (a 500 MHz model w/DVD-ROM and a nice fat 120 GB hard drive), but I was able to go into xorg.conf and change the settings on the display. After trying Ubuntu and Xubuntu, I decided I liked the XfCE variant better, so I went with Xubuntu, but not for very long. 

My main qualm with Linux on my Pismo was that it sucked the life out of my two batteries (which would run forever in Tiger, and even longer in 9.2). Other than that, I was pleased with Linux, but I still decided to go back to Tiger simply because if aesthetics. Linux just didn't feel right on the Pismo, and Tiger still works fine for me.

I'm working on making our troublesome family HP Pavilion a6400f desktop into a Linux machine (currently it dual-boots, because I can't get all the programs we use with Windows running in WINE yet). Compared to Vista on this machine, Ubuntu 9.10 Karmic is a slice of heaven.\\:D/

---

