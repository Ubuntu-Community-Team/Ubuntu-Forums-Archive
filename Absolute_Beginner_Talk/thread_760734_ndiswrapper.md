---
title: "ndiswrapper"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by thejem on 2008-04-20
Ok I've got ndiswrapper installed with my windows broadcom drivers and the result if
ndiswrapper -l is
bcmwl6 : driver installed
             device (14e4:4315) present
My wireless light is still orange and looking at network and network tools it shows no wireless networks.
Now what do I do. At least the device present is new with the drivers from windows.

---

### Post by cardinals_fan on 2008-04-20
Run the following:
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
ifconfig wlan0 up
dhcpcd -d wlan0
```

---

### Post by thejem on 2008-04-21
I ran those codes. Result of 'ifconfig wlan0 up' was ERROR while getting interface flags: No such device.
Result of'sudo dhcpcd -d wlan0' was dhcpcd 3.0.17 starting
ERROR, wlan0: ioctl SIOCGIFHWADDR: No such device

---

### Post by thejem on 2008-04-21
There must be a way to get the kernel to turn the broadcom on when booting but I don't know how...

---

