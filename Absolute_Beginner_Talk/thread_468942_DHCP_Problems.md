---
title: "DHCP Problems"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Mark1948 on 2007-06-09
I have finally got Linux running, doesn't sound much but I am smiling LOL

Anyway I have an issue with my Intel 3945 WiFi card. In manual connection if I set the IP, mask and gateway it is fine but DHCP doesn't work. Is the Linux DHCP protocol different to Windows or is this a bug/issue?

The 3945 is listed in "restricted drivers" along with my ATI x1600 mobility card, that might be relevant it might not but I am just making note of it.

I have downloaded the Linux drivers from Intel's website and looked at the install instruction :o OMG. I thought Linux install was download and click like XP but boy was I wrong. Oh well I enjoy a challenge so let's play :) ...........

---

### Post by Skrynesaver on 2007-06-09
The DHCP protocol is the same for all OSes.
What happens if you run a manual 
```

dhclient eth1

```
or whichever is your wireless interface?

---

### Post by Mark1948 on 2007-06-09
eth1 is my wireless. It returns:

mark@ubuntu:~$ dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted


Cheers
Mark

---

### Post by pardesi on 2007-06-09
what i can't understand is if it is your DHCP ubuntu should have sensed of it's own it should have been automatic.But if you have a static IP address then go to 
**System<Adminstration<Network<Properties**
change that to static .enter your IP adress, Netmask,gateway under static IP option...

---

### Post by Skrynesaver on 2007-06-09
Stick a sudo infront of it and try again ;) ie.
```
sudo dhclient eth1
```

---

### Post by Mark1948 on 2007-06-09
> **Skrynesaver said:**
> Stick a sudo infront of it and try again ;) ie.
```
sudo dhclient eth1
```

Yep that works

mark@ubuntu:~$ sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:de:2e:a4:cf
Sending on   LPF/eth1/00:18:de:2e:a4:cf
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.252
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.252
bound to 192.168.2.80 -- renewal in 40970 seconds.


Another piece of info is it is only a problem on wireless. If I plug the RJ45 cable in eth0 gets an IP of the DHCP first time.

Cheers :)

---

### Post by darkfame on 2007-06-09
> **Mark1948 said:**
> 
I have downloaded the Linux drivers from Intel's website and looked at the install instruction :o OMG. I thought Linux install was download and click like XP but boy was I wrong. Oh well I enjoy a challenge so let's play :) ...........

Don't worry about the installation instructions, Ubuntu and the restricted device manager handles everything for you.

---

