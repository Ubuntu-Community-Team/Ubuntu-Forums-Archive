---
title: "[Kubuntu] I'm getting errors while using the terminal"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Outrunner on 2007-03-12
Hello there! I'm using Kubuntu and while using the terminal, I sometimes get errors after I type a command. For instance:

```
liwe@liwe-desktop:~$ kdesu adept_updater
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kapture::PkgSystem::PkgSystem()

liwe@liwe-desktop:~$             
```

However, the command worked as it should(apparently). What is this and should I do anything about it?

---

### Post by Bachstelze on 2007-03-12
As you saw, the command worked so those message are harmless. If you still want to get rid of them, delete the InputDevice sections about wacom devices in your xorg.conf.

---

### Post by Outrunner on 2007-03-12
Well, it seems that my tiny brain has failed me once again. After editing xorg.conf nothing really happened so I decided I should restart. Well, instead of getting to the GUI, it throws me at a CLI. No problem, I log in and replace xorg.conf with the backup I made and then do 'startx'. So everything's back to normal, but obviously I didn't solve my problem(the errors are really annoying, you see).

The lines I'm deleting are as follows:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
```

Clearly, they are not what I should be deleting... Which one is the right line to delete? Please help me, I'm abolutely clueless about this :(

---

### Post by Songwind on 2007-03-12
After you delete the definitions of the Wacom input devices you also need to remove them from the ServerLayout section.

Otherwise Xorg expects the device descriptions and blows up when it can't find them.

---

### Post by Outrunner on 2007-03-12
OK, OK.... So I did edit it correctly now and it boots directly into the GUI, but I still get errors(only after the command[+password, if needed]). There are less errors now and although they drive me insane I might be able to live with them... hopefully. Thanks for you're help.

---

