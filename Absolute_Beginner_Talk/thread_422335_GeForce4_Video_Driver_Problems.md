---
title: "GeForce4 Video Driver Problems"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by flyboy284 on 2007-04-25
Hey guys, I have an Athlon XP 3000, 512MB RAM with a GeForce4 MX440 AGP 8x.
I have been trying to get the video drivers it work but each time I install the driver I get either a blank screen on reboot or a BSOD telling me that the X server failed to start.
I have tried the following drivers _nvidia-glx,_  _nvidia-glx-legacy_,  and the _nvidia-glx-new_ all install with Synaptic. I attempted to use Envy as well but it didn't work
either. I replaced the xorg.conf file with the "sudo dpkg-reconfigure -phigh xserver-xorg" command in the recovery mode after each driver failure.

Any advice will be appreciated.
thanks
Matt


P.S. Is this system even capable of XGL effects?

---

### Post by xopher on 2007-04-25
First, the error screen that X throws at you when it fails to start, is nothing like the BSOD from 'the other' OS. X actually tells you what's wrong, and sometimes even tells you exactly what to do.

So, could you please tell us what the error is?

The log file can probably be found here: /var/log/Xorg.0.log.old

(.old, because you changed the driver, and didn't start X with 'nvidia'.)

---

### Post by flyboy284 on 2007-04-25
The blue screen that came up when X failed to start didn't give much info. It said: [COLOR="Red"](EE) No devices detected.[/COLOR]
The Xorg.0.log.old file gave a lot of information, but the only error type info I could find was:
```

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```
and
```

(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

I hope this helps.

---

### Post by slayerboy on 2007-04-25
There was another post almost exactly identical to this:

[http://ubuntuforums.org/showthread.php?t=420276](http://ubuntuforums.org/showthread.php?t=420276)

Of which, I have created a "HowTo" topic for this possible issue:

[http://ubuntuforums.org/showthread.php?p=2533441](http://ubuntuforums.org/showthread.php?p=2533441)

---

### Post by flyboy284 on 2007-04-25
I have tried using the how-to but it still is not working for me. When I do the "_sudo aptitude remove envy linux-restricted modules_" command; 
it doesn't actually remove anything, it says it could find it but displays everything with _envy_ and _lunix-restricted modules_ in it.
Is it supposed to remove the modules from the PC?

When i tried it with the nvidia-glx-new driver i got an API mismatch error:
"_API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9631._"

When I tried the nvidia-glx driver I only got a blank screen on reboot.

---

### Post by slayerboy on 2007-04-26
That card is a legacy card, try installing nvidia-glx-legacy and it should work.  It looks like envy and restricted-modules are already removed.

When you type the sudo aptitude remove envy linux-restricted-modules and it listed the items, did any of them have I's to the left of them?

---

### Post by Kobalt on 2007-04-26
There is a know problem using the nvidia drivers with the GeForce MX440. The fix is quite simple though : you must install the drivers 9631 (that is to say the *nvidia-glx* package) and modify manually your xorg.conf file to add this line in your Device section : 
> Option "UseDisplayDevice" "DFP"
Restart, and that should do it.

PS : you can have the *linux-restricted-modules* package installed, it's not the problem

---

### Post by flyboy284 on 2007-04-27
Still no go.

I add the option line to the xorg file and when I rebooted I got the API mismatch error. I thought that wasn't a fair test.
Not knowing how to fix the API mismatch error, I reinstalled Ubuntu, Installed all the updates, used synaptic to install the video driver, edited the xorg file then rebooted.
I get only a blank screen on startup. I didn't hear the welcome screen sound either.

---

### Post by flyboy284 on 2007-04-28
Hey Guys,
I finally got it to work. I'm not sure What actually did it but I added these lines to my device section.

```

        Option		"NvAGP"	"1"
	Option		"AllowGLXWithComposite"	"True"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"True"
	BusID		"PCI:1:0:0"
	Option		"UseDisplayDevice"	"DFP"

```
The BusID  was changed from: "PCI:0:5:0" to "PCI:1:0:0", which made it actually "see" the device.

I want to thank everybody for their help, it was much appreciated!

---

### Post by DuboisS on 2007-06-06
Kobalt resolved my problem as well:
[INDENT]
There is a know problem using the nvidia drivers with the GeForce MX440. The fix is quite simple though : you must install the drivers 9631 (that is to say the nvidia-glx package) and modify manually your xorg.conf file to add this line in your Device section :
**Option "UseDisplayDevice" "DFP"**[/INDENT]

My Xorg were eating 97% or more CPU while trying to play any kind of video. It occurred after a WMV codec installation, automatically done by Totem.
Now, it's fixed.

Thanks!

Sylvain D.

---

