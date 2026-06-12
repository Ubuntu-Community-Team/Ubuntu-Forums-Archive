---
title: "Dual monitor refresh rate"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by StrikerWorldWide on 2006-07-27
Hi,

I just set up dual monitors on my fresh install on Ubuntu - but the refresh rate is stuck at 50Hz and my monitors freak out and say "Non-Preset Mode".

Someone please help!

-Striker

---

### Post by geco on 2006-07-27
If you know the refresh rate you want to assign, just edit your screen section in /etc/X11/xorg.conf file (**back it up before editing**)
e.g. here is my external screen configuration:
```

Section "Screen"
        Identifier      "External Screen"
        Device          "Mobility Radeon 9700 64MB (Secondary)"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024@60"
        EndSubSection
EndSection

```

You need to add "@ref_rate" in yout display subsection
e.g.
```

SubSection "Display"
                Depth           24
                Modes           "1280x1024@60"
        EndSubSection

```
you need to restart your X server to apply the changements.

Otherwise try the "xrandr" command to check and change your screen resolution and refresh rate.
```

xrandr

```
displays your current display's settings
e.g. for me:
```

geco@biohazard:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 433mm x 347mm )   75   70  *60   47   43
 1   1152 x 864    ( 433mm x 347mm )   75   70   60   47   43
 2   1024 x 768    ( 433mm x 347mm )   75   72   70   60   43
 3    800 x 600    ( 433mm x 347mm )   75   72   70   60   56
 4    720 x 576    ( 433mm x 347mm )   60
 5    640 x 480    ( 433mm x 347mm )   75   72   60
 6    640 x 400    ( 433mm x 347mm )   75   60
 7    640 x 350    ( 433mm x 347mm )   60
 8    512 x 384    ( 433mm x 347mm )   75
 9    400 x 150    ( 433mm x 347mm )   75   60
 10   320 x 120    ( 433mm x 347mm )   75   60
 11   320 x 100    ( 433mm x 347mm )   75   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

```
so I have 1280 x 1024 resolution and 60 Hz refresh rate

You can choose among the available res and ref rates.

To alter the ref rate tape
```

xrandr -r ref_rate

```
where "ref_rate" is the refresh rate choosed among the available ones.

If you want to know more about xrandr type
```

xrandr -h

```

Hope it may help you.

byebye

---

### Post by StrikerWorldWide on 2006-07-27
Ok maybe I should give more info.

I edited the xorg.conf file - if you need to see it, let me know. The ubuntu GUI screen resolution window says that the resolution is 2560x1024 (the right double resolution) and the refresh rate is 50Hz. For my monitors, it needs to be 60-76Hz I believe. How do I alter this?

-Striker

---

### Post by geco on 2006-07-27
> **StrikerWorldWide said:**
> Ok maybe I should give more info.

I edited the xorg.conf file - if you need to see it, let me know. The ubuntu GUI screen resolution window says that the resolution is 2560x1024 (the right double resolution) and the refresh rate is 50Hz. For my monitors, it needs to be 60-76Hz I believe. How do I alter this?

-Striker
We posted at the same time!
See my post above ;)

byebye

---

### Post by StrikerWorldWide on 2006-07-27
```

 SZ:    Pixels          Physical       Refresh
*0   2560 x 1024   ( 684mm x 271mm )  *50
 1   2560 x 960    ( 684mm x 271mm )   51
 2   2304 x 864    ( 684mm x 271mm )   52
 3   1600 x 600    ( 684mm x 271mm )   53
 4   2048 x 768    ( 684mm x 271mm )   54
 5   1280 x 1024   ( 684mm x 271mm )   76
 6   1024 x 768    ( 684mm x 271mm )   75
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

```

This is my xrandr settings. How doth I fix this?

---

### Post by geco on 2006-07-27
> **StrikerWorldWide said:**
> ```

 SZ:    Pixels          Physical       Refresh
*0   2560 x 1024   ( 684mm x 271mm )  *50
 1   2560 x 960    ( 684mm x 271mm )   51
 2   2304 x 864    ( 684mm x 271mm )   52
 3   1600 x 600    ( 684mm x 271mm )   53
 4   2048 x 768    ( 684mm x 271mm )   54
 5   1280 x 1024   ( 684mm x 271mm )   76
 6   1024 x 768    ( 684mm x 271mm )   75
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

```

This is my xrandr settings. How doth I fix this?

xranrd say that you are not allowed to change your refresh rate... I don't know why... maybe it's the drivers' fault.
You can just change your screen resolution to 1280 x 1024 and you will have a refresh rate of 76Hz
xrandr says
```

5   1280 x 1024   ( 684mm x 271mm )   76

```
than to switch it on:
```

xrandr -s 5

```

Are you using a Big Desktop/Twin View (one desktop with 2 monitors)?
I don't know mich about those, because I use one different desktop for each screen.

byebye

---

### Post by StrikerWorldWide on 2006-07-27
How do you set up each monitor with a different desktop? Can you still drag stuff between them?

---

### Post by geco on 2006-07-27
> **StrikerWorldWide said:**
> How do you set up each monitor with a different desktop? 

You have to set up two video drivers devices, screens and monitors

[Here](http://gentoo-wiki.com/HOWTO_Dual_Monitors) is a quite good how-to

I post also my xorg.conf sections
```


Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9700 64MB]"
	Driver		"fglrx"
	Option          "VideoOverlay" "on"
	Option          "OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9700 64MB] (Secondary)"
	Driver          "fglrx"
	Option          "VideoOverlay" "on"
	Option          "OpenGLOverlay" "off"
	BusID           "PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
EndSection

Section "Monitor"
        Identifier      "External Monitor"
	HorizSync	30 - 80 
	VertRefresh	56 - 76 
        Option          "DPMS"
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9700 64MB]"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9700 64MB] (Secondary)" 
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024@60"
        EndSubSection
EndSection									
Section "ServerLayout"
        Identifier      "Dual"
        Screen 0        "Laptop Screen"
        Screen 1        "External Screen" RightOf "Laptop Screen"
        Option          "Clone" "Off"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

```

>  Can you still drag stuff between them?
No, unfortunately you can't drag windows beetween them, I use it because I have a big desktop monitor and a little laptop monitor


byebye

---

### Post by StrikerWorldWide on 2006-07-27
Is there any danger to having refresh rates set to 50Hz on two TFTs? Is it only CRTs that make your head hurt?

-Striker

---

