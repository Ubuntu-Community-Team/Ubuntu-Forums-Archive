---
title: "Ubuntu just died big time"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-02
I was using firefox/kate selecting my courses for next semester - and ubuntu shuts off - goes to the fullscreen bash (like if you hit control + alt + F2 - flickers for a bit - then goes back to the login screen.  Everything I was currently working on was destroyed.

What the **** happened?

Does this have any error logs or anything?

It didn' thave enough time to restart - it was just like a restart except it only took 15 seconds to from the time it went black to the time it showed login screen?

This is the second time this happened in 2 days, the first resulted in my video drivers eating themselves.

If I wanted problems every day I woulda stuck with windows :(

Anybody have any clue what I could do?

---

### Post by jose158 on 2008-02-02
Hmm something similar to this happened to me twice. For me it turned out the fan stopped working and the processor overheated. Have an expert (Or you if you know how to check) look at it.

---

### Post by ~LoKe on 2008-02-02
Your xserver restarted.  Look in /var/log/Xorg.0.log or /var/log/Xorg.0.log.old

---

### Post by Syndacate on 2008-02-02
> **~LoKe said:**
> Your xserver restarted.  Look in /var/log/Xorg.0.log or /var/log/Xorg.0.log.old

I found this at the bottom of **Xorg.0.log.old**

```

Fatal server error:
Caught signal 11.  Server aborting

```

How do I make sure X is up to date?

---

### Post by kellemes on 2008-02-02
/var/log/messages would be more interesting I guess..
"Server aborting" is not very informative.. ;-)

---

### Post by ed-koala on 2008-02-02
If your PC supports it,  use Synaptic to install X Sensors.  If you do have an overheating problem you'll be able to see the temp going up on your CPU.  Something handy to have even if that isn't the problem.  :)

---

### Post by Syndacate on 2008-02-02
> **ed-koala said:**
> If your PC supports it,  use Synaptic to install X Sensors.  If you do have an overheating problem you'll be able to see the temp going up on your CPU.  Something handy to have even if that isn't the problem.  :)

I don't think my PC supports it - when I open it up it just shows a blank/empty window.

[quote=kellemes]/var/log/messages would be more interesting I guess..
"Server aborting" is not very informative.. ;)[/quote]

```

Feb  2 15:26:21 syndacate kernel: [35824.066507] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Feb  2 15:26:21 syndacate kernel: [35824.066523] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Feb  2 15:26:21 syndacate kernel: [35824.066547] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

That's the only thing it has since 6am last night (when I went to sleep).

I think those logs are ABOUT the time when it happened - I can't say for sure but I'm pretty sure that's approx when it happened.

---

### Post by Syndacate on 2008-02-02
> **Syndacate said:**
> I don't think my PC supports it - when I open it up it just shows a blank/empty window.



```

Feb  2 15:26:21 syndacate kernel: [35824.066507] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Feb  2 15:26:21 syndacate kernel: [35824.066523] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Feb  2 15:26:21 syndacate kernel: [35824.066547] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

That's the only thing it has since 6am last night (when I went to sleep).

I think those logs are ABOUT the time when it happened - I can't say for sure but I'm pretty sure that's approx when it happened.

My friend said those are just Ubuntu starting back up - which would make sense since X Server crashed.

So I guess I have to ask now:

What's signal 11?

---

### Post by kellemes on 2008-02-02
It most probably has to do with your videodriver..

What's your card?
What driver do you have installed?
How does /etc/X11/xorg.conf look?

Edit: By the way.. browse /var/log/Xorg.0.log for (EE) and for (WW).. they can tell you more about the issue.
Or better yet.. post it.. and also xorg.conf

---

### Post by Alx c on 2008-02-02
It s probably and OS error, if it is lets hope it gets fixed for the next version

---

### Post by smartalecks on 2008-02-02
Are the visual effects turned on? Turn them off...

---

### Post by Syndacate on 2008-02-03
> **kellemes said:**
> It most probably has to do with your videodriver..

What's your card?
What driver do you have installed?
How does /etc/X11/xorg.conf look?

Edit: By the way.. browse /var/log/Xorg.0.log for (EE) and for (WW).. they can tell you more about the issue.
Or better yet.. post it.. and also xorg.conf

It's a PNY GeForce 7600GS - 512mb

This is the only thing in xorg.0.log that have (WW), no (EE)

```

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) NVIDIA(0): No valid modes for "1600x1200@65"; removing.

```

**xorg.conf** - One of my conf files had "nvidia" as the driver - it's a restricted driver that I'm using.  
```

# bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	RgbPath		"/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"vbe"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection
Section "Device"
	Identifier	"Generic Device"
	Driver		"::DRIVER::"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Generic Mouse"
EndSection

```

Hrm, I think I should just leave it alone - and if it does it again maybe try reinstalling X11 - unless there's anything out in the obvious that one of you guys can think of.

---

