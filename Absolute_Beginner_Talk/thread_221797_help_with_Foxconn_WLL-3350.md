---
title: "help with Foxconn WLL-3350"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by ceborame on 2006-07-24
This is a wireless connection pproblem

I cannot get my Foxconn WLL-3350 to connect to my router Netgear DG834.

It is showing as active and the network monitor icon gives me 80-85% signal strength, but its status is disconnected.

I have entered ssid and left dhcp alone.

Even when I turn off wep in the router I still don't connect.

I would really appreciate some help with this please.

Thanks

---

### Post by risbac on 2006-07-24
Network icon monitor means the default Ubuntu one, or Network Manager? 

If you didn't install and run Network-Manager, I would advise you to try. Usually it's a much easier solution to connect to a wireless network, especially if you have a WPA or WEP key. 

If it's not working, you should look at the logs to see if you have any error message. Try to connect, then run dmesg in a terminal, and look at the end, try to find something related to a network problem.

---

### Post by ceborame on 2006-07-24
Thanks, with network manager icon I mean, if you right click at the top right of screen, then add the network icon. If you then click properties,information such as the signal strength and connectivity are shown.

I have not installed network manager, is this where my problem lies ?

Thanks

---

### Post by ceborame on 2006-07-24
bump

---

### Post by emilde on 2006-08-21
Finally found this article that helped me fix my problems with this card:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

Hope it helps someone else

---

