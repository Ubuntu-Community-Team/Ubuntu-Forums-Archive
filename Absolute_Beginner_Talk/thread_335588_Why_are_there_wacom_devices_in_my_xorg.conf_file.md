---
title: "Why are there wacom devices in my xorg.conf file?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tanguyr on 2007-01-10
Hello,

So i'm taking my very first steps with linux, using kubuntu 6.10 on a new Asus laptop. So far, i have to say i am *very* impressed with the quality level, and i'm having a blast and learning all kinds of interesting things.

Here's my question: why does my xorg.conf file contain references to wacom devices [1]? I don't have any wacom tablet or suchlike connected, and my laptop is not a tablet or touchscreen model. I found out (the hard way;) ) that removing these sections from the file causes a strange error: kubuntu "hangs" at the end of the startup sequence (i.e. blue bar gets almost all the way to the end, but i never get prompted for my password... X not starting?). I have to reboot in safe mode and restore a backup of this file (see, i told you i was learning :mrgreen: )

It's not that it's causing any kinds of problems, i'm just the curious type. BTW, if it's any use, i have an ati card on this laptop (i just mention it because searching the forums for "wacom" shows me that lots of people with ati cards and drivers have wacom sections in their xorg.conf files... but i'm guessing it's not related)

Anyhow, if anybody knows...

Regs,
/t

[1] here are the sections in question:
```

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

```

---

### Post by viciouslime on 2007-01-10
I am intrigued by this too, it is like this on ALL my ubuntu installs, is it just a compatibility thing?

---

### Post by doobit on 2007-01-10
I think it's because there is no automatic setup for Wacom devices, so the developers included a standard in the configuration file. If you don't have the device, then it throws up a meaningless error and moves on to the next thing. Nothing to worry about.

---

### Post by Lord Illidan on 2007-01-10
You can remove it safely if you know what you are doing...but otherwise it doesn't impact normal usage.

---

### Post by NT4usB on 2007-01-10
You can remove (or just comment out) but remember to also remove (comment) them out of: ```
Section    "ServerLayout"
```

---

### Post by gurnemanz on 2007-01-10
This would be very good news for me. I'd like to be able to use my tablet, and was concerned about locating a driver.

Is the driver also contained in Xubuntu?

---

### Post by nkkromhof on 2007-01-10
> **gurnemanz said:**
> 

Is the driver also contained in Xubuntu?


There's a bunch of people using Wacom tablets on (X)ubuntu, usually requires some tweaking, personally I didn't have to install the 3rd party Linuxwacom drivers. Though I needed an additional (user made) program to be able to use the Expresskeys on my Graphire4's pad.

Your mileage may vary, depending on your tablet and forum searching abilities :o 

Good luck getting it to work!

---

### Post by tanguyr on 2007-01-10
> **NT4usB said:**
> You can remove (or just comment out) but remember to also remove (comment) them out of: ```
Section    "ServerLayout"
```

Perfect! Thanks for the tip.

---

