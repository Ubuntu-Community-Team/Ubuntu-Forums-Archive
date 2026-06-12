---
title: "Mouse and Keyboard suddenly don't work"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by denny_cs on 2006-11-05
Hi,

I am new to Ubuntu Edgy. I have no idea why my mouse and keyboard suddenly don't work after using them for a while. I'm using Logitech Cordless Desktop EX110 and a USB 2.0 hub on IBM ThinkPad R51e. The mouse and keyboard won't work even after I unplug and plug the USB again. I try to plug another USB mouse, but the mouse still does not work. Command "lsusb" still list the mouse and keyboard.

When the system started, sometimes I received message "Failed to initialized HAL". Is this related to the problem above?

Any idea how to solve this?

Thanks.

Best regards,

Denny

---

### Post by bmathis on 2006-11-05
Try unplugging the hub and plugging the keyboard/mouse directly into the comp... I heard of similar problems with USB hubs.

---

### Post by denny_cs on 2006-11-05
Hi bmathis,

I've tried unplug the mouse and keyboard from the USB hub and plug them directly, but it does not work.

I also tried to plug the keyboard and mouse directly when the system is up, but again, the keyboard and the mouse suddenly stop working after a couple minutes.

Any idea?

Denny

---

### Post by denny_cs on 2006-11-05
I've try with another USB keyboard and mouse without USB Hub, and the problem still there. The USB keyboard and mouse suddenly stop working. 
The output of 'lsusb' command:

Bus 003 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

If I unplug and plug again, it seems that the devices are not recoqnized.
The output of 'lsusb' after unplug and plug again:

Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

The only way to make the keyboard and mouse work again is by restarting the Linux :(

Any suggestion how to fix the problem?

Denny

---

### Post by bmathis on 2006-11-05
Try editing xorg.conf file located in /etc/X11/xorg.conf. Mine looks like this, but I am on a laptop so yours will probably be different and need editing

> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

This link might help as well [http://ubuntuforums.org/showthread.php?t=219894]("http://ubuntuforums.org/showthread.php?t=219894")

---

### Post by Dr. Nick on 2006-11-06
Also make sure no other usb devices are plugged in, I have a problem sometimes with the usb mouse not working if I have a usb drive plugged in upon booting

---

