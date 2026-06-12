---
title: "Ubuntu completly crashed and would no longer boot"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Native Dialect on 2007-03-12
After spending four hours merely trying to figure out on my own, and with minimal help, how to  change my resolution settings from the seemingly permanent default of 640x480, I finally came across a script line to insert in the terminal, that gave me access to a section about my video settings. Upon attempting to add a line to give a new bit depth and resolution (32 bit, 1024x768), I found that my computer would no longer boot Linux, when I tried to restart the machine. 

Needless to say, I am reinstalling Ubuntu as I type this. I really want to use Ubuntu, but I really need some help. I've tried downloading drivers from Intel's site, i've tried installing drivers with the Synaptic Manager. The only thing that seemed to be a step in the right direction, was the ability to modify the text in the terminal...but I messed that up. Can anybody help me please?

---

### Post by igknighted on 2007-03-12
32bit is a bit of a misnomer.  It doesn't really exist.  Windows claims to use it, but in reality it is no different than 24bit.  Linux doesn't even pretend to do 32bit, so you need to remove this mode as it will make xorg rather unhappy.  Try booting into recovery mode and editing xorg.conf to get rid of it.

---

### Post by Native Dialect on 2007-03-12
Well Recovery Mode wasn't working, so I just reinstalled. That is one thing I love about Linux...the installtion is small (at least for Unbuntu). So now that I have the defaults again, what do I do so that I can access the full 1024x768 that my monitor (Sony SDM M51) supports, rather than the limited 640x480 that I am stuck with. I'm in dire need at this point, because I don't want to crash the OS again.

---

### Post by shareMenaPeace on 2007-03-12
edit xorg.conf - open a terminal and run

```
gksudo gedit /etc/X11/xorg.conf 
```

*Note all in linux is case sensitive*
Than scroll down the file once open and edit the screen section.

Example - the bold parts are intresting for you put the resolution you can use. If you wrong xserver will just ignore the resolution.
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
**    DefaultDepth    24**
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "backingstore" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"
   #Option         "DRI" "true"
  [B]      SubSection     "Display"
    Depth       1
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"  "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection[/B]
EndSection
```

---

### Post by Native Dialect on 2007-03-12
Thank you Sharemena...I believe I have the basic concept down. So my xorg looks like this

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SDM-M51"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SDM-M51"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
EndSection


If I am understanding this correctly, the part down where it says "Depth    24" i'm going to change the modes? I assume that I am going to be placing the 1024x768, inside of the paranethsis for 640x480? Or am I replacing all of the modes, with just that number?

---

### Post by igknighted on 2007-03-12
The default 24 means that it will default to 24bit color depth.  So you only NEED to add "1024x768" in the subsection with depth 24.  Also, add it first in the line.  It likes to default to the first one in line usually.  You don't need to replace any, just add it in front of the first resolution, and leave a space in between.  In fact, most of those color depth modes are not needed, so you can ignore them.  Just worry about the depth 24 one, as that is the relevant one.

---

### Post by STREETURCHINE on 2007-03-12
put   "1280x800" if that is the resolution you want in front of all of them and save

dont forget to 
                         ```
sudo apt-get update
```

before you shut down

---

