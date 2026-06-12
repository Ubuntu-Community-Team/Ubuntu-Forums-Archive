---
title: "WiFi troubles :("
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-13
Hey, I'm using Dapper and I've got ndiswrapper with a broadcom 4311 chipset. My wireless works fine at my house, but it doesn't seem to work with other wifi networks in other locations. I've only successfully gotten online with one other wifi network at some college I was visiting.

When I'm at another location that has wifi, I go to System>Administration>Networking... and go to preferences on the wireless device. I change the network to whatever ones are available, and try each one. After clicking ok it takes really long for "activating device..." to end. Then after clicking "close" (and selecting default device 'wlan0') it takes another couple minutes to end. But then it says the device isn't activated/0% connectivity.

Is it just the wireless networks I've been trying to connect to, or could it possibly be my device?

---

### Post by kbsuperstar on 2007-01-13
bump

---

### Post by kbsuperstar on 2007-01-13
bump bump

---

### Post by jas0 on 2007-01-13
Have you tried using network-manager-gnome?

---

### Post by kbsuperstar on 2007-01-13
No. I shall. thanks :D

---

### Post by ComplexNumber on 2007-01-13
wifi-radar is useful application too. it helped me a lot to get me up and running with wifi.
also note, you may want to isntall a program called BUM(Boot Up Manager). its in the repos. it shows the services (eg firewall, printer daemon, etc) running on your system and which are activated at boot time. after you have installed it, check that the daemon for network manager is running and that it loads at boot time.

---

