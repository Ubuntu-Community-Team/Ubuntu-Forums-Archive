---
title: "Need a suggested course of action"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-10-28
Ok so I've always been running Ubuntu on my onboard Intel card.  I have a dual boot set up and really haven't booted into Ubuntu for about 3 months.  On the Windows side of things I bought a new graphics card (ATI Radeon X1300)  and it still ran the onboard until I went into the hardware config and turned off the onboard card.

On the Ubuntu side of things when Gutsy came out, I found that the ATI card wasn't allowing  Ubuntu to install.  So I took it out and ran the on board and everything went good as usual.  Well I really would like to get the ATI card working (I know they are a bitch when it comes to Ubuntu compatibility)  So like Windows of course I tried to just put the card in and hope that Ubuntu would continue to run on the onboard until I told it not to but it won't boot into Gutsy if I have it in the PCI slot.

This is my only computer and I am no Linux master so does anyone have a suggested course of action to get this card working.  I've done several searches but all I can really do is print out the few tutorials I think will help.  It will take me all night if I screw up on the first try and then have to edit xorg and restart x from the terminal and boot back into Windows every time I need to figure out a different way, I'm just not that good with the command line.

UPDATE:  Is this link here:[ https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")  my best bet?

---

### Post by RomeReactor on 2007-10-28
Hi. I would suggest you change to the **vesa** or **ati** driver in "System->Administration->Screens and Graphics", reboot, go into your PC's BIOS, disable the Intel card, and continue booting.

The link you provided is for enabling the proprietary driver, so you can use desktop effects; but the first order of business would be to get your display working with the ATI card. Once you can boot into Ubuntu using that card, you can try enabling the other drivers.

---

### Post by siciliancasanova on 2007-10-28
Ok I'm going to do what you suggest.  What does anyone think about this link here:
[URL="http://jeffrasmussen.wordpress.com/2007/01/12/ati-radeon-x1300-works/"]
http://jeffrasmussen.wordpress.com/2007/01/12/ati-radeon-x1300-works/[/URL]

Apparently this driver just came out a couple days ago.

---

### Post by siciliancasanova on 2007-10-28
Ok this is where I'm at.

I switched the driver to VESA and it's not saving this configuration from the screens and monitors section.  Should I edit xorg and change it there?

I rebooted changed the BIOS, but it didn't really matter the BIOS was already disabling the onboard when the ATI was in the PCI.

---

### Post by RomeReactor on 2007-10-28
You could try editing Xorg.conf to change the driver from i810 or intel to ati; then reboot, which will possibly leave you in a console with no display, and then reconfigure X:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
chose **ati** for the video driver, and leave the defaults for everything else (unless you are certain something has to be changed). If your display doesn't start automatically after you finish reconfiguring X:
```
sudo /etc/init.d/gdm start
```

---

### Post by siciliancasanova on 2007-10-28
Update:

Ok now I am on VESA.  Even though my xorg file is supposed to be running the ATI driver.
VESA has always worked with my onboard card and now my resolution is at 800x600, things are still working.  However, when I put the ATI card in the PCI and boot it only gets to loading a little bit, presumably the part where it picks up the graphics card driver.  So at this point I still can't get into a command terminal and edit the xorg file with the ATI card in the PCI slot.

Not sure what I need to do from here to get my ATI card to work.

Also when I reboot with my onboard card now with VESA it gives me the option again to change drivers at boot time and configure but it still continues to not save changes such as switching it to ATI or switching it to RADEON

---

### Post by RomeReactor on 2007-10-28
I'm out of ideas; sorry. Maybe these [two]("http://ubuntuforums.org/showthread.php?t=588605") [threads]("http://ubuntuforums.org/showthread.php?t=579107&highlight=X1300") can help, or these search results on the [Multimedia & Video]("http://ubuntuforums.org/search.php?searchid=30085831") and [Desktop Effects & Customization]("http://ubuntuforums.org/search.php?searchid=30085951") sections.

---

### Post by siciliancasanova on 2007-10-28
I did find one on google where the guy was going through exactly what I am with his onboard card but it seems like he gave up on it.

---

### Post by CaptainInsaneO on 2007-10-28
When I made the switch from onboard to nVidia, I used my onboard video to install the drivers for my nVidia card, and then I changed my xorg.conf to the nVidia drivers. Then, I just rebooted into my bios, disabled my onboard video, saved and exited and everything worked fine.

I don't know if this will work for ATI, but it's worth a shot.

---

### Post by siciliancasanova on 2007-10-28
Basically that's what I'm trying to do now.  I have downloaded the latest ATI driver that worked for someone else that came out 2 days ago.  Now I'm not sure how to install this driver.  Like I said originally, I've been using Ubuntu enough to figure out where my problems are but I have no clue in the world how to install the downloaded driver.  I still spend most my time in Windows.

---

### Post by CaptainInsaneO on 2007-10-28
Have you tried using Envy?

Link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by siciliancasanova on 2007-10-28
Nope, but I'm going to.  Thanks for the suggestion.

Whenever I get this to work whether it's now or after I've been up all night I will post a how to for this card on my website.

---

### Post by siciliancasanova on 2007-10-28
Ahh so get this because I'm on the VESA driver with only a 600x800 resolution and cant enable desktop effects at all I can't hit the "apply" button with envy open.  Hmm, maybe I will try to switch my graphics card back to intel for now so I can actually operate envy.

---

### Post by RomeReactor on 2007-10-28
> **siciliancasanova said:**
> Ahh so get this because I'm on the VESA driver with only a 600x800 resolution and cant enable desktop effects at all I can't hit the "apply" button with envy open.

Is this due to the dialog window being to big for the desktop? if so, press and hold ALT and try moving the window with the mouse until the Apply button is visible.

---

### Post by siciliancasanova on 2007-10-28
Didn't matter, I fixed my resolution on my onboard.  I installed Envy, and it ran through and installed the ATI driver for me.  I restarted with my ATI card making sure the onboard was disabled and the same problem is persisting.

This is what Envy changed my xorg to:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

```

---

### Post by CaptainInsaneO on 2007-10-28
It looks to me like your BulletProof X kicked in there...

Are you now able to get output from your ATI card? If not, you can try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to re-configure your xorg.conf file.

---

### Post by siciliancasanova on 2007-10-28
The ATI card is not in right now.  Whenever I put it in and boot up I am running into a wall because I can't get Ubuntu to boot at all, even to reconfigure x.  So each time I make a change I am powering off, putting in the ATI card, booting up and seeing if it works, then taking the card out and turning the onboard back on and booting back up.

So I need a solution that can be achieved through the onboard and will allow the ATI card to at least be recognized.

---

### Post by CaptainInsaneO on 2007-10-28
What do you mean by the phrase you "can't get Ubuntu to boot at all"? Is it a black screen, or do you have a blue screen... error messages? what do you see?

---

### Post by siciliancasanova on 2007-10-28
Excuse me.  It's loading.  It gets about three bars down and stops, which I'm assuming is where it is hitting the graphics card driver.

I can get into bios and of course select my operating system but like I said when I select Ubuntu it just freezes on the loading.  This is the issue I've had with this card.

---

### Post by CaptainInsaneO on 2007-10-28
Hmm. That's pretty strange.

Do you try running off onboard video with the ATI card installed in your machine?

I know I'm asking a lot of really dumb questions but I'm trying to collect as much information as possible so we don't nuke your system.

---

### Post by siciliancasanova on 2007-10-28
Yes but not sure what that's really going to do.  First of all my machine is switching to the PCI card automatically when I put the card in so to do that I need to switch it to run the onboard with both of them in.  I'm not sure how smart envy is, if it would be able to detect the ATI card while I'm running the onboard.

EDIT:

Yes I have both in right now but I'm running on the onboard.  The ATI card is now in the restricted drivers manager and is enabled but the load screen still isn't getting past the same part.

---

### Post by CaptainInsaneO on 2007-10-28
You need to re-configure your xorg so it detects your driver then.

Try running ```
sudo aticonfig --initial
```

---

### Post by siciliancasanova on 2007-10-29
Hmm I did that but still hitting the wall.

---

### Post by siciliancasanova on 2007-10-29
It seems like I've already done everything that this guide shows: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

My xorg file seems to be correct as well.  Hmm this is weird.

---

### Post by CaptainInsaneO on 2007-10-29
I noticed earlier that you said you are not able to boot far enough to get a terminal (Ctrl+Alt+F1)... I apologize as I had not noticed that before. Maybe we can get you set up using a livecd. Also, you said you had not used Ubuntu in a couple months, and that you were trying to re-install? Maybe the download of Ubuntu you got for 7.10 is corrupt...

Anyway, to see the output when you start your system, you can use Alt+F2 to see the output instead of the progress bar. See if that gives you any better info.

---

### Post by siciliancasanova on 2007-10-29
Yeah well I have seen on google another case where the person said the almost identical thing with the same graphics card.  That the progress bar was stopping on them.  I will do what you suggest and watch to see where exactly it is stopping.  Here is my latest xorg file

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5	-	64.0
	Vertrefresh	56.0	-	65.0
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
	# 
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Monitor"
	# 
	Identifier	"monitor2"
	Gamma	1
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Driver		"fglrx"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
EndSection

Section "Device"
	# 
	Identifier	"device1"
	Driver		"vesa"Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
	Boardname	"VESA driver (generic)"
	Busid		"PCI:3:0:0"
EndSection

Section "Device"
	# 
	Identifier	"device2"
	Driver		"vesa"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:3:0:1"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Virtual	1280	1024
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	# 
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
EndSection

Section "Screen"
	# 
	Identifier	"screen2"
	Device		"device2"
	Monitor		"monitor2"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```


Be back soon

---

### Post by siciliancasanova on 2007-10-29
Hmm yeah it's stopping at 36.978231 , A few lines above there were a couple of error codes but nothing specific to say what they were.

---

### Post by siciliancasanova on 2007-10-29
Can anyone confirm this:  Based on the following info from the xorg log, is it possible that it's reading the wrong PCI bus?

```
(II) Primary Device is: PCI 00:02:0
(EE) No devices detected.

Fatal server error:
no screens found
```

---

### Post by CaptainInsaneO on 2007-10-29
Your xorg file looks really fishy to me. How did you get it if you can't boot into Ubuntu? Using the LiveCD?

> # You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

You should run that command if possible. Your current xorg.conf is really messy and I don't see any possible way that it could work.

Edit: Absolutely it's reading the wrong PCI bus. You can check which PCI busID your card is using by issuing this command:

```
lspci | grep VGA
```

---

### Post by siciliancasanova on 2007-10-29
I'm on the onboard right now, remember?

Sure I will try resetting it but that was the xorg that was generated by envy, not by myself.

---

### Post by CaptainInsaneO on 2007-10-29
Yes, re-configure it and choose ATI for the video driver. That should fix your problem. Hopefully.

---

### Post by siciliancasanova on 2007-10-29
Tried it again (the guy earlier suggested the same thing) and the progress bar still will not get past that point.

---

### Post by CaptainInsaneO on 2007-10-29
I'm beginning to think there might be something wrong with your install of Gutsy.

Believe it or not I've never seen anyone have this much trouble getting Ubuntu to boot with ATI. Everyone I've helped in the past has been able to get SOME kind of display going with their card. Albeit a limited one.

You should boot with your CD and choose "Check CD for defects" and see if there's something wrong with it.

Other than that, I am out of ideas. I'm sorry I couldn't help you more but I fear if I keep going I might have you do something that could really mess things up.

---

### Post by siciliancasanova on 2007-10-29
Already checked the cd for defects, this is actually the third disc that I burned to make sure that it wasn't that.

Well I'm off to bed, been working on this for 12 hours today and can't do it anymore.  Hopefully someone will help out between now and then.  Thanks for staying up and helping me on this.

---

### Post by CaptainInsaneO on 2007-10-29
No problem. I always try to help when I can, sorry I couldn't help more. :(

---

### Post by siciliancasanova on 2007-10-29
It's 2:50 am, still working on this problem to no avail.  In the end it's not THAT BIG of a deal but it would be nice not having to switch my VGA cable every time I switch operating systems.

---

