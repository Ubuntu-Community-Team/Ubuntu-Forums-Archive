---
title: "Synaptics touchpad driver's speed settings are unreliable"
date: 2013-09-23
forum: Apple Hardware Users
---

### Post by aneganov on 2013-09-23
Hi!

I run Ubuntu 13.04 on MacBook Pro 8.2. The problem is that synaptics driver speed configuration seems pretty unreliable.

The main difference between how the touchpad behaves under OS X and with synapitcs is:
[LIST]
[*]Under OS X: when you move your finger slowly horizontally from the left edge to the right edge cursor travels only 1/3 of the screen
[*]Under Ubuntu: when you move your finger slowly horizontally from the left edge to the right edge under Xorg, cursor moves from the left to the right edge of the screen
[/LIST]

I couldn't find good docs on how to configure **MinSpeed**, **MaxSpeed,** **AccelFactor** and **TrackstickSpeed** values.

Any ideas?

---

### Post by aneganov on 2013-09-23
I think I've found the solution finally. To get Apple touchpad configured "as on Mac" you need to configure not only synaptics, but xinput as well.

Let's see how those two configurations differ:

```
$ xinput list-props 11
Device 'bcm5974':
    Device Enabled (133):    1
    Coordinate Transformation Matrix (135):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (263):    1
    Device Accel Constant Deceleration (264):    3.000000
    Device Accel Adaptive Deceleration (265):    2.000000
    Device Accel Velocity Scaling (266):    12.500000
    Synaptics Edges (267):    -3611, 4246, 517, 6108
    Synaptics Finger (268):    30, 70, 257
    Synaptics Tap Time (269):    200
    Synaptics Tap Move (270):    400
    Synaptics Tap Durations (271):    180, 180, 50
    Synaptics ClickPad (272):    1
    Synaptics Tap FastTap (273):    0
    Synaptics Middle Button Timeout (274):    0
    Synaptics Two-Finger Pressure (275):    283
    Synaptics Two-Finger Width (276):    7
    Synaptics Scrolling Distance (277):    -200, -200
    Synaptics Edge Scrolling (278):    0, 0, 0
    Synaptics Two-Finger Scrolling (279):    1, 1
    Synaptics Move Speed (280):    1.000000, 10.000000, 0.020000, 40.000000
    Synaptics Edge Motion Pressure (281):    30, 160
    Synaptics Edge Motion Speed (282):    1, 929
    Synaptics Edge Motion Always (283):    0
    Synaptics Off (284):    0
    Synaptics Locked Drags (285):    1
    Synaptics Locked Drags Timeout (286):    500
    Synaptics Tap Action (287):    0, 0, 0, 0, 1, 3, 2
    Synaptics Click Action (288):    1, 0, 0
    Synaptics Circular Scrolling (289):    0
    Synaptics Circular Scrolling Distance (290):    0.100000
    Synaptics Circular Scrolling Trigger (291):    0
    Synaptics Circular Pad (292):    0
    Synaptics Palm Detection (293):    1
    Synaptics Palm Dimensions (294):    12, 100
    Synaptics Coasting Speed (295):    20.000000, 50.000000
    Synaptics Pressure Motion (296):    30, 160
    Synaptics Pressure Motion Factor (297):    1.000000, 1.000000
    Synaptics Resolution Detect (298):    1
    Synaptics Grab Event Device (299):    1
    Synaptics Gestures (300):    1
    Synaptics Capabilities (301):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (302):    1, 1
    Synaptics Area (303):    0, 0, 0, 0
    Synaptics Soft Button Areas (304):    0, 0, 0, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (305):    10, 10
    Device Product ID (253):    1452, 581
    Device Node (254):    "/dev/input/event5"
```

It's obvious that parameters starting with "Synaptics" come from synaptics driver. They are configured using **synclien** utility. The object of out interest - the rest of parameters, specifically:

```

    Device Accel Profile (263):    1
    Device Accel Constant Deceleration (264):    3.000000
    Device Accel Adaptive Deceleration (265):    2.000000
    Device Accel Velocity Scaling (266):    12.500000

```

These parameters are fully documented here: [http://www.x.org/wiki/Development/Documentation/PointerAcceleration/](http://www.x.org/wiki/Development/Documentation/PointerAcceleration/)
What I've changed - is **Device Accel Constant Deceleration** which was 1.00 by default. I set it to 3.00 as you see, which made the pointer moving 3 times slower allowing precise movement:

```
$ xinput set-prop 11 "Device Accel Constant Deceleration" 3
```

Since now speed is 3 times lower, I had to increase AccelFactor:
 
```
$ synclient AccelFactor=0.02
```

Also, there are different acceleration profiles which Xorg supports - from 1 to 7, but I haven't experimented with them, leaving default 1.

---

