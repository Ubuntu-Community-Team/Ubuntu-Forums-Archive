---
title: "[SOLVED] illegible error message at boot"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by bric on 2008-01-16
I have a new 64bit install of ubuntu that has been working well for about a week.  It's connected to a LCD HDTV as sort of an HTPC.  Due to problems with the bluetooth mouse/keyboard I was forced to shut down 'the bad way' (powering off without shutting down).  That's a whole other story ... still unresolved.

Anyway, starting up again after this unfortunate event presented me with an error message on screen that I couldn't read.  It looks like it's in X before the 'graphical styling' of the window manager has been applied (e.g., it still has that X shaped cursor).  I can't read the message because whatever resolution this initial incarnation of X is using is just too darned small.

To illustrate:
[IMG]http://aycu29.webshots.com/image/39148/2003153649553468729_rs.jpg[/IMG]

Does anyone know what this message might be?
The left button starts a dialogue box with a bunch of other illegible writing (presumably regarding monitors and resolution though).  The center button gives a command line.  The right button boots ubuntu at 640x480.  Similarly, canceling the dialogue box (from the left button) also gives 640x480.

The 640x480 mode only has that as the resolution under system > prefs > screen resolution (or whatever the menus are).  1920x1200 is no longer an option. Also, if I connect a monitor then it boots fine, no error message, but it comes back when reconnected to the TV (grrrrrr).

Can I alter the default resolution of X so that I can read this message? Or...???

---

### Post by dstew on 2008-01-16
It is possible that your X-window server configuration file was messed up, so now the X-server cannot do high resolution. You can try to reconfigure the X-server. First, back up your xorg.conf with```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Then enter the command to reconfigure the X-server:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bric on 2008-01-16
I tried this and no luck.  I had a look at the new xorg.conf and it did have sections that indicated that there should be hi-res modes available -- from what I understood of it.

```

Section "Device"
    Identifier    "Intel Corporation 965 G1 Integrated Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "TSB-TV"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 965 G1 Integrated Graphics Controller"
    Monitor        "TSB-TV"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1920x1080" "720x480" "640x480"
    EndSubSection
EndSection
```

However, it still presents me with the same dialog box and the same behaviour.  The motherboard is an Asus P5E-VM HDMI (G35 with integrated GMA X3500) but I assume the detection above as a 965 chipset is by design... ?

---

### Post by dstew on 2008-01-16
Here is a comment from a page about this chipset and Linux:

> Linux X.Org driver: Supported by Xorg [1]. The driver supports hardware accelerated 3D via the Direct Rendering Infrastructure (DRI), but only in depths 16 and 24.

Version 2.1.1 of the driver fixes a TV output problem. Use xrandr to view the enabled screens in X.

Do you have the version 2.1.1 intel driver installed? [Here]("http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100") is the page I found. [Here]("http://packages.ubuntu.com/gutsy/x11/xserver-xorg-video-intel") is the Ubuntu package.

---

### Post by bric on 2008-01-16
It was a base installation of 64bit Ubuntu, with a few firefox plugins and stuff like that.... and some files.  So I'm not sure which driver version it was/is.  I'll have a look at the links you sent.

Is there a way to tell which driver version is installed?  (config file(s) somewhere?)

---

### Post by Digger78 on 2008-01-16
search in synaptic package manager for **xserver-xorg-video-intel**

it will show what version you have installed and if there is an upgrade available

---

### Post by Paulmd on 2008-01-16
> **bric said:**
> I have a new 64bit install of ubuntu that has been working well for about a week.  It's connected to a LCD HDTV as sort of an HTPC.  Due to problems with the bluetooth mouse/keyboard I was forced to shut down 'the bad way' (powering off without shutting down).  That's a whole other story ... still unresolved.

Anyway, starting up again after this unfortunate event presented me with an error message on screen that I couldn't read.  It looks like it's in X before the 'graphical styling' of the window manager has been applied (e.g., it still has that X shaped cursor).  I can't read the message because whatever resolution this initial incarnation of X is using is just too darned small.

To illustrate:
[IMG]http://aycu29.webshots.com/image/39148/2003153649553468729_rs.jpg[/IMG]

Does anyone know what this message might be?
The left button starts a dialogue box with a bunch of other illegible writing (presumably regarding monitors and resolution though).  The center button gives a command line.  The right button boots ubuntu at 640x480.  Similarly, canceling the dialogue box (from the left button) also gives 640x480.

The 640x480 mode only has that as the resolution under system > prefs > screen resolution (or whatever the menus are).  1920x1200 is no longer an option. Also, if I connect a monitor then it boots fine, no error message, but it comes back when reconnected to the TV (grrrrrr).

Can I alter the default resolution of X so that I can read this message? Or...???


I'm pretty sure the last 3 words on the top line are "high graphics mode"

---

### Post by bric on 2008-01-16
Thanks, that was easy.  

It is indeed 2.1.1 that is installed.

Perhaps I'll just have to get gutsy (no pun intended) and play with that dialogue box that comes up at boot (i.e., button number 1's dialogue with the [presumably] display related options).

(time passes)

Well, I wish I had posted that and given someone the opportunity to scream, "No you fool! Don't do it!"

Anyway, I, uh, chose one of the options that I couldn't read and apparently it did choose a different video mode for me.  Just one that I can't read ... :)

Doh! 
:)

(bit more time passes, hence the edits)

 I found a command prompt even though things are crazy on the screen (using ctrl-alt-Fkeys) and restored the backup of xorg.conf .

Now I'm back to the original problem (and not messing around as recklessly).

Here's a sample of the dialogue box I get after clicking on the first (left) button.

[IMG]http://aycu25.webshots.com/image/41624/2003081252649660969_rs.jpg[/IMG]

Perhaps that will give someone an idea.  
I got my more screwed up screen (instead of the 640x480 screen) by choosing the lower monitor and the bottom option (default choice) from the radio buttons.

---

### Post by bric on 2008-01-16
Yeah, maybe "ubuntu is missing a high graphics mode" or something similar?

---

### Post by Paulmd on 2008-01-16
> **bric said:**
> Yeah, maybe "ubuntu is missing a high graphics mode" or something similar?

Pretty sure the first word isn't ubuntu. (there isn't a tall letter in the right spot (no 't')). The 'b' would fit, tho'.

'missing', 'running' are possibles for the 2nd long word. 'missing' is a stronger candidate, as it's a more error-message sounding word.

Neither of those phrases turned up anything useful on google.


how about attempting a screenshot with the printscreen command? this should save a file to the desktop, which may be more legible. hopefully.

---

### Post by bric on 2008-01-16
> **Paulmd said:**
> 
how about attempting a screenshot with the printscreen command? this should save a file to the desktop, which may be more legible. hopefully.

That's a possibility, though I wouldn't be hopeful because it's prior to the login ... meaning that X hasn't really fully loaded yet.

---

### Post by bric on 2008-01-16
I tried a 'startx' from the command prompt ('center button') and got this message:

[IMG]http://aycu13.webshots.com/image/41892/2005310796783863336_rs.jpg[/IMG]

It seems that the config in xorg.conf is not correct.  Perhaps that was obvious.

---

### Post by Digger78 on 2008-01-17
can you do 

```
cat /etc/X11/xorg.conf
```

and take a shot of the "monitor" "device" and "screen" sections

you could also try removing **xserver-xorg-video-intel** and then reinstalling it.

---

### Post by bric on 2008-01-17
Per request, this is from xorg.conf (after "dpkg-reconfigure xserver-xorg"):

```
Section "Device"
    Identifier    "Intel Corporation 965 G1 Integrated Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "TSB-TV"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 965 G1 Integrated Graphics Controller"
    Monitor        "TSB-TV"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1920x1080" "720x480" "640x480"
    EndSubSection
EndSection
```

I know it has different modes here but I tried the supposed shortcut (ctrl-shft-+ was it?) to cycle the resolutions in X and no change (stays at 640x480) so something in that illegible menu might be loading an alternate config? Or perhaps a setting is wrong here.

I'll try uninstall-reinstall now...

---

### Post by Digger78 on 2008-01-17
hold on,

```
sudo nano /etc/X11/xorg.conf
```

add the bold text

```
Section "Monitor"
    Identifier    "TSB-TV"
    Option        "DPMS"
    [B]HorizSync 28-72
    VertRefresh 43-60[/B]
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 965 G1 Integrated Graphics Controller"
    Monitor        "TSB-TV"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1920x1080" **"1024x768"** "720x480" "640x480"
    EndSubSection
```

Notice the capital H & S in HorizSync
Notice the capital V & R in VertRefresh

save it  

then try 

```
startx
```

---

### Post by bric on 2008-01-17
I used the synaptic package manager to re-install, then rebooted -- no change.
I uninstalled.  Rebooted.  Reinstalled.  Rebooted.  -- no change.
tried dpkg-reconfigure -phigh xserver-xorg again --no change.

and

tried the additions (HorizSync etc) to xorg.conf and no luck there either.  'startx' failed with the same message(s) as before (see top of this page).  Tried rebooting and it has the same  dialog box -- I wish I could read what it (and the subsequent configuration dialog) says.

---

### Post by Digger78 on 2008-01-17
Could you post your entire xorg.conf

```
cat /etc/X11/xorg.conf
```

also the output from

```
lspci
```

---

### Post by bric on 2008-01-17
the complete xorg.conf

```
# xorg.conf (xorg X Window System server configuration file)
#
# snipped out comments

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation 965 G1 Integrated Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "TSB-TV"
    Option        "DPMS"
    HorizSync 28-72
    VertRefresh 43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 965 G1 Integrated Graphics Controller"
    Monitor        "TSB-TV"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1920x1080" "1024x768" "720x480" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
EndSection
```



lspci yields:

```

00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

---

### Post by Digger78 on 2008-01-17
A couple of things to try.

remove    "1920x1080" from the modes line.  (dont put it back for now, even if it fails)

if that doesnt work change the BusID to

BusID        "PCI:0:2:**1**"

if you have the desktop loaded use 

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by bric on 2008-01-17
No luck with either of those unfortunately.

I've left 1900x1200 off the list.  Should I return the BusID to the original?

---

### Post by Digger78 on 2008-01-17
I'm not sure which one is the original

the last pic you posted shows PCI:0:2:1 but then your xorg.conf changed to PCI:0:2:0

personally i would be inclined to changed it back to PCI:0:2:0

I'll let you know if i come across a solution but for now,  i dont know what else to try.

Is it a TV your connected to or a monitor?

---

### Post by bric on 2008-01-17
> **Digger78 said:**
> I'm not sure which one is the original

the last pic you posted shows PCI:0:2:1 but then your xorg.conf changed to PCI:0:2:0

personally i would be inclined to changed it back to PCI:0:2:0


Yes, I'll change it back to PCI:0:2:0 (the original)  - the other change was at your suggestion.

> **Digger78 said:**
> 
I'll let you know if i come across a solution but for now,  i dont know what else to try.

Is it a TV your connected to or a monitor?

It's connected to a TV (and was working very nicely for a while...).

Thanks for all the suggestions.  I may hit up a fellow "Asus p5e-vm" user for an xorg.conf file.  Or perhaps I'll return to trying to make those dialog boxes legible -- maybe with some default settings for X.  And there's always re-installation if that's not too much of a surrender.

---

### Post by bric on 2008-01-18
Problem solved.  Though I don't know how.

I tried another modification of the xorg.conf that another p5E-vm user kindly sent me.  It failed to do anything so I restored the xorg.conf backup I had and rebooted.

This time at the first dialogue I clicked the button to get the graphics dialogue.  Then I randomly chose some settings.  It resulted, as expected, in an unusable screen (couldn't make out anything).  So I did ctrl-alt-f1 and by memory restored the xorg.conf.bak I'd made (again) and did a 'sudo reboot' (did this all without seeing anything so perhaps that's the solution -- do it blindfolded).

When the system came back up there was no dialogue box ... it went straight to the login screen at high resolution this time round (great cheering was heard).  Everything is working fine again.  I've backed up the working xorg.conf again just in case though it appears identical to the original backup file.

Weird!

I wish I could diagnose what happened.

One detail: the screen resolution options under "system > prefs > screen res" are now only the 1920x1200 and 640x480... I think there were more previously (though I couldn't be sure).

---

### Post by Digger78 on 2008-01-18
Excellent, I'm glad you got it fixed.

Any chance you could attach you Xorg.conf to this thread. (i'm just curious :) ) 

Dont forget to mark the thread solved (thread tools) ;)

---

### Post by bric on 2008-01-19
Yeah, fixed ... but not exactly solved.  I'm still left puzzled.

The xorg.conf is very generic (even more-so than what was there after dpkg-reconfigure was run) and this was restored from my original backup (which was exhibiting the same behaviour).

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
	Identifier	"Intel Corporation 965 G1 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 965 G1 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

Thanks for all your help (to everyone) though I don't know who deserves the credit, if anyone. ;)

But I guess it's solved (if general feelings of happiness and contentment are any judge).

---

### Post by bric on 2008-06-02
For any who might be interested (or encounter the same problem) I discovered that the illegible dialogue boxes I was seeing were in fact from the xorg.conf configuration GUI.

You can see gui screenshots here: [http://fosswire.com/2007/08/17/ubuntu-getting-xorgconf-gui/]("http://fosswire.com/2007/08/17/ubuntu-getting-xorgconf-gui/").

Apparently, ubuntu didn't like the existing config and started the GUI at boot ... which was no help since I couldn't read any of it.

<insert smiley with storm-cloud raining on me, or perhaps with stormy features here>

---

### Post by bric on 2008-06-14
Aaaaand... I got the same problem again.

This time I found an easy solution (annoyingly easy considering the time spent trying to solve it).

I unplugged and re-plugged the hdmi cable which came out from my pc to my hdtv monitor.  This seemed to kickstart the motherboard so that it queried the monitor for resolution settings again (or something) and this time it autodetected properly.

Hurray! (and now I know to manage my crashes with an alt-sysRq REISUB so hopefully it won't happen again)

---

