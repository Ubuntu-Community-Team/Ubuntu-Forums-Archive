---
title: "Elantech Touchpad in 12.04 - can't configure"
date: 2012-10-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by scotc on 2012-10-07
Dear The-Wise,
I can't find a solution to my Elantech issue and believe me I have looked.  I am running 12.04 on an Asus 1011px.

I can't seem to actually control the sensitivity of the pad from accidental triggering.  If I have "tap to click" enabled, it will mis-fire even when the sensitivity is set to minimum in "preferences/mouse and touchpad".

I've fiddled about with command line codes but none of them seem to atually be operating on the touchpad.  I can't work out where it's getting its instructions from, i.e. what is the actual driver for the pad.
Here's what the OS is telling me.

```
~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=10	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```

```
$ xinput list-props 13Device 'ETPS/2 Elantech Touchpad':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (259):	1
	Device Accel Constant Deceleration (260):	2.500000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	12.500000
	Synaptics Edges (263):	48, 1168, 27, 485
	Synaptics Finger (264):	1, 40, 256
	Synaptics Tap Time (265):	180
	Synaptics Tap Move (266):	58
	Synaptics Tap Durations (267):	180, 180, 100
	Synaptics ClickPad (268):	0
	Synaptics Tap FastTap (269):	0
	Synaptics Middle Button Timeout (270):	75
	Synaptics Two-Finger Pressure (271):	10
	Synaptics Two-Finger Width (272):	6
	Synaptics Scrolling Distance (273):	26, 26
	Synaptics Edge Scrolling (274):	0, 0, 0
	Synaptics Two-Finger Scrolling (275):	1, 0
	Synaptics Move Speed (276):	1.000000, 1.750000, 0.151630, 40.000000
	Synaptics Edge Motion Pressure (277):	30, 160
	Synaptics Edge Motion Speed (278):	1, 105
	Synaptics Edge Motion Always (279):	0
	Synaptics Off (280):	0
	Synaptics Locked Drags (281):	0
	Synaptics Locked Drags Timeout (282):	5000
	Synaptics Tap Action (283):	0, 0, 0, 0, 0, 0, 0
	Synaptics Click Action (284):	1, 1, 0
	Synaptics Circular Scrolling (285):	0
	Synaptics Circular Scrolling Distance (286):	0.100000
	Synaptics Circular Scrolling Trigger (287):	0
	Synaptics Circular Pad (288):	0
	Synaptics Palm Detection (289):	0
	Synaptics Palm Dimensions (290):	10, 200
	Synaptics Coasting Speed (291):	20.000000, 50.000000
	Synaptics Pressure Motion (292):		... of unknown type CARDINAL

	Synaptics Pressure Motion Factor (293):	1.000000, 1.000000
	Synaptics Resolution Detect (294):	1
	Synaptics Grab Event Device (295):	1
	Synaptics Gestures (296):	1
	Synaptics Capabilities (297):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (298):	1, 1
	Synaptics Area (299):	0, 0, 0, 0
	Synaptics Noise Cancellation (300):	6, 6
	Device Product ID (254):	2, 14
	Device Node (255):	"/dev/input/event9"

```

I thought to alter a few properties, such as
```
$ xinput --set-prop --type=int "ETPS/2 Elantech Touchpad" "Synaptics Palm Detectection" 1
```

Notably, I tried to alter the area of the touchpad to desensitize the area near the top by the space bar that causes the triggering, but whatever I set the area to, it made no difference to the area of response of the pad.
e.g.
```
$ xinput --set-prop --type=int "ETPS/2 Elantech Touchpad" "Synaptics Edges" 27 168 47 485
```

I have had a look for an Xorg.conf file in /etc/x11 and I don't appear to have one.  Is that usual for newer versions of Ubuntu?

So, can anyone help me to find out what is controlling my touchpad?
Many thanks, Wise Ones,
Scot

---

### Post by mikewhatever on 2012-10-07
Linux distros usually use the generic synaptics driver, which can be verified by 'dmesg | grep -i touch', and config options can be changed by synclient. (see synclient -l for available options).

In case you'd want to create a dead strip at the top (is that what you actually want?), a synclient command would look something like this
```
synclient AreaTopEdge xxx
```

To figure out the xxx value, it's usefull to obtain the touchpad geometry from Xorg.0.log, for example:

```
~$ cat /var/log/Xorg.0.log | grep -i touch
(II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event5)
(**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
(**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
(**) ETPS/2 Elantech Touchpad: Applying InputClass "ETPS/2 Elantech Touchpad"
(II) Synaptics touchpad driver version 1.2.2
(II) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
(II) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
(II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
(II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
(II) ETPS/2 Elantech Touchpad: buttons: left right middle double triple
(--) ETPS/2 Elantech Touchpad: touchpad found
(**) ETPS/2 Elantech Touchpad: always reports core events
(II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
(**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
(**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 0
(**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
(**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
(--) ETPS/2 Elantech Touchpad: touchpad found
(II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)

```

Geometry settings can be defined in xorg.conf, which needs to be created. Mine looks like this:
```

Section "InputClass"
        Identifier "ETPS/2 Elantech Touchpad"
        MatchProduct "ETPS/2 Elantech Touchpad"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "AreaBottomEdge" "740"
        Option "AreaRightEdge" "1070"
        Option "AreaLeftEdge" "110"
EndSection

```

I had to define left, bottom and right dead strips. Your values will likely be different, as I have a Dell and not an Asus.

---

### Post by scotc on 2012-10-08
Thanks for your help Mikewhatever.  Much appreciated.

Using your instructions above I get
```
~$ dmesg | grep -i touch
[   11.869646] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input9

``` 

which I think confirms that synaptics is operational?

Again, following your lead
```
~$ synclient -l
Parameter settings:
    LeftEdge                = 48
    RightEdge               = 1168
    TopEdge                 = 27
    BottomEdge              = 485
    FingerLow               = 1
    FingerHigh              = 40
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 58
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 10
    EmulateTwoFingerMinW    = 6
    VertScrollDelta         = 26
    HorizScrollDelta        = 26
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.15163
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 105
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 6
    VertHysteresis          = 6
    ClickPad                = 0
```

Which seems to tell me that I was misinformed about there being an option "Edges 47, 1168...."  and there is rather "LeftEdge" etc


Checking the geometry of the pad with 
```
~$ cat /var/log/Xorg.0.log | grep -i touch
```

gives (edited)

```
[    27.852] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 1216
[    27.852] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 512

```

If I enter
```
~$ synclient TopEdge=100
```  
nothing changes! the pad has the same sensitivity over the whole area.  Similarly if I change it to 200, 300 nothing happens.  300 should make a dead edge along the top of the pad so tall that the pad is just a strip along the bottom.

On another line of enquiry, if I use the GUI method (via applications/system/prefs/mouse and pad)  to alter the limited features there, I CAN switch the "tap to click" on and off and it works.  I don't see a similar option in synclient though, perhaps I am not understanding it.

Also in the GUI is "disable while typing", which is currently unchecked and remains so despite using the command line  synclient PalmDetect=1.

With a quick trial for this post, it seems that palm detect is not working as the mouse can still jump during typing.

It is as if there are two conflicting ways to control the touchpad.  

It would be very helpful to me, in a general way, to understand how these "drivers" etc are working together or not.

---

### Post by mikewhatever on 2012-10-08
How about **synclient AreaTopEdge=50** ?

The 'Tap to Click' feature, I believe, is governed by TapButton1, TapButton2 and TapButton3 values. Yours are set to 0, which means disabled. 

The 'Disable while typing' is provided by something called syndaemon. If enabled, it should be running in the background, here is mine:
```
~$ ps -ef | grep syndaemon
mini      1567  1499  0 Oct07 ?        00:02:29 syndaemon -i 2.0 -K -R -t

```

That sets the timeout for 2 seconds - the default value.

---

### Post by scotc on 2012-10-09
Thanks again Mikewhatever,

taking your syndaemon suggestion first I get

```
:~$ ps -ef | grep syndaemon
1000      9438  7714  0 19:22 pts/0    00:00:00 grep --color=auto syndaemon
```

which if I understand correctly means the "palm detect" is not active.

My "TapButton1" is currently as follows
```
TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0

```

which allows me to tap AND is confirmed by the GUI "enable mouse clicks with touchpad".  I'm not sure what "3" signifies above.

Syndaemon. I have looked up the syntax and simply coded
```
syndaemon 2.0 -t -d
```
That seems to put a 2 second pause on taps, but not mouse movement, when  typing, so perhaps job done?

What is the most sensible way to make this syndaemon command permament (I presume it would reset after reboot)?

By the way, I tried your code
```
~$ synclient AreaTopEdge=50
```
and that works just fine too.  It deadens the top 7th of the touchpad.

Again, what is the best way to make that permanent, should I decide to go that way?
Thanks, Scot

---

### Post by mikewhatever on 2012-10-09
Hi again, I am glad it works.

Syndaemon takes care of the "Disable while typing" feature, which is not the same as "Palm detect". You should be able to turn it on using the touchpad GUI, just check the box next to "Disable touchpad while typing". I've never actually used "Palm detect", not sure how it works.

The values you get for TapButtons look ok, 1 means left click and 3 right click, so, in your case, a one-finger tap should immitate the left click, and a two-finger tap the right click.

Lastly, to make the dead strip thing permanent, you'll need to put the following into a config file:

```
Section "InputClass"
        Identifier "ETPS/2 Elantech Touchpad"
        MatchProduct "ETPS/2 Elantech Touchpad"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "AreaTopEdge" "50"
EndSection
```

Open the file for editing with **gksu gedit /etc/X11/xorg.conf**, and paste that in.

---

### Post by scotc on 2012-10-11
Thanks Mikewhatever,
the problem of pad triggering is solved!

I created the etc/x11/xorg.conf file (which of course does not exist in 12.04).
I put the code in as you suggested.  Rebooted and I do have a dead strip at the top of the pad where formerly I would get a cross-trigger from the space bar / my thumb.

I also have added the "syndaemon 2.0 -d -t" to the "startup applications".

The touchpad GUI "disable while typing" does not appear to actually do anything.  

So, with your help, thread is solved.
Thanks
Scot

---

### Post by wb8nbs on 2012-12-09
This worked also for me in 12.10 on an Asus N56VJ. My Xorg.conf has:

```
Section "InputClass"
        Identifier "ETPS/2 Elantech Touchpad"
        MatchProduct "ETPS/2 Elantech Touchpad"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "AreaBottomEdge" "1850"
        Option "AreaTopEdge" "200"
        Option "AreaLeftEdge" "200"
        Option "AreaRightEdge" "3000"
        Option "PalmDetect" "1"
EndSection

```

Which gives about a centimeter dead all around the touchpad. The bottom zone in particular helps a lot in keeping the cursor steady while pressing one of the buttons.

---

### Post by hongquan1987 on 2013-01-30
Thank you.
Is there a Facebook Like button here? I want to "like" you.

---

### Post by BlinkinCat on 2013-01-30
> **hongquan1987 said:**
> Thank you.
Is there a Facebook Like button here? I want to "like" you.

Hi - No like buttons but you  can make friends 'tho - ):P

---

