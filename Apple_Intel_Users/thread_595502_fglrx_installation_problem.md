---
title: "fglrx installation problem"
date: 2007-10-28
forum: Apple Intel Users
---

### Post by Subversive_One on 2007-10-28
Hello all,

I'm brand new to Ubuntu, and I would greatly appreciate your help.  I'm having great difficulty installing ATI drivers.  Here's my set up:

Macbook Pro 17" C2Duo 2.16Ghz, ATI Mobile Radeon X1600.

I'm attempting to install by following this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

When I type this code:
> sudo apt-get install xorg-driver-fglrx

I get the following response:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx

I can't figure out what to do.  Please help.  Thanks in advance.

---

### Post by matthew.lns1 on 2007-10-28
Go to ATI's website. They have the driver there.

---

### Post by cyberdork33 on 2007-10-28
> **matthew.lns1 said:**
> Go to ATI's website. They have the driver there.

Don't do that, you should use the version in the repos. 

Are you connected to the internet? can you make sure to enable software sources in System > Adminstration > Software Sources.

---

### Post by Subversive_One on 2007-10-28
> **cyberdork33 said:**
> Don't do that, you should use the version in the repos. 

Are you connected to the internet? can you make sure to enable software sources in System > Adminstration > Software Sources.

Thanks for pointing me in the right direction, CyberD.  You're right, I didn't have the software sources enabled.

Now I've run into another problem... 

When I try to "Configure the Driver"...

> sudo aticonfig --initial

I get this error:
> Warning: Could not find configuration file
Please copy configuration file template to /etc/X11


Thanks in advance!

---

### Post by cyberdork33 on 2007-10-29
> **Subversive_One said:**
> Thanks for pointing me in the right direction, CyberD.  You're right, I didn't have the software sources enabled.

Now I've run into another problem... 

When I try to "Configure the Driver"...



I get this error:


Thanks in advance!

Well that is odd... it is looking for your xorg.conf, and it doesn't seem to exist.

Trying running this first:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```That should regenerate one for you.

---

### Post by Subversive_One on 2007-10-29
> **cyberdork33 said:**
> Well that is odd... it is looking for your xorg.conf, and it doesn't seem to exist.

Trying running this first:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```That should regenerate one for you.

Hi Cyber,

Thanks for all of your help!!! That last string of code seems to have helped quite a bit.  Now, when I run fglrxinfo, this is what I get:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37
```

So looks like something has finally installed!  Hooray!  Sort of...


---

When I go to System / Preferences / Appearance / Visual Effects...

I try to select "Extra" or "Custom,"  I get the following error message:

> The Composite extension is not available

---

Perhaps I'm going about this all wrong.  At the end of the day, I'm trying to get the nifty compiz effects.  Is there a better way to do this?

I've already run these:
```
sudo aptitude install compizconfig-settings-manager
sudo aptitude install emerald

```

But I still run into the "Composite extension is not available" error.

Any help is greatly, greatly appreciated.  Thanks again!

---

### Post by crazybrit4967 on 2007-10-29
> **Subversive_One said:**
> Hi Cyber,

Thanks for all of your help!!! That last string of code seems to have helped quite a bit.  Now, when I run fglrxinfo, this is what I get:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37
```

So looks like something has finally installed!  Hooray!  Sort of...


---

When I go to System / Preferences / Appearance / Visual Effects...

I try to select "Extra" or "Custom,"  I get the following error message:



---

Perhaps I'm going about this all wrong.  At the end of the day, I'm trying to get the nifty compiz effects.  Is there a better way to do this?

I've already run these:
```
sudo aptitude install compizconfig-settings-manager
sudo aptitude install emerald

```

But I still run into the "Composite extension is not available" error.

Any help is greatly, greatly appreciated.  Thanks again!

I'm not sure if it'll help or not, but try this: type sudo gedit /usr/bin/compiz, and add "fglrx" to the whitelist section (line 54), then try enabling it again.

---

### Post by cyberdork33 on 2007-10-29
you need to install XGL to do compositing with all of ATI's drivers (except the very latest, which are not really worth upgrading to at the moment).

```
sudo aptitude install xserver-xgl
```

---

### Post by Subversive_One on 2007-10-30
Hi Cyber,

Thank you for all of your help.  You've been extremely generous and helpful!!!

I thought I had everything up and running... but now I've run into another issue.

I'd like to set up WINE to play warcraft in Ubuntu.  Following these directions:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)


I get the following error from step 1:

```
bryan@ubuntu:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
bryan@ubuntu:~$ 
bryan@ubuntu:~$ 

```

Any ideas as to what is wrong?

Thanks again.

---

### Post by cyberdork33 on 2007-10-30
> **Subversive_One said:**
> Hi Cyber,

Thank you for all of your help.  You've been extremely generous and helpful!!!

I thought I had everything up and running... but now I've run into another issue.

I'd like to set up WINE to play warcraft in Ubuntu.  Following these directions:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)


I get the following error from step 1:

```
bryan@ubuntu:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
bryan@ubuntu:~$ 
bryan@ubuntu:~$ 

```Any ideas as to what is wrong?

Thanks again.
That is normal when running XGL. You do actually have direct rendering. Check 'flgrxinfo'. It should say that ATI is the vendor.

---

### Post by heatpumpcontrol on 2007-10-30
> **crazybrit4967 said:**
> I'm not sure if it'll help or not, but try this: type sudo gedit /usr/bin/compiz, and add "fglrx" to the whitelist section (line 54), then try enabling it again.

THAT WORKED!!!  Woooo hoooooo! thanks.

Sad .... didn't work. I will update when I find the fix..

SOLVED-- xserver-xgl as mentioned before works.. I've done two installs now on the same machine..(my errors) and it gives me the correct results.

---

### Post by Subversive_One on 2007-10-31
Hi CyberG,

I've got a different issue, that I was hoping you could help me work through...

I can't seem to access my track pad config.

I've tried to follow the directions here:

[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

But most of that information was already in my xorg.conf file.



When I go to System / Preferences / Touchpad, I get the following error message...

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

I've looked through the xorg.conf file, and I've already verified that SHMConfig is already set to "True."

Unfortunately, I don't know how to access the XF86Config.  Could you please give me a point in the right direction?  Thank you!

---

### Post by cyberdork33 on 2007-10-31
> **Subversive_One said:**
> Hi CyberG,

I've got a different issue, that I was hoping you could help me work through...

I can't seem to access my track pad config.

I've tried to follow the directions here:

[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

But most of that information was already in my xorg.conf file.



When I go to System / Preferences / Touchpad, I get the following error message...

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```I've looked through the xorg.conf file, and I've already verified that SHMConfig is already set to "True."

Unfortunately, I don't know how to access the XF86Config.  Could you please give me a point in the right direction?  Thank you!
You don't have XF86Config, you have xorg.conf. Can you post your xorg.conf?

---

### Post by Subversive_One on 2007-10-31
Thanks for looking at this Cyber!

here's my xorg.conf

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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        Option		"VertTwoFingerScroll"   "True"
        Option 		"SHMConfig"		"True"
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```



Here's something else odd, that I noticed...  When I go to System / Preferences /... all of the options in that pull down (such as sound, sessions, screensaver...) have a little icon next to it.  The "Touchpad" option does not have any icon at all.  Hope this info is helpful.

Thanks again!

---

### Post by cyberdork33 on 2007-10-31
> **Subversive_One said:**
> Thanks for looking at this Cyber!

here's my xorg.conf

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
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
        Option        "VertTwoFingerScroll"   "True"
        Option         "SHMConfig"        "True"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "fglrx"
    Busid        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    Horizsync    30-70
    Vertrefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
EndSection
Section "Extensions"
    Option        "Composite"    "0"
EndSection
```

Here's something else odd, that I noticed...  When I go to System / Preferences /... all of the options in that pull down (such as sound, sessions, screensaver...) have a little icon next to it.  The "Touchpad" option does not have any icon at all.  Hope this info is helpful.

Thanks again!
IDK. It looks good. can you try running gsynaptics from the terminal? You can also try qsynaptics.

---

