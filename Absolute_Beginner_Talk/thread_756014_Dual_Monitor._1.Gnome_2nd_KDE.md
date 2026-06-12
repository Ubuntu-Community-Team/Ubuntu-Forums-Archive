---
title: "Dual Monitor. 1.Gnome 2nd KDE"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-15
Hey,

Im looking to use a dual monitor set up so i can have one monitor for work and one for personal stuff. I want to be able to simply move the mouse all the way to access the second monitor, whats the easiest and best way to do this?

Also is it possible for me to have GNOME on one monitor and KDE on another moniter. (or gnome and icewmm)

Saj

---

### Post by Inxsible on 2008-04-15
You can always use dual monitors and move personal apps to the 2nd monitor and keep your work related apps on the first.

Is that what you mean?

You can only load one DM at a time, so it will all be gnome or all kde.

---

### Post by Inxsible on 2008-04-15
Do you by any chance mean that you will have 2 computers, but want to use the same keyboard and mouse?

You can use a KVM switch in that case. or have a look at a software called Synergy. Its open source and free.

Here's a [CNET video]("http://reviews.cnet.com/Control_two_computers_with_one_keyboard_and_mouse/4660-10165_7-6663696.html") on it

---

### Post by saj0577 on 2008-04-15
Okay how do i do that then using one DM?

No thanks I already have a KVM Switch but thats for a different set of computers, this dual monitors is purely just for one computer with 2 screens attached, (one being a laptop screen and one being an external screen)

Saj

---

### Post by game_plan on 2008-04-15
What video card are you using? 

If your using NVIDIA you will need to get their driver from [http://www.nvidia.com]("http://www.nvidia.com") before it will work. Then edit your /etc/X11/xorg.conf file. 

My desktop is down due to an RMA right now, but I'll post my functional xorg file in a few days when my system is back up :)

---

### Post by saj0577 on 2008-04-15
Cheers.

NO NVIDIA drivers needed for me :)

Saj

---

### Post by Inxsible on 2008-04-15
Were you able to set up dual monitors then ?

what video card do you have ?

---

### Post by saj0577 on 2008-04-15
Not sure what video card i have it will be a intel something i wil check if needed. No i tried googling but there are lots of different ways to dual screen but i dont know how to do it to suit my needs.

Saj

---

### Post by Inxsible on 2008-04-15
> **saj0577 said:**
> Not sure what video card i have it will be a intel something i wil check if needed. No i tried googling but there are lots of different ways to dual screen but i dont know how to do it to suit my needs.

SajOk to even start dual monitors, we will need to know the video card. Try this command and post the output here```
lspci | grep VGA
```That should tell you what video card you have.

---

### Post by saj0577 on 2008-04-15
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)


Saj

---

### Post by Inxsible on 2008-04-15
> **saj0577 said:**
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Sajhmm. I am not sure how to setup dual monitors on an Intel card. For nvidia, you just have to type in nvidia-settings in the terminal and it pulls up an app where you can set dual monitors. 

Maybe someone else can help you out here.

---

### Post by saj0577 on 2008-04-15
Okay no problem, lets hope fore the best.

Thanks
Saj

---

### Post by game_plan on 2008-04-16
On one laptop with Intel graphics it still worked by setting things manually in xorg.conf (laptop screen and external monitor)

---

### Post by saj0577 on 2008-04-17
Anyone?

Saj

---

### Post by saj0577 on 2008-04-18
I got it working with the defautl screen resolutions app but one screen was really zoomed in :S

Saj

---

### Post by game_plan on 2008-04-20
Here you go, these are the sections of the file you will want to play with...
You should be able to use this as it is
```

Section "ServerLayout"
    Identifier     "Multihead configuration"
    Screen      0  "Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "AllowMouseOpenFail" "yes"
EndSection

```
These sections simply change the manufacture and names (its only for display in X anyways), and set the horizsync and vertsync to your monitors
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG Electronics"
    ModelName      "L204WTX-SF"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "dpms"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "LG Electronics"
    ModelName      "L204WTX-SF"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "dpms"
EndSection

```
Here change the driver to your driver, and change name and manufacturer as above (note: options with '#' are for NVIDIA driver, you can take them out)
```

Section "Device"
	Identifier	"Videocard"
	Driver		"nvidia"
	VendorName	"nVidiaCorporation"
	BoardName	"nVidia Corporation G70 [GeForce 7600 GT]"
#	Option		"TripleBuffer"	"true"
#	Option		"backingstore"	"true"
#	Option 		"VBERestore"	"true"
#	Option		"AllowGLXWithComposite"	"true"
#	Option		"XAANoOffscreenPixmaps"	"true"
	Option          "TwinView"
	Option          "MetaModes"     "1680x1050,1680x1050; 1680x1050; 1600x1200,1600x1200; 1600x1200; 1600x1024,1600x1024; 1600x1024; 1440x900,1440x900; 1440x900; 1400x1050,1400x1050; 1400x1050; 1360x768,1360x768; 1360x768; 1280x1024,1280x1024; 1280x1024; 1024x768,1024x768; 1024x768; 800x600,800x600; 800x600; 640x480,640x480; 640x480"
	Option          "TwinViewOrientation"   "RightOf"
	Option          "ConnectedMonitor"      "LCD,LCD"
EndSection

Section "Screen"
    Identifier     "Screen"
    Device         "Videocard"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "AddARGBGLXVisuals" "True"
 #   Option         "RenderAccel" "True"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1680x1050" "1600x1200" "1600x1024" "1440x900" "1400x1050" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x720" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Let me know if you need anymore help (before i forget, its VERY IMPORTANT you make a backup of your current xorg file first, so you can restore to it if things don't work)

---

### Post by saj0577 on 2008-04-20
Cheers i will give it a go during the week sometime. :)

Saj

---

