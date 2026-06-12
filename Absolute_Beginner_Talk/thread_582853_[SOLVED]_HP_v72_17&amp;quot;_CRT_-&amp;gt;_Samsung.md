---
title: "[SOLVED] HP v72 17&amp;quot; CRT -&amp;gt; Samsung SyncMaster 245B Wide 24&amp;quot;, how to?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Saya on 2007-10-20
Hi all.

Couple things I believe to be relevant.

[list][*]My Ubuntu box will be without internet until mid November.
[*]The graphics card is a nVidia GeForce 6200LE
[*]I conf'ed this installation back when 7.04 was released, and haven't touched its settings since then (oh I love Ubuntu)
[/list]
Now I've decided to trash my old CRT and got my hands on a SyncMaster 245B.

My questions are,
[list][*]How will it be affected by my old xorg configuration, i.e. the HP v72's sync rates?
[*]Is it compatible with the graphics card?
[/list]
Thanks for any help...

---

### Post by mivo on 2007-10-20
All you probably will have to do is to run this:

```
sudo dpkg-reconfigure xserver-xorg
```

.... and select "medium" when you are asked to choose between simple, medium and advanced monitor configuration. If all goes well, the choice of 1920x1200 (the 24"'s native resolution) will be offered to you. Make a copy of /etc/x11/xorg.conf before you do this. You will not need any extra drivers, and yes, the card you have should work just fine (just don't expect to play any fast games at 1920x1200 :)).

---

### Post by Saya on 2007-10-20
Thanks muchly, I'll see how it goes once the beast arrives after the weekend. Gaming isn't exactly an issue, I use the box for coding, image and video editing and the occasional movie only. If things start to go sluggish there's always the option of future upgrades.

Again, thanks, I'll report back in case things go wrong.

---

### Post by mivo on 2007-10-20
I picked up a 22" LCD last week that replaced a 19" one. Doing the above worked smoothly for me, so it turned out to be just a matter of ten minutes. I was also worried it would turn into a larger affair, but it was simple and straight-forward. :) (I assume your video card has a DVI out, by the way.)

---

### Post by stefan1975 on 2007-10-21
hi all,

i have a samsung syncmaster 245b too as external monitor for my dell m65 notebook (nvidia quadro 350). Unfortujnately i cannot get it to work at all with ubuntu 7.10 (or opensuse 10.3 or mandriva 2008 for that matter) with the binary nvidia drivers. The only way i can get picture out of it is using vesa drivers at an insanely low resolution. When i use nv or nvidia the screen stays black and the power-led blanks blue. I do get sound (the gdm drums) and can <crrtl><alt><f2> to a console session.

I hope things work out better for you, if it works please let met know or show your xorg.conf so that i can finally get it to work as well, ubuntu 7.10 works fine at 1920x1200 on my laptops lcd screen, but now i have a useless Syncmaster 245b standing here. 

Mint 3.0 and arch 2008.02 are working fine with my screen, so i really dont know what is going on with it, maybe a 2.6.22 kernel thing or so or a combination with 100.14.19 nvidia drivers .....

I tried reinstalling with the monitor connected, reinstalling using the alternate cd, using both x86 and x64, doing a dpkg-reconfigure, no show just a black screen with a blinking led.
stefan

---

### Post by Qwerty_ on 2007-10-21
Stefan have you installed the nvidia restricted drivers?

System>Administration>Restricted Drivers Manager.

---

### Post by stefan1975 on 2007-10-21
hi,

thanks for the tip. i did install the restricted drivers. on my lcd screen i have compiz wobbling like crazy, just not the 245b. I also tried downloading the nvidia drivers directly from nvidia or running the "nv" drivers, both with a vga cable and a dvi cable but still no show. 

I do not think it is a hardware issue, we have three dell m65 laptops all with samsung syncmaster 245b screens and no combination works with the latest batch of distros.

windows vista is working fine as well (well monitor wise that is).

stefan

---

### Post by stefan1975 on 2007-10-22
Saya,

how did this work out for you? i am back at the office and whatever i try to do i cannot get my syncmaster 245b working. this is a real showstopper for me since i cant keep working on my laptop's lcd screen. 

I think it is so weird, why wouldn't it be working? 

hope you or anyone can help.

stefan

---

### Post by Saya on 2007-10-24
> **stefan1975 said:**
> Saya,

how did this work out for you?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Picked the resolutions I assumed to use later on (1920 x 1200, 1650 x 1050), CTRL + Backspace, and t'was done.

---

### Post by stefan1975 on 2007-10-31
good for you. could you please post your xorg.conf so that i can compare it to mine? I still can't get it working properly in my docking station. are you using a docking-station/laptop? It might be a laptop issue or something because it sort of works when i use nvidia-settings and enable the syncmaster and then select twinview. i get compiz enabled 1920x1200 graphics on my syncmaster, but just as a clone of the lcd screen, so when i close the lid of the laptop, the tft turns off as well, this is very unhandy in a docking station.

thanks,
stefan

---

### Post by Saya on 2007-10-31
I'll probably get my internet back at home no later than Monday, I'll see if I can get my xorg.conf here before that. Since I'm using a stationary PC with only one monitor I don't know if it'll be of much help, but we'll see.

---

### Post by Saya on 2007-10-31
> **stefan1975 said:**
>  could you please post your xorg.conf so that i can compare it to mine?
Surprisingly got my internet back today, so here's my xorg.conf

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
	Identifier	"nVidia Corporation NV44 [GeForce 6200 LE]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster 245B"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44 [GeForce 6200 LE]"
	Monitor		"SyncMaster 245B"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

