---
title: "VirtualBox and Wacom"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Hobo2021 on 2007-10-20
Has anyone been able to successfully get pressure sensitivity working in a Windows XP guest? I can use my tablet as a mouse but the XP guest doesn't register any pressure information.

I've commented out the necessary lines to get USB to work in Gutsy:
[http://buranen.info/?p=187](http://buranen.info/?p=187)

I've tried changing the ownership of the device as per instructions here
[http://forums.virtualbox.org/viewtopic.php?t=109&highlight=wacom+graphire](http://forums.virtualbox.org/viewtopic.php?t=109&highlight=wacom+graphire)

And even tried adding a user owner group and adding myself.
[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

No difference.

Any help would be appreciated. Thank you.

---

### Post by catfacts on 2007-10-21
Did you install the wacom drivers in the virtual os from the wacom website, Just cuz they work in gutsy doent mean they will nessacarily cary over, thou Im not sure on the exact details.

---

### Post by Hobo2021 on 2007-10-21
Did you install the wacom drivers in the virtual os from the wacom website, Just cuz they work in gutsy doent mean they will nessacarily cary over, thou Im not sure on the exact details.

I guess my list wasn't quite exhaustive. I did install the wacom drivers in the guest os, if I try to run the config it gives me "A supported tablet was not found on the system". Yes I also have it enabled in the virtualbox usb settings, so it can definitely see it. I mean it works, EXCEPT for pressure sensitivity...but of course, that's half the point of using a wacom.

---

### Post by jessika-kaos on 2008-02-14
Did you ever find a solution? I am having the exact same problem. I've spent hours looking through forums and I can't find a solution. I get the same message error message and I can't even get the cursor to move in the guest OS (win xp). Whenever I plug the tablet in Windows detects it as Virtual Keyboard Driver, Wacom HID Pen, Virtual Media Keys, etc.


Anybody else? Is this actually even possible to do?Are Ubuntu's Wacom drivers perhaps interfering (should I try uninstalling those?)

---

### Post by descentspb on 2008-03-15
That's how i got it to work. Just enabled USB in VBox as usual, plugged the USB Wacom into the Virtual Machine, installed the drivers for it. After that you should press "Right CTRL + i" to disable the mouse integration. And it works, with pressure sensivity.

---

### Post by houdodu on 2008-05-22
this works, but ruins the wacom for ubuntu, even when you exit. is it impossible to use the wacom as a pointer on both ubuntu and windows?

---

