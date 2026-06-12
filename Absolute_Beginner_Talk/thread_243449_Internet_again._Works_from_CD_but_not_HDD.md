---
title: "Internet again. Works from CD but not HDD"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by DavidBell on 2006-08-25
I am trying Ubuntu, and when booting direct from the CD my internet is working fine, but when I installed to HDD it doesn't work any more. I can go back and boot from the CD and it still works there. It's a bummer because ubuntu obviously is capable of using my internet access, but for some reason wont let me in the HDD version.


Details are

6.06 Installed on logical partitions 5/6 (ext3/swap) on second HDD in a triple boot system (other two are WinXP). Modem is Speedtouch 536 ADSL (just a modem I think no router) connected to ethernet card. ISP is Bigpond.

I checked everything in System|Preferences|Network Proxy, System|Admin|Networking and Ssytem|Admin|Network Tools, and settings all look exactly the same for CD & HDD installs (except hostname changed from 'ubuntu' to 'david-desktop'

Any advice where else to look? I wondered if it was something to do with security/privileges but have not found anything relating to net access. 

TIA David

---

### Post by TLE on 2006-08-25
Please try and see if it helpd to shutdown the internet and start it up again. Type this in terminal:
```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by DavidBell on 2006-08-25
(TLE) I switched the modem off/on and did get intenet for maybe 1 minute then it stopped again. It's alive! (sort of)

Ran your commands in terminal with following output, but haven't been able to get internet back.

Thanks for your help so far. David.

_Terminal output_

```
david@david-desktop:~$ sudo ifdown eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:80:ad:75:7f:e3
Sending on   LPF/eth0/00:80:ad:75:7f:e3
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.0.138 port 67
david@david-desktop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:80:ad:75:7f:e3
Sending on   LPF/eth0/00:80:ad:75:7f:e3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
david@david-desktop:~$
```

---

### Post by TLE on 2006-08-25
I'm sorry but then I probably can't help you, it was just because it sounded just a problem I have. But if those commands don't work, then it isn't. So I hope somebody else steps in and helps you.
Sorry

---

### Post by syedn on 2006-08-25
What kind of internet service do you have?

If you have ASDL over PPPoE (aka, DSL but you have to "dial it in" with a username & password) try the following in terminal:

```
sudo pppoeconf
```

I'll check this after class, hope that that's a solution!

---

### Post by gentlemanmasher on 2006-08-25
Not sure if this might be the case but it ended up being my ehternet card.  


Tulip is what it was showing as I used this fix and it worked like a charm.

[http://ubuntuforums.org/showthread.php?t=202884](http://ubuntuforums.org/showthread.php?t=202884)

---

### Post by DavidBell on 2006-08-25
Seems to be working now. [http://ubuntuforums.org/showthread.php?t=202884](http://ubuntuforums.org/showthread.php?t=202884) describes the problem better, solution is in [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

Thanks DB

---

