---
title: "Help please with getting GUI back up"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by staib on 2006-11-05
Hi
Have been running 6.06 and then 6.10 happily - until my ATI Radeon card's cooling fan decided to go on strike. Faced with a blank screen, I tried a VERY old non-3D graphics card but this wouldn't even load the GUI desktop.  I have now replaced the old Radeon with an Nvidia 7600GS but I end up with the same page full of error messages.

If I boot (using grub) from the second option then it brings me to the command prompt - but being a newbie I'm not sure what command to type in to get the gui back up and running.  I'm sure its simple (if you know what to do) and would be v grateful for any insights!
Cheers,  Nick

---

### Post by apjone on 2006-11-05
I normally insert the live CD + boot to the live desktop then mount my / filesystem to /mnt . Then i back up my xorg.conf cp /mnt/etc/X11/xorg.conf /mnt/etc/X11/xorg.conf.old. Then copy the live cd xorg over mine. cp /etc/X11/xorg.conf /mnt/etc/X11/xorg.conf and that normally works for me


> **staib said:**
> Hi
Have been running 6.06 and then 6.10 happily - until my ATI Radeon card's cooling fan decided to go on strike. Faced with a blank screen, I tried a VERY old non-3D graphics card but this wouldn't even load the GUI desktop.  I have now replaced the old Radeon with an Nvidia 7600GS but I end up with the same page full of error messages.

If I boot (using grub) from the second option then it brings me to the command prompt - but being a newbie I'm not sure what command to type in to get the gui back up and running.  I'm sure its simple (if you know what to do) and would be v grateful for any insights!
Cheers,  Nick

---

### Post by bulldog on 2006-11-05
First thing to do is to uninstall your ATI drivers,they won't work well with your new nVidia card.:D 

Then install drivers for your nVidia graphics.

If you type in your console ```
sudo dpkg-reconfigure -phigh  xserver-xorg
```it's possible to get into your GUI mode again.

---

### Post by staib on 2006-11-05
Thanks for those swift replies...

Bulldog - thanks for the tip about switching drivers - I was just trying to re-open the gnome gui first, albeit in an unaccelerated fashion.  I tried that command but it comes back with a "warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20061105...."  then drops back to the command prompt.

Apjone - I would have tried that too, but I don't have a CD of 6.10, as I just "upgraded" from 6.06 - which went fine.  I am assuming there would be a problem doing what you suggest with the 6.06 cd - or would that be OK?!

Cheers,

Nick

---

### Post by apjone on 2006-11-05
should be ok , just back up the xorg.conf as i said just in case. It should give you a gui back, good luck

> **staib said:**
> Thanks for those swift replies...

Bulldog - thanks for the tip about switching drivers - I was just trying to re-open the gnome gui first, albeit in an unaccelerated fashion.  I tried that command but it comes back with a "warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20061105...."  then drops back to the command prompt.

Apjone - I would have tried that too, but I don't have a CD of 6.10, as I just "upgraded" from 6.06 - which went fine.  I am assuming there would be a problem doing what you suggest with the 6.06 cd - or would that be OK?!

Cheers,

Nick

---

### Post by bulldog on 2006-11-05
> **staib said:**
> Thanks for those swift replies...

Bulldog - thanks for the tip about switching drivers - I was just trying to re-open the gnome gui first, albeit in an unaccelerated fashion.  I tried that command but it comes back with a "warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20061105...."  then drops back to the command prompt.

Apjone - I would have tried that too, but I don't have a CD of 6.10, as I just "upgraded" from 6.06 - which went fine.  I am assuming there would be a problem doing what you suggest with the 6.06 cd - or would that be OK?!

Cheers,

Nick

The warning is it makes a copy of your xorg.conf,so you could copy it back if things don't work out,nothing to worry about though.
It set the xorg.conf back to default.

Try startx or if that isn't working```
sudo /etc/init.d/gdm start
``` in your normal mode,not recovery mode.

---

### Post by staib on 2006-11-05
OK - I dropped in the 6.06 disc, but it also now gets the same error message.  Now I can see it, it said:

"Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?  <Yes> <No>"

The deafult is Yes, so going with that takes me to another screen with all sorts of X Windows data, that tells me the log file is "/var/log/Xorg.0.log" and the config file is "/etc/X11/xorg.conf"   

Clicking OK offers a more detailed output.  But's its v long!

I guess I was hoping to be able to re-initialise somehow the X server, so it can see what the new system contains...

Nick

---

### Post by apjone on 2006-11-05
hmmm, strange......... sorry mate this is beyond me. :( ](*,) ](*,) 

> **staib said:**
> OK - I dropped in the 6.06 disc, but it also now gets the same error message.  Now I can see it, it said:

"Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?  <Yes> <No>"

The deafult is Yes, so going with that takes me to another screen with all sorts of X Windows data, that tells me the log file is "/var/log/Xorg.0.log" and the config file is "/etc/X11/xorg.conf"   

Clicking OK offers a more detailed output.  But's its v long!

I guess I was hoping to be able to re-initialise somehow the X server, so it can see what the new system contains...

Nick

---

### Post by bulldog on 2006-11-05
> **staib said:**
> OK - I dropped in the 6.06 disc, but it also now gets the same error message.  Now I can see it, it said:

"Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?  <Yes> <No>"

The deafult is Yes, so going with that takes me to another screen with all sorts of X Windows data, that tells me the log file is "/var/log/Xorg.0.log" and the config file is "/etc/X11/xorg.conf"   

Clicking OK offers a more detailed output.  But's its v long!

I guess I was hoping to be able to re-initialise somehow the X server, so it can see what the new system contains...

Nick

That shouldn't happen though,if you fire up the live cd it works independent of your install and should use a native driver for your graphics.

It can't make a log file on your cd ](*,) 

Just try to boot your normal kernel,no recovery and use the reconfigure command if X gives you the error.

Then type restartx or sudo /etc/init.d/gdm start
and see what happens.

---

### Post by staib on 2006-11-05
Thanks Bulldog...

Tried as you suggested - but I can't even get to the command prompt in the normal kernel - I get that error message and then if I OK everything the cursor settles about 3 characters off the left of the screen - I don't believe there is any command prompt there, as nothing happens even with basic commands.

I tried using the "sudo /etc/init.d/gdm start" coimmand from the recovery kernel, and at least that produced a tidy screen version of the "Failed to start the X server..." message. Its a neat black and white message with a drop shadow around the bottom.

The report ends...

(EE) No devices detected

Fatal server error:
no screens found.

The further details section notes 
(**) | | -->Device "NVIDIA Corporation Default Card"

but then there are lots of references further down to ATI and Radeon...

Is this driver loading and causing a problem? Is there a way to remove the ATI driver from the command prompt and revert to default...(I know there is!)

Of scant comfort is the fact that XP on the other partition recognised the new card immediately Grrrr!

Thanks for the help guys.

Nick

---

### Post by bulldog on 2006-11-05
Okay let's try something different shall we?

Go in recovery mode and type in console```
sudo nano /etc/X11/xorg.conf
```

This opens xorg.conf in a text editor.
Then scroll down to the device section and make it driver "nv" instead of what it is.
Then everything which refers to ATI put a # before it.

I have a nVidia graphics and this is what my xorg.conf looks```
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
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option "RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"Philips 170S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
	Monitor		"Philips 170S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

Take from it what is relevant to you.

Then close the file by CTRL--x and push enter to save it.
Then try to reboot or startx etc.

---

### Post by staib on 2006-11-05
That all made sense Bulldog - thanks... I am learning...It's the console, not a command prompt :) 
I have even adjusted the monitor display, so I can see everything. 

I opened up the xorg conf file using nano and replaced the ATI driver reference with nv (I saw yours was nvidia...?)  But anyway using the startx command generated an X Window error screen saying:
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) No drivers available

So I rebooted (again) - but no luck - back to the messy X server error message - which repeats the above...  Is there some generic display module that will work?

Nick

---

### Post by bulldog on 2006-11-05
Yes and that is triggered by ```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

This should work,it makes a backup of your xorg.conf and replace it with a new one.

But can you remember how you installed your ATI drivers?
It should be so much easier if they where gone from the system.

EDIT:
You can try however to install the nvidia drivers```
sudo aptitude install nvidia-glx
```

---

### Post by staib on 2006-11-05
Yes - I used the guide here - the top section worked fine:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Anyway, I went to install the nvidia driver (thanks) using:

sudo aptitude install nvidia-glx

and that quickly suggested removing the ATI one (which seemed sensible), so I did all that - and then it finished loading the nvidia driver as well...

Re-booted in the main kernel (grub option 1) > but... that went to the usual error screen...  ](*,) 

Please save me from Windows!  I want Ubuntu back!

LOL - Nick

---

### Post by staib on 2006-11-05
I just typed:

sudo nano /etc/X11/xorg.conf

in the console and can see that the driver (under Section "Device" is now showing as "nvidia" - so there is some good news!

Nick

PS - I can also see from the detailed output of the X Server Error report that all referenced to the old ATI Radeon card have gone and are replaced with references to various NVIDIA cards...

---

### Post by bulldog on 2006-11-05
And sudo dpkg-reconfigure -phigh  xserver-xorg isn't doing anything in this stage for you?

---

### Post by staib on 2006-11-05
No - sorry - I had tried that way back this afternoon and then again later but nothing.  

What is also weird is that I tried again booting from the original 6.06 CD, but that won't get past the start up page (the one with the logo and the boot up stuff scrolling past).

I also just tried booting from a Puppy Linux CD and that also wont allow me into any graphical interface.

The "only" thing I did last night was swap out the fried ATI card and replace it with an ancient Hercules 3d prophet card to see if I could get a picture back.

The new Nvidia card is a 7800GS which I had assumed would work fine.

As I mentioned, booting into XP was problem free, so I know its not a physical graphics card problem...

I can see into the Ubuntu file system from Windows, but am not sure what I should be looking for...

Any further help much appreciated - had no idea this would all take this long!

Nick

---

### Post by bulldog on 2006-11-05
Well I'm running out of options :neutral: 

We did remove the ATI drivers,put in the nvidia drivers,tried to reconfigure your xorg.conf and all of that seems to do nothing at all.

I have no clough what to do anymore,what's relevant is done and didn't help.

I'll find it kind of strange the live cd won't boot into a graphical interface as well,almost thinking Ubuntu is not configuring your card for any reason.

---

### Post by staib on 2006-11-05
Cheers pal - I'm off to have a glass or two of wine - doubtless I'll be back at some time, but I'll raise a glass to you in appreciation of all your effort!  

I'll check back later see if anyone else has any ideas.  At this stage I would be happy to reinstall from scratch, if I could get the CD to load in the first place... :confused:  ](*,) 

Nick

---

### Post by staib on 2006-11-05
If anyone new to this thread fancies a little evening brain teaser - a challenge more satisfying than any game of Sudoku - I would appreciate some ideas, so that I can get my 6.10 desktop back into shape!

Summary:

Running Ubuntu 6.10 - having upgraded from Dapper Drake - functional, fast, we all loved it... hardly use the XP dual boot option.

Last night the ATI Radeon gave up the ghost (dodgy fan). I tried replacing card with an old Hercules 3d prophet II MX that I had - no luck - I think something "bad" may have happened in trying to use that card...

This morning I installed a new nvidia 7600GS card - but no joy booting into the graphic desktop.

Have removed the ATI driver and downloaded the nvidia driver but nothing.

I have tried "sudo dpkg-reconfigure -phigh xserver-xorg" from the  second boot option that takes me into the console. Nothing.

Whatever it is that is wrong is also blocking the 6.06 CD from running in a graphic mode.  (All works fine in XP - so I know the graphics card is good)

Any ideas - anyone?! :-k 

Nick

---

