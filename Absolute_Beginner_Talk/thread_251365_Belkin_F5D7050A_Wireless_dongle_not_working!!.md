---
title: "Belkin F5D7050A Wireless dongle not working!!"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by dragze on 2006-09-05
Hi, i have the Belkin USB F5D7050A Wireless dongle, now in dapper it is detected etc etc and all looks promising, but as soon as you try to activate it the system crashes. I have tryed activating it with no encrytion and also with WPAPSK, i edited my /etc/network/interfaces config file using the following guide: [RalinkRT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500")

The only difference is that my device comes up as rausb0 instead of ra0.
When following this guide the pc wont even boot all the way into linux with the wireless dongle attached, it crashes just after setting up network devices i.e. as soon as it activates the whole system crashes!

Any ideas please!! need this to work and it seems to be supported driver wise etc, but it just keeps crashin the pc, i have also tried it in another linux machine with the exact same results!!

Help please!! Thanks in advance,
dragze.

---

### Post by dragze on 2006-09-05
bump

---

### Post by thale on 2006-09-05
This is a common issue. I too am using a Belkin USB wireless dongle. I have not found a fool proof solution, but though the course of a few crashes you should be able to get it to work.

What I've done. 

First thing, deactive the device if it's active then select ok/exit out of the network settings window. Reopen networking tool and edit the properties on the device to pick out your sid, set your wep key, etc. Make sure the "enable device" check box is unchecked then hit ok. This may, or may not crash your computer. If it does not select ok/exit out of the networking tool again. Reopen networking tool, check the settings for the device, this time check the "enable device" box. Hit ok, this may crash, if it doesn't hit ok on the networking tool window and your should be good to go. Using the Activate button seems to crash it every time and if it has to write the properties AND active the device at the same time it seems to crash it as well. It's very picky, and my method doesn't always work. you just have to keep at it.

---

### Post by blackest_knight on 2006-09-11
check this thread
[http://ubuntuforums.org/showthread.php?p=1488461](http://ubuntuforums.org/showthread.php?p=1488461)
It seems to be a problem with the gui, I had the belkin usb detected but the network gui tool caused a lockup everytime i attempted to use it. 
this thread should get things going for you.

---

