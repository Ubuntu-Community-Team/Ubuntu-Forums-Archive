---
title: "Configuring wireless network with BCM43XX"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ravis_31 on 2007-03-20
Hi,I tried configuring my wireless conn on my laptop using [this]("http://ubuntuforums.org/showthread.php?t=197102") link and configured the network manager on gnome.I can see the network icon on the top left corner but it shows only the wired network.
Now how do i know whether ndiswrapper is already installed and how do i get the wireless icon to show up in the tray?
if already configured how do i enable it for WPA coz' my modem has WPA enabled.

travis

---

### Post by driant on 2007-03-20
"ndiswrapper -v" at the terminal will let you know whether or not you've got ndiswrapper installed. I've got Broadcom wireless hardware in my machine, too, and [this howto]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") is what ended up getting it working for me. It basically details how to set up ndiswrapper and the device's Windows drivers instead of using bcm43xx. I never did get gnome-network-manager playing nice (instructions for that are at the bottom of the howto), but wireless does work!

The whole WPA thing is also a mystery to me, unfortunately.

Good luck, hope this helps!

---

### Post by ravis_31 on 2007-03-21
well i tried but i keep getting compilation errors,i was unable to compile as well as make installer.I there any way else

travis

---

### Post by ravis_31 on 2007-03-23
I got the wireless working from [this ]("http://ubuntuforums.org/showthread.php?t=197102")thread but the networking icon on the top-right corner doesn't show my wireless connection.It shows the wired ethernet connection(disabled) and dial-up connections.Any way i could get the wireless connection displayed in that?

travis

---

