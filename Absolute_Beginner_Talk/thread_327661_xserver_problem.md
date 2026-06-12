---
title: "xserver problem"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by mcrae on 2006-12-29
The xserver doesn't start on boot. I'm running Dapper Drake 6.06 and recently this problem appeared without any obvious reason. Going to the external terminal I tried startx and after doing 

 rm /tmp/.X0-lock

I managed to start xserver with startx.

Now I'm trying to fix it but nothing I have found in the forum helps. This is the end of the output of 

```
less /var/log/Xorg.0.log
``` :

```
....
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
```

any ideas...

Thanks in advance

---

### Post by teaker1s on 2006-12-29
sounds like "gdm" on ubuntu gnome        or "kdm" on kubuntu
 login manager problem try reinstalling

---

### Post by mcrae on 2006-12-30
you mean reinstall the whole system or just gdm...

---

### Post by teaker1s on 2006-12-30
just gdm as for what ever reason gdm seems broken/misconfigured  as startx results in bypassing gdm and loading desktop either dpkg reconfigure it or remove and reinstall with synaptic

---

### Post by wornomsf on 2007-02-26
I have the same problem /dev/input/wacom  not found. Where can I get wacom.
Stephen

---

