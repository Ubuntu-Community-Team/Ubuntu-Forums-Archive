---
title: "ubuntu not recognizing my router or lan card"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by pdog1337 on 2008-02-11
hi I am current posting this on vista :( as ubuntu isnt recoignizing my belkin router or my network card
I installed it from a live disk version 7.04 have no idea what to do any help?
thanks

---

### Post by johnn1949 on 2008-02-11
Have you worked through this guide?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

It's probably your card driver.

Here's a list of Belkin cards with info on whether theywork out of box or need some tweaks.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

Good luck.

John

---

### Post by pdog1337 on 2008-02-12
not using wireless Im using a belkin router to connect to the net tried typing the routers ip into firefox didnt connect

---

### Post by pdog1337 on 2008-02-12
bump

---

### Post by anewguy on 2008-02-12
If you're not wireless then you must be hardwired.  In that case, do you have MAC filtering turned on on the router?  You say you can't connect to your router - I assume you mean to do maintenance on the router.  Have you tried a regular net address?

What type of NIC are you running on your PC?

:)

---

### Post by pdog1337 on 2008-02-12
[IMG]http://i30.tinypic.com/2ls6vxf.jpg[/IMG]

---

### Post by pdog1337 on 2008-02-12
any help?
thanks

---

### Post by dstew on 2008-02-12
Try to re-start the NIC driver:```
sudo rmmod e1000
sudo modprobe e1000
```

---

### Post by louieb on 2008-02-12
To see what network devices Ubuntu sees
```
ifconfig
```If you see a listing for eth0 or eth1 that looks something like this:  then it sees your network card. 
```

eth1      Link encap:Ethernet  HWaddr 00:07:E9:78:B3:80  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe78:b380/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:488884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121300187 (115.6 MB)  TX bytes:16376132 (15.6 MB)


``` Then try to get an ip address from your router.
```
sudo dhclient   
```I am puzzled why a wired connection isn't working. It would be useful of you could copy  the output  of the above commands and paste them in a file. and save on a usb stick. Then go back to VISTA and post the output here.

One thing more: Did you hibernate windows before starting Ubuntu? Sometimes that will put the network card to sleep and it won't do anything.

---

