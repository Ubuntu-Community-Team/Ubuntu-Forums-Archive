---
title: "Problem Installing From Terminal"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by burntmonk on 2007-05-12
When I try to install something through the terminal I get a weird message.  Here I was trying to install mplayer and the embedded player into firefox, everything started like normal, but spit out that weird error a few times, then continued like normal, then just stopped and brought the command prompt back up.  Any clues?

I was thinking my sources list might be kinda screwy too, so it's in the picture, there might not be anything wrong with it, but just hoping someone could give me some input.  Thanks.

[IMG]http://a44.ac-images.myspacecdn.com/images01/21/l_bb255c638b76049f68c24ab5131327e3.png[/IMG]

---

### Post by FuturePast on 2007-05-12
It would be more useful if you copy/pasted the actual command run and the resulting errors into your post.

---

### Post by burntmonk on 2007-05-12
Here's where I was trying to run EasyUbuntu:

```
branden@ubuntu:~/easyubuntu$ sudo python easyubuntu.in
System sanity check: PASSED!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Nythain on 2007-05-12
take it you are running kde
kdesu kate /etc/X11/xorg.conf
comment out the tablet pc only lines like this:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

```

---

### Post by burntmonk on 2007-05-13
No, actually I'm running Gnome.

---

