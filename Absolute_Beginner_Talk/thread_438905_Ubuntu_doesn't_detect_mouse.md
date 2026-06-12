---
title: "Ubuntu doesn't detect mouse"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by martgus on 2007-05-10
Hello,

I've installed Ubuntu 7.04 on my laptop (I even got the problem with screen resolution fixed eventually ), but I can't use my USB-mouse, which must be the most basic Logitech optical wheel mouse. If I plug it in, just nothing happens. Touchpad works fine, though.
Any ideas what should I do to make Ubuntu understand that I have connected my mouse and would actually like to use it?

---

### Post by sailor2001 on 2007-05-10
usb mouse? Usb uses more of your resources (ram) and it's possible that you just don't have enough memory for it.......check to see if you have other programs running that would be using your ram

---

### Post by jhenager on 2007-05-10
What I would do first, is verify that the USB port is ok by using a flash drive or some other common USB device in it. Next, doublecheck to see if the mouse is operational on another system. Try some different connection scenarios, such as hot plugging it while the system is up, or restarting while it is connected. Make sure the BIOS is set to always enable an external mouse. If you have another USB mouse to test with, try that.
Check these things and post the results back.

---

### Post by martgus on 2007-05-10
Thanks, guys! 

The USB port works just fine, it detects my camera, memory sticks etc. The mouse works on my other computer and also with this very same computer under Windows. 

If I go to System > Preferences > Removable Drives and Media Preferences, I see that under Input Devices there is a check box (Automatically run a program when a USB mouse is detected) next to Mice. Well, the box is empty (not ticked) and so is the command filed below it. Should I perhaps tick the box and also insert some kind of command (which?)  to run?

---

### Post by Headweightlost on 2007-06-03
> **martgus said:**
> Thanks, guys! 

The USB port works just fine, it detects my camera, memory sticks etc. The mouse works on my other computer and also with this very same computer under Windows. 

If I go to System > Preferences > Removable Drives and Media Preferences, I see that under Input Devices there is a check box (Automatically run a program when a USB mouse is detected) next to Mice. Well, the box is empty (not ticked) and so is the command filed below it. Should I perhaps tick the box and also insert some kind of command (which?)  to run?
I'm running 7.04 with a usb mouse and I've never had this problem, so perhaps the source of it is something else (my Input Devices box is UNchecked and the mouse works)

---

### Post by Headweightlost on 2007-06-03
Maybe this'll help? (I'm trying to get Feisty to detect my digi-cam so i can upload pics)

[http://ubuntuforums.org/showthread.php?t=420537&highlight=detect+camera]("http://ubuntuforums.org/showthread.php?t=420537&highlight=detect+camera")

---

