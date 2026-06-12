---
title: "Touch Pad Malfunctioning on Laptop Model Dell Latitude D600"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by NavmaN on 2006-10-22
Hello,

Recently, the touch pad on my laptop has been malfunctioning. It has extremely low sensitivity. If you move your finger along the touch pad as fast as possible, the maximum length it will move the mouse is about 2 inches, whereas before, when it was working, it could move across the whole screen in one swipe.

When I use the Ubuntu LiveCD, my touch pad is working fine. And right when I installed Ubuntu it was working fine too, but a day later it started malfunctioning. The knob (other form of a mouse on a laptop) goes normal speed, but it's really messed up, but it's the hardware itself, because this problem persists in windows and ubuntu and the LiveCD.

Please help me correct this problem by whatever means possible, short of reinstalling Ubuntu.

Thanks

P.S. I am very happy with Ubuntu, and find it to be a definite alternative to Windows, and a better and more secure alternative at that.

P.S.S. My laptop is a Dell Latitude D600

---

### Post by localuser on 2006-10-22
> but it's the hardware itself, because this problem persists in windows and ubuntu and the LiveCD.
...
Please help me correct this problem by whatever means possible, short of reinstalling Ubuntu.

If its a hardware problem, then this may not be the right forum, nor, I imagine, will reinstalling Ubuntu help.

If it turns out not to be hardware, but rather a configuration issue, then there is a package called qsynaptics that may be able to help.

---

### Post by TheWizzard on 2006-10-22
run ```
qsynaptics -r
``` at startup

---

### Post by NavmaN on 2006-10-22
TheWizzard,
I ran the command you specified with qsynaptics isnstalled, etc. and I got this message ```
USER@COMPUTER:~$ qsynaptics -r
restoring saved parameter settings from ~/.qsynaptics
users home is /home/USER
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
activate AND save changes...
syndaemon: no process killed
Can't access shared memory area. SHMConfig disabled?
retVal is 0

```

Thanks,
NavmaN

---

### Post by localuser on 2006-10-22
> **NavmaN said:**
> TheWizzard,
I ran the command you specified with qsynaptics isnstalled, etc. and I got this message ```
USER@COMPUTER:~$ qsynaptics -r
restoring saved parameter settings from ~/.qsynaptics
users home is /home/USER
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
activate AND save changes...
syndaemon: no process killed
Can't access shared memory area. SHMConfig disabled?
retVal is 0

```

Thanks,
NavmaN

Try this...

Edit /etc/X11/xorg.conf
You'll find a section for your touchpad
add the following within that touchpad section

Option     "SHMConfig"     "true"

---

### Post by NavmaN on 2006-10-22
Okay,
I fixed the xorg.conf file, and ran qsynaptics -r, with no errors, it just listed data. I then checked the mouse sensitivity preference menu, and the sensitivity settings still have no effect on the touch pad, i.e. the touch pad is still extremely insensitive.

Is there anything else I should do with qsynaptics now that it works properly?

Thanks,
NavmaN

---

### Post by localuser on 2006-10-22
Do a listing of the /dev/input directory and post what you find.

Also, list out what you have in the touchpad section of your /etc/X11/xorg.conf and post what you find.

---

### Post by NavmaN on 2006-10-22
Okay,
In /dev/input I have: 
```
**event0**, **event1**, **event2**, **event3**, **mouse**, **mice**, **mouse0**, **mouse1**, **ts0**, and **ts1**
```
In the touchpad section of xorg.conf I have:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection
```

Thanks,
NavmaN

---

### Post by localuser on 2006-10-22
I should have asked you for your /proc/bus/input/devices listing as well, but that's okay.

Try this....

In the xorg.conf file change the "device" entry from "/dev/psaux" to "/dev/input/mouse0"

I am guessing that you need mouse0, but the devices file I listed above would give the answer.

---

### Post by NavmaN on 2006-10-22
There is nothing in the devices file you mentioned.
I did the changes you mentioned, and it didn't work, so I restarted, and it still doesn't work.

Thanks,
NavmaN

---

### Post by localuser on 2006-10-22
Well, we can beat this into submission 'cause otherwise I got nothin'

Hopefully someone else that's more knowledgeable can now step in...but until then, how about trying

Option "Device" "/dev/input/mouse1" or 
Option "Device" "/dev/input/mouse"

I was under the impression that it should be one of the mouse devices listed in the /dev/input directory and in particular the device listed in the proc/bus/input/devices file.  But its looking like that may not be the case.

---

### Post by NavmaN on 2006-10-22
Okay,

I did what you said and it's not working *BUT* I tried to run qsynaptics itself, by ```
qsynaptics
``` and the program came up, but this is what was in the terminal:
```
[B]X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/B]
users home is /home/navman
LeftEdge:::1900
RightEdge:::5400
TopEdge:::1900
BottomEdge:::4000
FingerLow:::25
FingerHigh:::30
MaxTapTime:::180
MaxTapMove:::220
MaxDoubleTapTime:::180
SingleTapTimeout:::180
ClickTime:::100
FastTaps:::0
EmulateMidButtonTime:::75
VertScrollDelta:::100
HorizScrollDelta:::0
VertEdgeScroll:::1
HorizEdgeScroll:::1
VertTwoFingerScroll:::0
HorizTwoFingerScroll:::0
MinSpeed:::0.09
MaxSpeed:::0.18
AccelFactor:::0.0015
EdgeMotionMinZ:::30
EdgeMotionMaxZ:::160
EdgeMotionMinSpeed:::1
EdgeMotionMaxSpeed:::400
EdgeMotionUseAlways:::0
UpDownScrolling:::1
LeftRightScrolling:::1
UpDownRepeat:::1
LeftRightRepeat:::1
ScrollButtonRepeat:::100
TouchpadOff:::0
GuestMouseOff:::0
LockedDrags:::0
RTCornerButton:::2
RBCornerButton:::3
LTCornerButton:::0
LBCornerButton:::0
TapButton1:::1
TapButton2:::2
TapButton3:::3
CircularScrolling:::0
CircScrollDelta:::0.1
CircScrollTrigger:::0
CircularPad:::0
PalmDetect:::1
PalmMinWidth:::10
PalmMinZ:::200
CoastingSpeed:::0
PressureMotionMinZ:::30
PressureMotionMaxZ:::160
PressureMotionMinFactor:::1
PressureMotionMaxFactor:::1
PressureMotionMaxFactor:::1
0.14.6[B]
Hardware properties:
    Can't detect hardware properties.
    This is normal if you are running linux kernel 2.6.
    Check the kernel log for touchpad hardware information.
Driver version: 1406
Hardware properties:
    Can't detect hardware properties.
    This is normal if you are running linux kernel 2.6.
    Check the kernel log for touchpad hardware information.[/B][B]
Driver version: 1406
syndaemon found!
syndaemon timing is 0[/B]
read AccelFactor=0.0015
read BottomEdge=4000
read CircScrollDelta=0.1
read CircScrollTrigger=0
read CircularPad=0
read CircularScrolling=0
read ClickTime=100
read CoastingSpeed=0
read EdgeMotionMaxSpeed=400
read EdgeMotionMaxZ=160
read EdgeMotionMinSpeed=1
read EdgeMotionMinZ=30
read EdgeMotionUseAlways=0
read EmulateMidButtonTime=75
read FastTaps=0
read FingerHigh=30
read FingerLow=25
read GuestMouseOff=0
read HScrollEmuOff=0
read HorizEdgeScroll=1
read HorizScrollDelta=225
read HorizTwoFingerScroll=0
read LBCornerButton=0
read LTCornerButton=0
read LeftEdge=1900
read LeftRightRepeat=1
read LeftRightScrolling=1
read LockedDrags=0
read MaxDoubleTapTime=180
read MaxSpeed=0.18
read MaxTapMove=220
read MaxTapTime=0
read MinSpeed=0.09
read PalmDetect=1
read PalmMinWidth=10
read PalmMinZ=200
read PressureMotionMaxFactor=1
read PressureMotionMaxZ=160
read PressureMotionMinFactor=1
read PressureMotionMinZ=30
read RBCornerButton=3
read RTCornerButton=2
read RightEdge=5400
read ScrollButtonRepeat=100
read ScrollingMode=1
read SingleTapTimeout=180
read SynDaemonOff=1
read SynDaemonTiming=0
read TapButton1=1
read TapButton2=2
read TapButton3=3
read TappingOff=1
read TopEdge=1900
read TouchpadOff=0
read UpDownRepeat=1
read UpDownScrolling=1
read VScrollEmuOff=0
read VertEdgeScroll=1
read VertScrollDelta=10
read VertTwoFingerScroll=0
read VertTwoFingerScroll=0[B]
Hardware properties:
    Can't detect hardware properties.
    This is normal if you are running linux kernel 2.6.
    Check the kernel log for touchpad hardware information.[/B]
Driver version: 1406

```

I bolded everything that might be useful. Also, it might be helpful to be reminded that my touch pad was working in this very same Ubuntu 6.06 installation, but soon after it started malfunctioning. It might be concluded that there is a corrupt package or program that makes my touch pad malfunction.

Thanks,
NavmaN

---

### Post by localuser on 2006-10-23
To tell you the truth I'm not certain where your configuration files are at this stage, and what the behavior was when you ran qsynaptics prior to making the changes.  Did you see the same errors before?

---

### Post by NavmaN on 2006-10-23
Depending on what changes you mean...
Before I tweaked the xorg.conf file the error was the SHMConfig.
Before these problems and the corruptive package, I never had the need to run qsynaptics, and the package wasn't even installed, everything just worked fine. To be honest, I think it may have been the Flash 9 beta. Do you have any information about that?
I don't know if all the dependencies were installed prior to installing the flash 9 beta, so it might have installed and some how corrupted something in a means unfamiliar to either me or you.

Thanks,
NavmaN

---

### Post by localuser on 2006-10-24
> **NavmaN said:**
> Do you have any information about that?

Sorry NavmaN, I don't. :(

---

### Post by NavmaN on 2006-10-24
Lol, well that's fine. I think the only solution in to reinstall Ubuntu, which isn't that big of a deal to me. One more question, is it possible to copy big files 500 mb+ from your windows partition to ubuntu?

Thanks,
NavmaN

---

### Post by localuser on 2006-10-24
[QUOTE=NavmaN;1658061]Is it possible to copy big files 500 mb+ from your windows partition to ubuntu?/QUOTE]

I've never tried but I don't see why you wouldn't be able to.  Are you asking in reference to the size of the files or are you asking about *how* to get it done?

---

### Post by NavmaN on 2006-10-24
I know how, I was just wondering if there were limitations on size. The way I'm talking about, you literally copy it, you don't even need write access, just read.

NavmaN

---

### Post by hochman on 2006-10-30
I had a similar problem after installing Flash 9 from a 3rd party repository. I think that this repository had a Dapper version of the synaptics driver on it that overwrote the original driver. In order to fix it, all I had to do was uninstall and reinstall xorg-xserver-synaptics (I think that's the package name) after removing the 3rd party Flash repository from my sources list. Now I know about qsynaptics and can use it too thanks to this thread.

---

