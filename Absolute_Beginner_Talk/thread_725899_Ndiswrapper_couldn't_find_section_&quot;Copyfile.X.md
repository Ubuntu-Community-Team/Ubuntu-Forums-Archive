---
title: "Ndiswrapper couldn't find section &quot;Copyfile.XP.Sys"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2008-03-16
Hi, im trying to install my Belkin F5D6050, my inf file shows

```
CopyFile.XP.Sys

bkusbxp.sys,,,2
```

uncommented but when i run ndiswrapper -i bkusb.in_

```
mike@ubuntu:~$ cd /home/mike/Desktop/Files/Drivers/WINXP
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ sudo ndiswrapper -i bkusb.inf
[sudo] password for mike:
installing bkusb ...
couldn't find section "CopyFile.XP.Sys" -
installation may be incomplete
couldn't find section "CopyFile.XP.Sys" -
installation may be incomplete
couldn't find section "CopyFile.XP.Sys" -
installation may be incomplete
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ sudo ndiswrapper -i bkusb.in_
installing bkusb.in_ ...
couldn't find section "CopyFile.XP.Sys" -
installation may be incomplete
couldn't find section "CopyFile.XP.Sys" -
installation may be incomplete
couldn't find section "CopyFile.XP.Sys" -
installation may be incomplete

```
The GUI for ndiswrapper in system>admin shows invalid driver

What am I doing wrong here? :mad:

---

### Post by MikeJ112 on 2008-03-16
Ok ive added it in using the GUI and tried to install but now im getting this

```
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ 
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ ndiswrapper -m
module configuration already contains alias directive

mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ modprobe ndiswrapper
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ ifdown wlan0
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ sudo ifup wlan0
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mike@ubuntu:~/Desktop/Files/Drivers/WINXP$ 

```

---

