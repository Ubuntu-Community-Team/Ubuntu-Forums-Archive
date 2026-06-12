---
title: "VMWare USB headset"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by cold-peak on 2007-04-24
Hi all,

I know it is possible to install VMware under Ubuntu, but i am at the stage where i do not want to Dual boot any more, and just have Ubuntu installed.

However there are a couple of aplications that "will" work under wine, however i really need it for Windows. Is it possible to use a USB audio device under VMWare for this?

(Using Teamspeak).


Regards,

---

### Post by AscendedDaniel on 2007-05-01
I got my Logitech Communicate STX webcame working (including the onboard microphone), so it is possible. Basically, you need to plug the device into the virtual machine. You can do this virtually, or by plugging it in when the vm has focus, in which case vmware should do this for you. 

Things to keep in mind:
[LIST]
[*]You need to give the vm a usb controller
[*]The USB settings are usually under VM > Removable Devices > USB (You can virtually switch which machine (host or vm) the device is plugged in here.)
[/LIST]

---

