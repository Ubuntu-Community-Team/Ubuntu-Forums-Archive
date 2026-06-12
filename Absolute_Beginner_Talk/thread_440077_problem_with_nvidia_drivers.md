---
title: "problem with nvidia drivers?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Rob195 on 2007-05-11
Hi everyone! I'm new to the entire world of Linux and I'm just coming to discover how wonderful it is.

But I''m having a problem and I dont really know what is causing it, I might be watching a dvd, or some videos online, and all of a sudden, the screen will blank out, and it seems like the X server restarts - I find myself logged out, back at the login screen. I can then log back in and everything appears to be fine. It's just kinda frustrating that in the middle of a movie, you're not really sure if you are just going to be dropped from the system?

I'm using the latest nvidia drivers on a Geforce 6200 - any ideas?

This problem only occurs when dealing with movies, or other media of that nature, never while playing music, browsing the web, or doing anything else.

This also occurs when using Beryl, except when dealing with Beryl, my computer completely locks up with just a frozen screen, and I have to hard reboot.

---

### Post by Kobalt on 2007-05-11
I have a GeForce 7200 Go and if I enable GLX for such things as Beryl/Compiz (even though I don't run them) I get random crashes... I don't know if that's related, but it could help maybe. Indeed I've removed the "AddARGBglx" section from my xorg.conf since then, no crashes for a couple of weeks...

---

### Post by Medieval_Creations on 2007-05-11
I am running a GeForce 6200 too and have never had that issue.

How did you install the nvidia drivers and did you reconfigure xserver afterward?

There are the steps that I used when setting up mine:
```

sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg

```

One not about doing the reconfigure.  Make sure you choose nvidia as the driver and enable (or check) all the modules (bitmao, dbe, ddc, dri, extmod, freetype, glx, int10, record, v41, & vbe.

If it doesn't automatically detect it, here's what I put in as my Vid-Card description.
```

   Vid-Card:

	nVidia Corporation [GeForce 6200 Turbo Cache]

```

If that doesn't fix it, then we may need to look into how you monitor is being configured.  I attached my xorg.conf for you to referance.   Feel free to try it, but make sure you back up yours first, & it may not work for your rig.

---

### Post by Rob195 on 2007-05-11
I installed the driver by going into the restricted modules manager.  I saw that there was an ati graphics driver already listed there, and so I just put a check in the enable box, and upon restart ubuntu told me that the nvidia driver was now in use.  was that wrong?

I'm also having a problem where firefox and opera will just completely shut down for no appearent reason. I dont know if the two problems are related.

---

### Post by Toet on 2007-05-11
> **Rob195 said:**
> I installed the driver by going into the restricted modules manager.  I saw that there was an ati graphics driver already listed there, 

Are you just mixing your words up in this post, or did you install an ATI driver?

---

### Post by Rob195 on 2007-05-11
no it was definitely an nvidia driver.  Did I not configure it properly?

Yeah, sorry I did mix up my words, it was an nvidia driver.

---

### Post by Terl on 2007-05-11
> **Rob195 said:**
> 
This also occurs when using Beryl, except when dealing with Beryl, my computer completely locks up with just a frozen screen, and I have to hard reboot.

Have you tried running these things with beryl off?  I would try that.  I have had issues with some games running slow/odd if beryl or compiz is on.  That would help sort out if it is the driver or beryl interfering.

---

### Post by Rob195 on 2007-05-11
yeah, i only get the hard crash with beryl on.  When beryl is not on, I only get logged out and brought back to the login screen

---

### Post by Terl on 2007-05-11
> **Rob195 said:**
> yeah, i only get the hard crash with beryl on.  When beryl is not on, I only get logged out and brought back to the login screen

Maybe a silly question, but is the screensaver trying to cut in and causing problems?

When you start up do you see the nvidia logo and such?

---

### Post by Rob195 on 2007-05-11
When the system starts up I see the restrcted driver module starts, but i dont see any nvidia logo

problems also occur with Azureus.  For some reason, most of the time when a popup window comes up, it will hard lock the computer

---

### Post by Terl on 2007-05-11
Ah, that is interesting!  Could you please post a copy of your xorg.conf?  That will tell us what we need to know to get you hooked up.  The nVidia logo splash should show up unless you actuvely set it not to and it does not sound as if you have.

---

### Post by Rob195 on 2007-05-11
I'm sorry, but I'm very new to linux and......could you mabye describe to me how to do that?

I got it, I'll have it up in a sec

---

### Post by Rob195 on 2007-05-11
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"nVidia Corporation GeForce 6200 A-LE"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 6200 A-LE"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


I see there that no logo is set to true, that would explain the no splash screen, but if that is all, then my problem still remains.

It also says something about my card being pci, but I have an AGP card, could that also be an issue?

---

### Post by Terl on 2007-05-11
```
Section "Device"
Identifier "nVidia Corporation GeForce 6200 A-LE"
Driver "nvidia"
Busid "PCI:1:0:0"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "NoLogo" "True"
EndSection

```

OK, you have the logo turned off... no problem with that.  

I am stumped.  Is this with every dvd you try?  Can you think of anything common when the shutdown happens?

---

### Post by Rob195 on 2007-05-11
yeah the two types are common:

Beryl Off:
All applicatios close without warning and I appear at the login screen.
usually occurs when dealing with video

Beryl On:
Screen freezes and computer hard locks.
occurs randomly

My only thoughts are that my chipset on my graphics card might be defective, because when I also installed this card in windows, it now has the nasty habit of crashing the computer as well, with the blue screen.  Mabye this card is just unstable.

---

### Post by Terl on 2007-05-11
> **Rob195 said:**
> yeah the two types are common:

Beryl Off:
All applicatios close without warning and I appear at the login screen.
usually occurs when dealing with video

Beryl On:
Screen freezes and computer hard locks.
occurs randomly

My only thoughts are that my chipset on my graphics card might be defective, because when I also installed this card in windows, it now has the nasty habit of crashing the computer as well, with the blue screen.  Mabye this card is just unstable.

Have you perhaps a spare card to swap and see?  :)   Kidding... That last bit sounds like a possibility and that is where I was headed.  (I am at work so I am switching in and out of the forums and running my reports and db's at the same time-so pardon delays).  If it is crashing windows too it does not bode well.  Is there a warranty--hopefully...

I have an ati x1600 sitting in a drawer... :)

---

### Post by Rob195 on 2007-05-11
yeah I have a x1300 here too, its pci and never gave me any trouble, I just seem to never have luck getting it to run on linux.  

Besides, its a big pain in the neck because my mother board doesnt load the pci drivers until its reached some sorta login screen, so it would leave me constantly switching the monitor cable between onboard and the card.

---

### Post by Terl on 2007-05-11
Linux is one reason the x1600 (mine is a PCI-E) is sitting in the drawer...that and I just did not like the performance compared to nVidia with the games I play.  I have always used nVidia and one time I try an ATI and I am disappointed.  Oh well.

Do you have a way to test with another nVidia card?  It would be nice to confirm suspicions...

---

### Post by Rob195 on 2007-05-11
yeah, I do have an agp nvidia card that is 64mb I think I can put that in there.

---

### Post by Terl on 2007-05-11
I would give it a try.  If there is no crashing it will make you check more into the newer card. 

Speaking of crashing, the Cubbies going to make it?  :)

---

### Post by Rob195 on 2007-05-11
I've been saying since the offseason that they are going to be competitive.  I'm not going to stake claim on the playoffs, but they are going to give those top teams out there a run for their money.

playoffs would be nice though.

---

### Post by crazyflax on 2007-05-11
Hey guys I'm new to Linux and these forums so be kind :p I'm using Ubuntu 7.04 and it's a really old computer. My main issue is that my video card is an NVIDIA GeForce 2 MX 400. Whenever I don't move my mouse for more than a minute, the screen goes black and I get these wierd multi-colored (mainly orange) horizontal bars. I can stop X from running and sometimes it'll allow me to log back in and sometimes I have to shutdown the computer with the power button. Any suggestions? Thanks for your help!

---

