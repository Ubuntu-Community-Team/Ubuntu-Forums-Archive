---
title: "Still can't recieve IP/DNS from wired broadband.."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by torgeir89 on 2007-11-05
I have two computers I'm installing Ubuntu on. In windows they both have no problem getting an internet connection (they're on DHCP), recieve IP and DNS automatically. 

In Ubuntu, though, it can't seem to connect automatically. I've installed Ubunto on one of the computers, and the other one I tried from the live CD. It "looks" like it's connected, the network manager says "connected" etc, but when I click "more information" my IP, DNS, etc comes up as "0.0.0.0". So it's obviously not recieving IP/DNS correctly.

Any help would be appreciated, I really don't want to move back to windows.

---

### Post by sailor2001 on 2007-11-05
in system/admin/network  is your wireless recognized? Click on it and properties and uncheck roaming

---

### Post by hyper_ch on 2007-11-05
Add nameservers to your resolv.conf file located at /etc/resolv.conf

sailor: How do you know it's a wifi?

---

### Post by bumanie on 2007-11-05
Can't pretend to be any kind of expert, however I believe it is possible that your system is incompatable with ipv6, which was not on feisty. You could try getting a firmware upgrade for your modem or possibly read this site and if you feel comfortable, follow their suggestions.
[http://www.lockergnome.com/nexus/linux/2007/10/24/ubuntu-gutsy-internet-help](http://www.lockergnome.com/nexus/linux/2007/10/24/ubuntu-gutsy-internet-help)
As a side issue I even had trouble connecting to the net on windoze when ipv6 was first released and foisted upon me by the 'great' guys at M$.
My ISP said the modem was connected to the net, but my modem and computer were no longer communicating. In windoze I got rid of ipv6 and everything was OK. At this time, feisty had internet access as it did not contain the ipv6 stack.

---

### Post by aonegodman on 2008-06-05
I've got the exact same problem.

Charter HS Cable works fine on Windows XP laptop, not working on Ubuntu desktop.

I have a hardwired ethernet connection direct from cable modem, no router, no wireless.

---

