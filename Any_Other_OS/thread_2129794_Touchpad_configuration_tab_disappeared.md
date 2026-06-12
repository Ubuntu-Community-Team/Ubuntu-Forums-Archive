---
title: "Touchpad configuration tab disappeared"
date: 2013-03-27
forum: Any Other OS
---

### Post by how2do on 2013-03-27
I have an Acer Aspire E431 and Mint 14 Mate. I always have to re-enable the touchpad after each boot. Until this morning, I had to do ctrl fn f7 to enable it, but when I booted this morning, I discovered that the key combination had mysteriously changed to just fn f7. Also all my touchpad configuration options that I had configured had disappeared, and the touchpad configuration tab under control center/assisstive technologies/mouse was no longer there. Apparently this is the result of an update within the last week (Mar 20 -27) (for lack of any other cause). Does anyone know how to restore the configuration options tab to the Control Center? When I first installed Mint I remember that I had to do something to get the touchpad configuration options to show, but I don't remember what it was. I Tried reinstalling xserver-xorg-input-synaptics to no avail. Is there some other package I should install/reinstall or...?  gpointing-device-settings  is installed. I noticed that there is no xorg.conf file present under /etc/x11 as what I have read seems to indicate there should be.  Something else I noticed is that the touchpad is currently being recognized as "PS/2 Synaptics TouchPad" but several months ago when I was dealing with another touchpad issue, it was recognized as "synPS/2 Synaptics TouchPad". I tried running synclient -l but there is no output from this at all. I tried installing the Synaptiks pacjage, but it says "Touchpad not found". I have read bug reports that suggest that the problem might be the result of a bad kernel update? Here is some information from various terminal commands:

computer@computer-Aspire-E1-431:~$ cat /proc/bus/input/devices


I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input15
U: Uniq=
H: Handlers=mouse0 event8 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

computer@computer-Aspire-E1-431:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                     id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=13    [slave  keyboard (3)]
computer@computer-Aspire-E1-431:~$ xinput --list-props 12
Device 'PS/2 Synaptics TouchPad':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (254):    0
    Device Accel Constant Deceleration (255):    1.000000
    Device Accel Adaptive Deceleration (256):    1.000000
    Device Accel Velocity Scaling (257):    10.000000
    Device Product ID (249):    2, 1
    Device Node (250):    "/dev/input/event8"
    Evdev Axis Inversion (476):    0, 0
    Evdev Axes Swap (478):    0
    Axis Labels (479):    "Rel X" (142), "Rel Y" (143)
    Button Labels (480):    "Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139)
    Evdev Middle Button Emulation (481):    0
    Evdev Middle Button Timeout (482):    50
    Evdev Third Button Emulation (483):    0
    Evdev Third Button Emulation Timeout (484):    1000
    Evdev Third Button Emulation Button (485):    3
    Evdev Third Button Emulation Threshold (486):    20
    Evdev Wheel Emulation (487):    0
    Evdev Wheel Emulation Axes (488):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (489):    10
    Evdev Wheel Emulation Timeout (490):    200
    Evdev Wheel Emulation Button (491):    4
    Evdev Drag Lock Buttons (492):    0

---

### Post by cortman on 2013-03-27
First, just a couple posting tips- when you post code or terminal output, it's a lot more readable if it's between ```
 tags- the hash mark on the editing toolbar. It displays like this-

[code]It displays like this
```

A few paragraph breaks in the post would be helpful too. Just a few friendly suggestions. :)

It looks like the computer does see the touchpad but for some reason won't load drivers for it. Perhaps try booting using the old kernel (you can select it from the GRUB menu at startup) and see if that fixes it.
I don't know if Mint has a different GUI for touchpad settings than Ubuntu, so I can't say what went wrong there.

---

### Post by Perfect Storm on 2013-03-27
Moved to Other OS/Distro Talk.

---

