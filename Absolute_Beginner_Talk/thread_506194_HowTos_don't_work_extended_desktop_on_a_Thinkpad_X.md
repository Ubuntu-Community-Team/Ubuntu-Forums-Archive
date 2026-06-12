---
title: "HowTos don't work: extended desktop on a Thinkpad X31 + external monitor"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by jigantor on 2007-07-21
Hi all,

I've been trying to get an external screen working as an extended desktop on my IBM Thinkpad X31 - I followed the HowTo [here,]("http://sernaonubuntu.wikidot.com/multiple-monitors") which as far as I can tell is also consistent with [this]("http://ubuntuforums.org/showthread.php?t=301951&highlight=install+xinerama") HowTo, which seems to solve most other people's problems. But I just can't get it working - there seems to be no change from my out of the box setup (ie, I can have a the external monitor running as a clone, or have one but not the other, but not as an extended desktop). I can't find anybody else who seems to be having this problem - ie Xinerama apparently not changing anything. Here's the relevant bits of my xorg.conf:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
    	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000] 2"
	Driver		"ati"
	BusID		"PCI:1:0:0"
   	Option     	"Display" "CRT"
    	Option        "MonitorLayout" "CRT,LFP"
  	Screen        1
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
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

Section "Screen"
    Identifier    "External Screen"
    Device	  "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000] 2"
    Monitor        "External Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Two Screen Layout"
    Screen        0 "Default Screen" 0 0
    Screen        1 "External Screen" RightOf "Default Screen"
    Option        "Xinerama" "On"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option    "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

There may well be something really obvious that I've missed. Sorry if that's the case :) But any help would be really appreciated!

---

### Post by bomanizer on 2007-07-23
Have you tried to toggle the external display with the FN key? Kinda obious, but had to ask :) Also, the ibm "tools" I have include controls for powerin on / shutting down thinkpad h/w, they're in /proc/acpi/ibm

Do this, for example:

```
cat /proc/acpi/ibm/video
```

and it should show some info on the current status.

EDIT: [thinkwiki]("http://www.thinkwiki.org/wiki/Problem_with_video_output_switching") has stuff on this.

---

### Post by jigantor on 2007-07-25
If I boot the laptop with the external screen plugged in, only the external screen (and not the laptop screen) works. If I boot the laptop and subsequently plug in the external screen, I can switch between them using the Fn-F7 combination. If they are both on simultaneously, however, they only run as clones - not an extended desktop.

The problems described on thinkwiki are slightly different to mine - I'm not having a problem getting the external display working, I'm having a problem getting it working as a second/extended desktop.

When I run ```
cat /proc/acpi/ibm/video
``` I get this, regardless of whether the external monitor is plugged in or not:

```
status:         supported
lcd:            disabled
crt:            disabled
dvi:            disabled
auto:           enabled
commands:       lcd_enable, lcd_disable
commands:       crt_enable, crt_disable
commands:       dvi_enable, dvi_disable
commands:       auto_enable, auto_disable
commands:       video_switch, expand_toggle

```

I'm not quite sure what that means, or how to activate the commands that are listed.

---

### Post by bomanizer on 2007-07-25
Ok. Then I think it's related to X. I don't have an external display, just tought I'd share some stuff I've ran into. Also, I'm not an expert at this, but I think the controls under /ibm are indeed functional, 'cause I'm able to toggle fan modes with them. (/proc/acpi/ibm/fan) For example, I've tweaked the fan tresholds (only a few degrees) so that a light strain on (browsing, etc..) the cpu doesn't instantly make the fan to step up.

```
echo crt_enable > /proc/acpi/ibm/video
```

..is the way to issue commands. Just use the desired command after "echo". Use "sudo" or "sudo su".
I've added this thread on my subscriptions, I'm interested to try an external LCD. I'll post any results if I get to fiddle with this.

---

### Post by jigantor on 2007-07-29
> 
```
echo crt_enable > /proc/acpi/ibm/video
```

..is the way to issue commands. Just use the desired command after "echo". Use "sudo" or "sudo su".

Hmm. For some reason even when I use sudo/sudo su it still spits back a 'permission denied'. Am I missing something important here?

---

### Post by bomanizer on 2007-07-30
> **jigantor said:**
> Hmm. For some reason even when I use sudo/sudo su it still spits back a 'permission denied'. Am I missing something important here?

Whops, sorry.. I wasn't clear enough, my bad. Anyways, you must go sudo-all-the-way, meaning be root:

```
$ sudo su
root@blahblah$ echo crt_enable > /proc/acpi/ibm/video
```

:cool:

---

