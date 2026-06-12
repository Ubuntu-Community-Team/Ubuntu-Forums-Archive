---
title: "[SOLVED] Treo 600 Problem with USB and installing"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-09-12
Greetings Friends!

I would like to install my Treo 600. I'm using Ubuntu 7.04.

Under       System--->Preferences--->PalmOS Devices

An application called "Welcome to gnome-Pilot! opens. After filling in relevant information a INITIAL SYNC page appears. It say's:

"About to retreive Owner Name andID from PDA. Please put PDA in Cradle (/dev/pilot) and press HotSync button."

SO I PRESS THE BUTTON!!!! And get

Warning (gnome-pilot)
Failed to connect using device 'Cradle', on port '/dev/pilot',Check your configuration, as you requested old-style usbserial 'ttyUSB' syncing, but do not have the usbserial 'visor kernel module loaded. You may need to select a 'usb:' device.

I'm not a wizard at Linus or Ubuntu but if you are and know how to correct the problem I certainly would like to hear from you!!!!

Thank You!!!!

---

### Post by linuxwizard on 2007-09-12
You need to add module visor in Ubuntu 7.04. Look on this page for:: Notes for Releases. It tells you what you need to do. Follow the link there

[https://help.ubuntu.com/community/PortableDevices/PalmOS](https://help.ubuntu.com/community/PortableDevices/PalmOS)

---

### Post by lentomies on 2007-09-12
THANK YOU LINUX WIZARD!!!!!!

Followed the info you provided and it worked perfectly!

I especially like the fact that the treo 600 can be sync'd without having to load palm desktop or it's associated syncing s/w... You simply press the sync button on the USB cord and you got it made!!! Awesome!

Thanks again!!!!

---

### Post by linuxwizard on 2007-09-12
That's good to hear that everything worked out and you have it all setup.

Please mark thread as solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

