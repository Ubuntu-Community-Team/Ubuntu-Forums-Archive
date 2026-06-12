---
title: "Ubuntu LiveCD issues..."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by toiletdude on 2007-08-07
hey all!
about 3 weeks ago I tried Ubuntu for the first time using the live disk and I absolutely loved it.
My only complaint is this...

When I get to the initial menu that says install, install in safe GFX mode, etc. I click 'Install' it runs through the whole deal of the load and then just goes black... Idunno why. Ubuntu works fine in Safe GFX mode, but the res is really bad and I want to be sure that's not how it will look all the time. . . 

SPECS:
PIII 900 Mhz 
512 MB RAM
8 MB GFX card
DVD drive
*...those are my main specs...*


Thanks a bunch, guys!

---

### Post by jnorthr on 2007-08-07
This may happen if a driver has not been provided in ubuntu that matches your video graphics card. Generally, a 'generic' video driver may be installed in such cases thus providing you with a usable, though not perfect, display. After install you may be able to obtain a video driver that will more fully use the features of your GFX card. It may be worth some google research to see if you can locate a unix/linux/ubuntu video driver for your system prior to doing an actual installation. 

How does you screen look when running from the live cd ?

---

### Post by toiletdude on 2007-08-07
it doesnt look bad... just not the most appealing
It's just in 600 x 800 res... (or somethin' like that)

So it's really pixelated/choppy looking in the apps and on the desktop.

I suppose I'll do my google research, if I find this driver, what should I do with it? can I install it on Windows? or is there a place to put it on windows?
OR, should I run the LiveCD in safe GFX mode, then search/install the driver?

Thanks.

---

### Post by cobrn1 on 2007-08-07
You'll probably end up going into ubuntu safe graphics mode and then installing the driver. THen you'll probably have to restart the pc/xserver and then if all goes to plan you'll have a decent resolution. You may have to edit xconf tho, I'm not really sure.

But hey - you've been bumped to the top of the list, and we're half way there, so don't fret! :D

---

### Post by toiletdude on 2007-08-07
hey thanks!
Just two other things, when I load my Ubuntu installation, it doesn't work... It comes to a command prompt place (black and white) and wont go any further...

Also, how would I go about installing the driver?

Thanks a bunch, dudes.

---

### Post by cobrn1 on 2007-08-07
at the command promp try typing in startx      see how far that get you...

I think yo install the drivers you'll need to use apt-install, but I'm not an expert so hopefully someone else will post the answer. What is your graphics card though - that would really help to know.

---

### Post by toiletdude on 2007-08-07
my graphics gard is a **S3 Graphics Savage/IX 1014 ** it's also 8 MB.

---

### Post by cobrn1 on 2007-08-07
Oh this is a tricky one...

I had a look and couldn't find any drivers for that graphics card...sobs... however, there is a native linux driver - savage (imaginative, no?!) Anyway, If linux isn't using that then that might be the root of your problems...

Basically, could you please find a file called xorg.conf (I think it's found in /etc/X11/) and copy and paste its contents into a post please. Then we can look and see if it is using that driver. Please be caseful not to edit the file, just copy and paste (messing this file up can seriously bugger up your installation...)

Anyway, if it's not using the driver then we can make it, otherwise I'm afraid there's not much else I can do, there doesn't appear to be any other drivers...

Oh well, if you post the contents of the file then we'll have a better idea...

---

### Post by toiletdude on 2007-08-08
alrighty, i'll get that to you tomorrow.

once again, i appreciate the help. I'm a linux noob.

---

### Post by splintercellguy on 2007-08-08
I suppose backing up /etc/X11/xorg.conf, and sudo dpkg-reconfigure xserver-xorg, picking the resolutions you want MAY do the trick. Vesa driver may do it.

---

### Post by cobrn1 on 2007-08-08
> **splintercellguy said:**
> I suppose backing up /etc/X11/xorg.conf, and sudo dpkg-reconfigure xserver-xorg, picking the resolutions you want MAY do the trick. Vesa driver may do it.

THat's an interesting idea...

First lets just see what the conf file says... if it's not using 'savage' as the driver then its an easy fix, otherwise we might have to try the above...

---

### Post by toiletdude on 2007-08-08
just an update, forgot to mention some things before.

I never have actually installed ubuntu successfully, it wont let me partition my drive.


But anyway, I'll get the contents of xorg.conf in a few minutes. :)

---

### Post by cobrn1 on 2007-08-08
What were you using to partition your hard drive?

---

### Post by toiletdude on 2007-08-08
Just the default partitioner that is in the Ubuntu installer.

Anyway, how exactly would i go about getting the contents of the file xorg.conf?

---

### Post by eapache on 2007-08-08
In a terminal use```
sudo gedit /etc/X11/xorg.conf
```this should open it in a text editor.

---

### Post by cobrn1 on 2007-08-09
It would seem that:

```
sudo dpkg-reconfigure xserver-xorg
```

is a common fix to this problem and may work for you. As always, we reccoment you back up the xorg.conf file (make a copy called xorg.conf.bac in the original folder, so you can restore that if it all goes wrong)...


Also, if you post the contents of the xorg.conf file (at /etc/X11/) then we can see if it is using the 'savage' driver, which it should. You can open the file by opening nano (or any simple text editor) and going to that directory and opening the file. Just copy and paste the contenct into your post...


Finally, this is the S3 driver page, and the first listing has drivers which look like they're for your card (but I'm not 100% sure - given that you're still running a live CD if it goes wrong you can just reboot anyway, so no harm trying...

[http://www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp](http://www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp)

Direct link to what I think is the correct linux drivers for your card:

[http://drivers.s3graphics.com/en/download/drivers/legacy/SavageMX-IX_290-299/Savage_4.0.3_binary.tgz](http://drivers.s3graphics.com/en/download/drivers/legacy/SavageMX-IX_290-299/Savage_4.0.3_binary.tgz)

---

### Post by toiletdude on 2007-08-11
alright, thanks a bunch. will try it out today.

Sorry for not answering you guys much, been busy and my Windows installation has been giving me hell...

---

### Post by toiletdude on 2007-08-11
alright, guys.
I'm posting this from the Ubuntu LiveCD. :)

Anyway here's the contents of xorg.conf...


> 

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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



There are the contents :D

I noticed that it says: Generic Video Driver... i think that's the issue. (idk though, first time on Linux)

Thanks guys.

---

### Post by eapache on 2007-08-11
this is probably the issue. change the driver from vesa to savage, save, then press ctrl-alt-backspace. This will restart x. A login screen should appear, and autologin after a few seconds. Post back if that works.

---

### Post by toiletdude on 2007-08-13
sorry, when i tried it, it didnt work...:(

I did CTRL + ALT + BACKSPACE and after it 'restarted' it just went black...

I might try again later, though

---

