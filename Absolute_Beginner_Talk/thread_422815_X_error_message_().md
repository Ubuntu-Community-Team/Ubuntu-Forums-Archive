---
title: "X error message (?)"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by wmblowers on 2007-04-25
Does anyone know what this means?  It shows up at the first part of the install dialog, then the rest of the install completes no problems.  It happens when I do an automatic update with Adept through KDE.  There doesn't seem to be any ill effects, but I wonder why it comes up:

***
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
***

Thanks in advance for any help...

WLB  :>)

---

### Post by marx2k on 2007-04-25
Do you have anything special connected to your system? Looks like the system is finding something connected that it doesnt know about?

what does the command 'dmesg' say?

---

### Post by Nythain on 2007-04-25
is it saying that every time you try to kdesu or gksudo or whatever something... looks similar to the errors spewed forth due to the stylus and other entries in the xorg.conf... you can try commenting some things out in your xorg.conf like this
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
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
and see if that helps

---

### Post by wmblowers on 2007-04-25
Thanks, Nythain, commenting out the Tablet PC stuff did the trick.  Appreciate you (both) taking the time to respond.

WLB  :>)

---

