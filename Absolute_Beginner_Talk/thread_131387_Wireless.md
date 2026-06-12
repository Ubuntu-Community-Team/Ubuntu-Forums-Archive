---
title: "Wireless"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by StageMgr2Stars on 2006-02-16
Thanks to all to who helped a while back with my ndiswrapper problem. The driver was sucessfully installed (or so I think). Where do I go from here. I have  Dell Inspiron 2200 with a Dell Wireless 1370 card. I am using Breezy. I am at a stand still and this is the one thing that is so important that I get working. So please help.

when I type in iwconfig I get:

courtneyscott@courtneyscott:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


When I check the installed drivers I see:

Installed ndis drivers:
bcmwl5  driver present, hardware present

(That was the driver I installed)


Thanks again.

---

### Post by carlosqueso on 2006-02-16
try ```
sudo modprobe ndiswrapper
``` and, if that works ```
sudo ndiswrapper -m
``` will have it working all the time.

---

### Post by StageMgr2Stars on 2006-02-16
[QUOTE=carlosqueso]try ```
sudo modprobe ndiswrapper
``` and, if that works ```
sudo ndiswrapper -m
``` will have it working all the time.[/QUOTE]
I have tried that so many times its not even funny. b/c thats the last two steps I always see and it never does anything. its listed under System --> Admin --> Windows Wireless Devices. But I still dont see an option for wlan in the network settings.

---

