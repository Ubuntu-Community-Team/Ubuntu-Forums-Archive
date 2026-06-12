---
title: "funny behaviour of synaptics driver"
date: 2010-06-09
forum: Apple Hardware Users
---

### Post by dvandok on 2010-06-09
As a reasonably satisfied Ubuntu-on-MacBook (MacBook 2,1) user I find that over an extended period of usage, certain oddities in the system are starting to come more and more to the foreground, almost demanding a resolution. Maybe that's the way I'm wired, I just want to fix things if they're broken even if it is perfectly possible to work around them.

The touchpad is one of these things. I don't want to use tapping (it's too erratic for my taste) but I find that the option to turn tapping off keeps turning itself back on every time I connect my USB mighty mouse. I observed this by running synclient -l, removing/reinserting the mouse, and running synclient again. 

After turning tapping off in gsynaptics:
```

    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0

```

After reinserting the mouse:
```

    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2

```

There is very little information in the logs to trace who is doing this, and since the settings live in shared memory in the X server it seems very hard to debug (at least I have no experience tracing shared memory access). My suspicion is that it is the synaptics driver itself (/usr/lib/xorg/modules/input/synaptics_drv.so) that somehow gets triggered through the XINPUT extension and loads the built-in defaults.

In the Xorg.0.log I find this:

```

(II) Primax Electronics Apple Optical USB Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Primax Electronics Apple Optical USB Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Primax Electronics Apple Optical USB Mouse (/dev/input/event13)
(**) Primax Electronics Apple Optical USB Mouse: Applying InputClass "evdev pointer catchall"
(**) Primax Electronics Apple Optical USB Mouse: always reports core events
(**) Primax Electronics Apple Optical USB Mouse: Device: "/dev/input/event13"
(II) Primax Electronics Apple Optical USB Mouse: Found 8 mouse buttons
(II) Primax Electronics Apple Optical USB Mouse: Found scroll wheel(s)
(II) Primax Electronics Apple Optical USB Mouse: Found relative axes
(II) Primax Electronics Apple Optical USB Mouse: Found x and y relative axes
(II) Primax Electronics Apple Optical USB Mouse: Configuring as mouse
(**) Primax Electronics Apple Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Primax Electronics Apple Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Primax Electronics Apple Optical USB Mouse" (type: MOUSE)
(II) Primax Electronics Apple Optical USB Mouse: initialized for relative axes.

```

So maybe evdev has something to do with it as well.

I'm open to any suggestions on how I can trace further what is going on with the driver/settings; I am not so much interested in workarounds.

---

