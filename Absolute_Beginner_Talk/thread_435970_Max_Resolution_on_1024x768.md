---
title: "Max Resolution on 1024x768 ?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by NovaNine on 2007-05-07
Hi guys.
I just upgraded to Feisty Fawn. And I can't get my resolution higher than 1024x768 
How do I fix this ? And where do I get the latest drivers for my ATI card ? (ATI Radeon 9600)

Thanks.

---

### Post by Marshalus on 2007-05-07
Have you tried the Restricted Driver Manager?

I have an x1600 that I can't get to work, default has 1024x786 resolution in 7.04 (but 1280x1024 in 6.10) however when I install the drivers I get a black screen of death instead of a login prompt when restarting X.

---

### Post by Iarwain ben-adar on 2007-05-07
First step,
search...

[http://ubuntuforums.org/showthread.php?t=435715&highlight=resolution](http://ubuntuforums.org/showthread.php?t=435715&highlight=resolution)

[http://ubuntuforums.org/showthread.php?t=434756&highlight=ati+driver+installation](http://ubuntuforums.org/showthread.php?t=434756&highlight=ati+driver+installation)


Iarwain

---

### Post by NovaNine on 2007-05-07
Is there anyway I could fix this without converting to the fglrx drivers ? Because they won't work with "the cube"...

---

### Post by fakie_flip on 2007-05-07
> **NovaNine said:**
> Hi guys.
I just upgraded to Feisty Fawn. And I can't get my resolution higher than 1024x768 
How do I fix this ? And where do I get the latest drivers for my ATI card ? (ATI Radeon 9600)

Thanks.

This usually fixes resolution problems.

sudo dpkg-reconfigure -phigh xserver-xorg

Then push control alt backspace at the same time.

System>Administration>Restricted Drivers Manager

If that doesn't work, you may look here for other ways of installing the driver.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by NovaNine on 2007-05-07
> **fakie_flip said:**
> This usually fixes resolution problems.

sudo dpkg-reconfigure -phigh xserver-xorg

Then push control alt backspace at the same time.

System>Administration>Restricted Drivers Manager

If that doesn't work, you may look here for other ways of installing the driver.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But doesn't this mean changing drivers ? Which would mean I'd lose the cube ?

---

### Post by fakie_flip on 2007-05-07
> **NovaNine said:**
> But doesn't this mean changing drivers ? Which would mean I'd lose the cube ?

No, you wouldn't lose the cube. The cube would work better with those drivers. Using the Restricted Drivers Manager is the best way in Feisty to install the drivers for your video card. It is easy for beginners.

---

### Post by NovaNine on 2007-05-07
OK. I've switched drivers.

I still can't change the resolution, and the cube disappeared. And when I go to the desktop effects menu, it tells me : "The Composite extension is not available"

What's wrong ?

---

### Post by fakie_flip on 2007-05-07
If you are having problems with the new driver, you can switch back with Restricted Drivers Manager to your old driver. If that doesn't work you can switch back by restoring your old xorg.conf. Use this to see if there was a backup created of your xorg.conf. Sorry, I don't know much about Compiz and Beryl, so I can't help you with it, but there are people who can.

ls /etc/X11/

---

### Post by MiniMe on 2007-05-07
By coincidence I just posted a thread on how I was able to get higher resolutions with my ATI card and Feisty. Check out this thread if you like:

[http://ubuntuforums.org/showthread.php?t=436083](http://ubuntuforums.org/showthread.php?t=436083)

---

### Post by freebird54 on 2007-05-07
There are 2 ways to have the cube.  Neither of them has any trouble with different resolutions.  On Feisty I would suggest that you stick with the open source drivers that were loaded in the first place - as there are fewer 'other' issues than with the fglrx drivers to get 'the cube'.

The most likely culprit for the limited choice of resolutions is the 'Monitor' definition.  If you get the correct HorizSync and VertRefresh settings, then add in the resolutions you want, you should have them after an 'X' restart <ctrl><alt><backspace>.  The alternatie to that is the **sudo dpkg-reconfigure xserver-xorg** command - as was earlier stated.  here is a guide that will explain it:  [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

If you use the fglrx drivers, to get the cube you would have to run an XGL session - which involves quite a bit of setup, and loses you the ability to run some other 3d things (mainly games).  If you want to anyway - I can show you that setup too... :)

If more troubles - just post...

---

### Post by NovaNine on 2007-05-07
Hi and thanks for all the info.
I have reverted back to the default ati drivers I.E I've unchecked the Ati accelerated graphics driver box in the "Restricted Drivers" menu...

Now,when I try to get in "Desktop Effects", it tells me : "The Composite extension is not available"

What has gone wrong ? This didn't happen before I changed drivers...

---

### Post by bobplano on 2007-05-07
i don't know why don't you check for a section like this```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```
and if it's there get rid of it or if it isn't then add it

---

### Post by freebird54 on 2007-05-07
More than likely you have entries in your xorg.conf that do such things to you.  They were needed with the other driver - but not now.  Unfortunately, you need to go through and edit the xorg.conf to match up with what you are now running.  Feel free to post your xorg.conf file here - and I could look through it and show you any needed changes.  Or - if you prefer, I could post a working file (from my system) that might be close enough (apart from monitor specs) to use directly.  Let me know which.. :)

( you will note in my sig that I have a card using the same chipset - so I have SOME idea :)

---

### Post by alienexplorers on 2007-05-07
Have you tried setting up a modeline ([http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)) in the monitor section of your xorg.conf file.

Run gksudo gedit /etc/X11/xorg.conf

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Delta"
    ModelName      "Delta DE-570 BA"
    HorizSync       30.0 - 70.0
    VertRefresh     60.0 - 120.0
        [COLOR="Red"]Modeline       "1280x1024_65.00"  119.40  1280 1368 1504 1728  1024 1025 1028 1063 -HSync +Vsync[/COLOR]
    Option         "DPMS"
EndSection

Save your xorg.conf.... Hit ctrl+alt+backspace.... Relogin back in.... Check for proper screen size and refresh rate.

---

### Post by freebird54 on 2007-05-07
BTW:  to post this file, in case you haven't done that yet...Open an Applications->Accessories->Terminal, and enter the following:

```
cat /etc/X11/xorg.conf
```

then highlight it, and copy it.  Paste it into your reply. Highlight it again, the click the # in the button bar above your text.  This will put it into a 'code' box...

Just in case :)

---

### Post by brentoboy on 2007-05-07
I've seen this in several places, it is the plague of feisty.  For whatever reason, it seems that in a lot of cases, the detected refresh rates for monitors is lower than it should be.

It isnt your drivers or anything like that, you can get high resolution on both the restricted and the free version of the drivers.

what you need to do to fix it is to find the section in your /etc/X11/xorg.conf file that talks about your monitor, and add lines for horizontal and vertical refresh rates.
feisty configured mine like this:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

```
and it should have been this:   ****DO NOT JUST PLUG THIS IN, IT IS AN EXAMPLE*****
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

```

after I fixed that, it popped me up to 1600x1200 without any issues at all (and no messing around with drivers either)

the thing is, (and probably this is why feisty underestimates these numbers) ---  if you "overclock" these numbers above what your monitor is made for, that can be... bad.  like, popping sounds and smoke and what-not.

what you need to do is look up your monitor on the internet at the manufacturer's website, and get the exact refresh rates. and then fill them in.  your monitor's exact model number (usually on back) is what I would google with first.  (if you cant find it on the official website).

magic marker those numbers on the back of your monitor.  You never know when you will want them again.

---

### Post by NovaNine on 2007-05-08
> **freebird54 said:**
> BTW:  to post this file, in case you haven't done that yet...Open an Applications->Accessories->Terminal, and enter the following:

```
cat /etc/X11/xorg.conf
```

then highlight it, and copy it.  Paste it into your reply. Highlight it again, the click the # in the button bar above your text.  This will put it into a 'code' box...

Just in case :)

Here is the file :)

```
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
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI RADEON 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI RADEON 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

Thanks for your help :D

---

### Post by freebird54 on 2007-05-08
OK - this is painfully generic! :)  I will post a few sections of mine, along with** bolded** bits (to add) and *italicized* bits (to change to match your hardware).

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
[B]	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"[/B]
	BusID		"PCI:1:0:0"
EndSection
```

As you can see - a few things to add here - mostly to enable Desktop Effects (cube etc)

```
Section "Monitor"
	Identifier	"Samsung 900IFT"
	Option		"DPMS"
[I]	HorizSync	28-100
	VertRefresh	50-160[/I]
EndSection
```

As brentoboy said, you **MUST** have correct values for **YOUR** monitor entered here.  With what you have in your current file, 1024x768 is about all it can do.  *IF* your monitor can handle numbers like mine, you can get 1600x1200 (or more) if you should happen to want it.  However - using numbers too big for your monitor can lead to the permanent loss of the *magic blue smoke* that is hidden in your monitor :)  If you can't locate specs for it, post your monitor model number, and we'll go looking for more info.
```

Section "ServerLayout"
**	Option          "AIGLX" "true"**
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

just add in the AIGLX line...
```

Section "Extensions"
*	Option "Composite" "Enable"*
EndSection
```

This needs to be 'turned back on' to work properly with the open source driver - and run the cube.

Hopefully this will get everything back to running the way that it can - but we need the 'numbers' for your monitor to solve the original problem...

PS:  If you really can't find the monitor numbers, you need to run the command mentioned before:
```

sudo dpkg-reconfigure xserver-xorg
```

and choose either 'medium' or 'advanced' when trying to detect the monitor.  Make sure to enter the 'best' resolution information with YOUR choice of best from within the capabilities of your monitor.  On mine, I could run higher - but I stick to 1280x1024 at a decent refresh rate.  Here is a link that walks you through the dpkg command - although answering with defaults will get you through all but the video driver, and resolution questions..  LInk: [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

OK - there ya go!  :)

EDIT:  BTW - cut and paste works more reliably for adding stuff than typing it in.  Just make **SURE** to change the monitor values to match **YOURS**  ('nuff reminders?) :)

---

### Post by NovaNine on 2007-05-08
GOT IT :D

Thanks a lot for all of the help :)

---

### Post by freebird54 on 2007-05-08
Awwright!  Glad you got it!  Now - one last bit of housekeeping...

If you could go back to your original post, choose EDIT, and then click on ADVANCED, then select RESOLVED - the thread will become more useful for those who are searching for answers down the road.  OK?

Enjoy!

---

