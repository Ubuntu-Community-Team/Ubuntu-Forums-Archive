---
title: "Stitic IP internet connection"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by teodor_ on 2007-10-08
I recently chagneg my ISP. The old one worked with PPPoE, and had no problems configuring it. Now I am with a stitic IP, and I filled the adresses of gateway etc. ifconfig says that eth0 is UP AND RUNNING, but dont have internet connection.   I tried installing Debian, and it gave me a message that the gateway is unreachable, and it wrote another address. I everything, but I can't connect.


What shall I do ???

---

### Post by skymera on 2007-10-08
can you try DHCP?

---

### Post by teodor_ on 2007-10-08
doesnt work, it says that eth0 works, but i dont have internet connection. Cant update software, cant surf sites.

---

### Post by skymera on 2007-10-08
im sorry i dont know much about connections :(

try 

sudo ifconfig eth0 up

replace eth0 with device

---

### Post by Dr Small on 2007-10-08
Try to restart networking:
```
sudo /etc/init.d/networking restart
```

---

### Post by bodhi.zazen on 2007-10-08
Try ```
sudo dhclient eth0
```

Post any error messages.

---

### Post by teodor_ on 2007-10-08
eth0      Link encap:Ethernet  HWaddr 00:0D:61:3A:4B:B9 
          inet6 addr: 2002:4e5a:3334:6:20d:61ff:fe3a:4bb9/64 Scope:Global
         inet6 addr: fec0::6:20d:61ff:fe3a:4bb9/64 Scope:Site
        inet6 addr: fe80::20d:61ff:fe3a:4bb9/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:319694 (312.2 KiB)  TX bytes:3178 (3.1 KiB)
       Interrupt:201 Base address:0x8000 

teodor@teodor-desktop:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... 
                                         SIOCADDRT: Network is unreachable
Failed to bring up eth0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by bodhi.zazen on 2007-10-08
Those error messages usually occur when you have a problem with the gateway.

You should confirm the gateway address with your IP.

---

### Post by teodor_ on 2007-10-09
how to confirm the gateway? this is the gateway that my ISP gave me and it works fine in Win. Is there a special gateways for Windows and other for Linux ??

---

### Post by bodhi.zazen on 2007-10-09
OK, the gateway is the same with both windows and your IP provider.

Do you use a router ? Have you tried using your router IP as the gateway ?

---

### Post by teodor_ on 2007-10-09
I use an Ethernet switch, I share internet connection with my roommate. It's TP-Link  TL-SF1008D. But how do I find out what's its IP ?

---

### Post by bodhi.zazen on 2007-10-09
Ah, could you ask your room mate or look at the gateway s/he uses?

If you are getting an IP from a local router, you need to use the router IP as the gateway.

Also can you post the (working) information from windows and current information from Ubuntu.

Windows, Open a terminal (Start -> run ---> cmd)

```
ipconfig /all
```

Ubuntu

```
sudo ifconfig
```

---

### Post by teodor_ on 2007-10-09
my roommate uses the same settings, but he has different IP. 
Win shows the IP and other settings, that I have inputted, no IP routing, no WINS proxy, no DHCP, and the adresses.

ubuntu ifconfig show the same IP and other stuff that I inputted.  It even shows that eth0 is UP. but when I execute the dhclient it shows "can't bring eth0 up."

what the **** could the it be?!


we turned it into chat, if you want we can use some chat client, and if we fix the problem, I will post the solution only for other with the same problem.
its driving me really really crazy

---

