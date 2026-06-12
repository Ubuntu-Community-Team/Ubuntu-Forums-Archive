---
title: "Wlan"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by cold-peak on 2006-11-17
Hi all,

Trying to get my Netgear WG111T wireless usb stick to work with Ubuntu 6.10. A while back i managed to get it to work with Suse 10.1, however i am having no luck with Ubuntu.

I have installed the latest Ndiswrapper, and installed the correct drivers and it tells me that the driver is:

"driver installed, hardware present"

however it hasnt seem to have added "wlan0" to anything ie, when i do:

sudo iwconfig

It isnt shown... any ideas?


Cheers,

Conrad

---

### Post by jd65pl on 2006-11-17
have you done

```
sudo modprobe ndiswrapper
```

---

### Post by nickpaton on 2006-11-17
Hi Conrad and welcome to the forums.

Have you tried this guide:

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111")

---

### Post by cold-peak on 2006-11-17
hi there,

that seems to give no output

- i will try this guide ;) - but it looks like i have done pretty much the same.

---

### Post by cold-peak on 2006-11-17
ok i tried

ifup wlan0 and it gave this:

```


root@KUSARI:/home/conrad# ifup wlan0
wlanctl-ng: No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0


```

---

### Post by nickpaton on 2006-11-18
Doesn't look too good.

Since you're using Edgy, you have seen the note right at the bottom of wiki.

Not sure how I can help further - anyone else?

---

### Post by cold-peak on 2006-11-19
Hi there,

i decided to "re-format" and then try it again, and it now works perfectly ;)

Thanks for the guide ;)

---

### Post by nickpaton on 2006-11-19
Congratulations!!:D

---

