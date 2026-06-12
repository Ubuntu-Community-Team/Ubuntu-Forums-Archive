---
title: "eth1 disconnected"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by hiikeeba on 2008-02-18
I  have a Dell Inspirion 1420n.  I had been able to connect to my home network via eth1 by configuring it to be a Local Zeroconf Network, then applying that, then changing it back to "Automatic Configuration."  Last week, I went to a hotel, and enabled roaming mode and connected to the Internet easily.  When I returned home, eth1 showed it was disconnected.  How can I restart the card?

---

### Post by Nxion on 2008-02-18
Type this in a terminal

```
sudo /etc/init.d networking restart 
```That should do the trick.

---

### Post by hiikeeba on 2008-02-18
> **Nxion said:**
> Type this in a terminal

```
sudo /etc/init.d networking restart 
```That should do the trick.

Thanks for the response, however, I get this message:

"sudo: /etc/init.d: command not found."

---

### Post by Tatty on 2008-02-18
Think there was a small typo in that,  its meant to be 

```
sudo /etc/init.d/networking restart
```

:popcorn:

---

### Post by bradmayne on 2008-02-18
try sudo eth1 up

also dmesg grep and post the results

---

### Post by hiikeeba on 2008-02-19
Got this message first:
sudo: eth1: command not found

When I enter the second command i get a very long message  that the forum will not let me post because: "You have included 10 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator."

I cannot attach it because: "Your file of 32.0 KB bytes exceeds the forum's limit of 19.5 KB for this filetype."

I'm stumped.

---

### Post by hiikeeba on 2008-02-19
> **Tatty said:**
> Think there was a small typo in that,  its meant to be 

```
sudo /etc/init.d/networking restart
```

:popcorn:

I entered to code and got this:

 * Reconfiguring network interfaces...                                                                                                                       RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 6377
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:a7:c8:86
Sending on   LPF/eth1/00:1b:77:a7:c8:86
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "jerrt".
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:a7:c8:86
Sending on   LPF/eth1/00:1b:77:a7:c8:86
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by hiikeeba on 2008-02-23
Okay.  Thinking upgrading to 7.10 would help, I upgraded.

No dice.

Eth1 is still disconnected.

Anyone know where to get a cheap copy of Windows XP?

---

