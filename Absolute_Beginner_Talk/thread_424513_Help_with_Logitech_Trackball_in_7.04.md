---
title: "Help with Logitech Trackball in 7.04"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by foffen on 2007-04-26
I have a Logitech ES100 wireless keybd and a  "Cordless Optical Trackman" trackball (why not just call it the TB5000 or something simple :confused: :) )

Tried all sorts or things, here is some background
[LIST]
[*]successfully ran sudo apt-get install xvkbd xbindkeys xmacro
[*]successfully ran sudo apt-get install xserver-xorg-input-evdev
[*]NO  xmodmap modifications done
[*]"Logitech USB Receiver" name i got from cat /proc/bus/input/devices
[*]Tried older setup suggestions using "Dev Name", "Dev Phys" etc, all failed 
[*]lsmod | grep evdev returned "evdev                  11008  5"
[*]
[/LIST]
Working xorg.conf setting (working i mean it works like a mouse but no back(btn8 )/fwd(btn9) buttons, which is what i really want)

```
Section "ServerLayout"
    InputDevice    "Mouse0" "CorePointer"
EndSection
...
Section "InputDevice"
	 Identifier     "Mouse0"
	 Driver         "mouse"
	 Option         "Protocol" "auto"
	 Option         "Device" "/dev/psaux"
	 Option         "Emulate3Buttons" "no"
	 Option         "ZAxisMapping" "4 5"
	 Option		"Buttons" "10"
EndSection

```

When i installed ubuntu i had a PS/2 mouse connected, maybe that's why it shows as "/dev/psaux"?
 
Amongst all the other setups i have tried (many trials so far) the most correct one i guess would be the one i adapted from the MX1000 setup

```

Section "ServerLayout"
    InputDevice    "Trackball" "CorePointer"
EndSection
...
Section "InputDevice"
	Identifier	"Trackball"
        Driver          "evdev"
        Option          "Name" "Logitech USB Receiver"
	Option		"HWHEELRelativeAxisButtons" "4 5"        
EndSection
```

This causes X to crash. Here is the output from /var/log/Xorg.0.log

[I][SIZE="1"]
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Trackball-usb-0000:00:10.1-1/input0: Core Pointer
(**) Option "CorePointer"
(**) Trackball-usb-0000:00:10.1-1/input1: Core Pointer
(II) Trackball-usb-0000:00:10.1-1/input1: Found 3 relative axes.
(II) Trackball-usb-0000:00:10.1-1/input1: Configuring as pointer.
(**) Trackball-usb-0000:00:10.1-1/input1: WHEELRelativeAxisButtons: 4 5.
(II) Trackball-usb-0000:00:10.1-1/input1: Found 16 mouse buttons
(**) Trackball-usb-0000:00:10.1-1/input1: Configuring 3 relative axes.
(II) Trackball-usb-0000:00:10.1-1/input1: Configured 18 mouse buttons
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Trackball-usb-0000:00:10.1-1/input1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Trackball-usb-0000:00:10.1-1/input0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) Trackball-usb-0000:00:10.1-1/input0: Init
(**) Trackball-usb-0000:00:10.1-1/input1: 3 valuators.
(**) ../../src/evdev_btn.c (166): Registering 18 buttons.
(II) Trackball-usb-0000:00:10.1-1/input1: Init
(II) evdev brain: Rescanning devices (2).
(II) Trackball-usb-0000:00:10.1-1/input0: On
(II) Trackball-usb-0000:00:10.1-1/input1: On
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(main+0x6bf) [0x80749af]
3: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d38ebc]
4: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting[/SIZE][/I]
hmmm...?

Found this guide for this trackball on older release so it must be doable...

[http://www.thpoon.com/modules.php?op=modload&name=News&file=article&sid=11&mode=thread&order=0&thold=0]("http://www.thpoon.com/modules.php?op=modload&name=News&file=article&sid=11&mode=thread&order=0&thold=0")
Allthough  this crashed X with error [I]
[SIZE="1"]
(EE) Mouse0: Unknown protocol "evdev"
(EE) PreInit failed for input device "Mouse0"
(II) UnloadModule: "mouse"
(WW) No core pointer registered[/SIZE]
[/I]
soo... now what? pls help, tried for a few hours now to avoid annoying you all...

---

### Post by foffen on 2007-04-27
bump, someone must be able to help me? please?

---

### Post by SZF2001 on 2007-04-27
Well, all I know about trackballs is that you can find out the mouse's button scheme through a set of numbers, then change the xorg.conf file as root to emulate the scroll effect.

Like this: [http://ubuntuforums.org/showthread.php?t=169423&highlight=marble+mouse](http://ubuntuforums.org/showthread.php?t=169423&highlight=marble+mouse)

Even though it's not your mouse, it's the same idea. There is another thread by Buffalo Soldier explaining somewhere how he found the button scheme here:

[http://ubuntuforums.org/showthread.php?t=77005&highlight=marble+mouse](http://ubuntuforums.org/showthread.php?t=77005&highlight=marble+mouse)

Good luck, soldier.

---

### Post by landstander on 2008-01-04
Hey foffen,

Any luck on getting those extra buttons to work since April of 2007?

I'm using the same trackball; Logitech Trackball, model name: "Cordless Optical Trackman", and Kubuntu (Gutsy v7.10). If you got the extra buttons working, it would be a huge help if you could post an update on how you got the extra buttons to work, and any updates to your xorg.config files etc. If you haven't gotten it to work that would also be informative as far as what devices people should avoid using when switching to Linux.

I've been working hard at trying to get this to work and I'm beginning to run out of options. If any one else has a fix that works for this specific trackball, please by all means post it. 

Also does any one know of a Linux supported device that works really well for producing and working with 3D graphics and animation? Preferably something with mappable buttons and ergonomically designed with long hours of use in mind.

Thank you for taking the time to read my response.

---

### Post by SidewinderPro2 on 2008-01-04
Rollerball mice own. I have an ancient Logitech TrackMan Marble. PS2, it worked by default in Gutsy, so I'm sure how they fare in past releases.

---

