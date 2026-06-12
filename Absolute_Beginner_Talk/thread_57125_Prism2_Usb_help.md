---
title: "Prism2_Usb help"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by Pheonicks on 2005-08-15
Ok I've searched and searched for an answer to this problem and found some good sources but I need some specific help. I have a buffalo technology airstation usb wireless adapter on a computer that I just installed ubatu on. From my searching I've found that this device will work with the prism2_usb driver. However, the floppy drive is broken, I have no internet access on it, and no network connection. I also have no blank cd's to burn the source of the driver onto so all routes to bringing anything onto this computer are gone. It's my gf's computer and I don't have any spare drives for a floppy etc.. So you see my dillema... What I have found is that when I search for prism on the ubantu box it has a file called prism2_usb.ko. What is a .ko file and how can I use it? Do I have to edit my kernel to get it to work? Help?

:-| 
Pheonicks

---

### Post by az on 2005-08-15
Install linux-wlan-ng.  It is on your cd.  It is a tool to make you able to use the device.  The driver is already installed on your system.  When you plug the thing it, the driver gets loaded by hotplug.

The linux-wlan-ng devices do not integrate very well with the networking GUI.  I think that you can get it to work without WEP, but if you need to use a WEP key, you are going to have to read the documentation and edit some files by hand to get it going.

Look here for details:
[http://ubuntuforums.org/showthread.php?t=25676&highlight=prism2_usb](http://ubuntuforums.org/showthread.php?t=25676&highlight=prism2_usb)

---

### Post by Pheonicks on 2005-08-15
Thanks Azz, I'm trying it now. :-)

---

