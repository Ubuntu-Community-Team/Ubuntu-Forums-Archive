---
title: "Was the Synaptics Touchpad Conf File Moved?"
date: 2008-11-10
forum: Apple Hardware Users
---

### Post by UberWookieks on 2008-11-10
I finally got the touchpad on my Macbook (2,1) working the way I wanted it when I switched from Hardy (x86) to Intrepid (x64) using a clean install. I copied the relevant section from my old xorg.conf to the new one, but it looks like the configuration stuff got moved elsewhere. Does anyone know how to make X consult xorg.conf for configuration details rather than whatever it is using now? Or where the current configuration files is? gsynaptics doesn't cut it since I need to change some things it doesn't address and since it doesn't appear to be running anyway. My xorg.conf looked like this:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "TapButton"             "0"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "VertTwoFingerScroll"   "1"
        Option          "TwoFingerButton1"      "2"
        Option          "MaxTapMove"            "0"
        Option          "MaxDoubleTapTime"      "90"
        Option          "LockedDrags"           "off"
        Option          "MinSpeed"              "1.10"
        Option          "MaxSpeed"              "1.30"
        Option          "AccelFactor"           "0.08"
        Option          "TapButton3"            "2"
        Option          "TapButton2"            "3"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "0"
EndSection

```

/var/log/Xorg.0.log doesn't seem to contain anything unusual besides:

```
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput

```

And here, I can't tell if it's finding the hardware or not:

```
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Macintosh mouse button emulation"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device appletouch
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) appletouch: x-axis range 0 - 1599
(II) appletouch: y-axis range 0 - 386
(**) Option "Device" "/dev/input/event10"
(--) appletouch touchpad found
(**) appletouch: always reports core events
(II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
(II) appletouch: x-axis range 0 - 1599
(II) appletouch: y-axis range 0 - 386
(--) appletouch touchpad found
(II) config/hal: Adding input device Apple Computer Apple Internal Keyboard / Trackpad
(**) Apple Computer Apple Internal Keyboard / Trackpad: always reports core events
(**) Apple Computer Apple Internal Keyboard / Trackpad: Device: "/dev/input/event1"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Apple Computer Apple Internal Keyboard / Trackpad"
(EE) config/hal: NewInputDeviceRequest failed
```

---

### Post by bryonak on 2008-11-11
Using the xorg.conf for input devices is a deprecated concept, the Xorg devs decided to move everything over to hal.

You can search these forums for details, for example [here's a thread]("http://ubuntuforums.org/showthread.php?t=977987") which deals with the issue (read the first two pages before downloading my appletouch.fdi file! Especially the last posting on page 2)

---

### Post by kosumi68 on 2008-11-11
You can add this to your xorg.conf if you want to retain the old config:

```

Section "ServerFlags"
    Option "AutoAddDevices" "off"
EndSection

```

---

