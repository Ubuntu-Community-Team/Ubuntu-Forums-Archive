---
title: "New Network Card - unable to lookup  via gethostbyname()"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by bathtoy on 2007-01-18
My onboard network port ceased to work due to some sort of hardware failure. 
To solve the problem I installed a new PCI network card (a NIC as it is often reffered?).
I disabled the onboard port in my bios (used to show up as eth0 in Ubuntu), and now it appears that the new card is eth1(eth0 no longer shows up in Ubuntu).

All seems to be working fine (network, browsing, etc) but I cannot run any root(sudo) applications(synaptic, etc)

What is the problem? I am aware that the /etc/hosts file may have something to do with this, but I think mine is alright, it follows (ubunntu is computer name) - 

127.0.0.1 localhost 
127.0.1.1 ubunntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I am asuming the eth0 to eth1 transition is causing the problem? Any help greatly appreciated! - Ubuntu ver. = Dapper

---

### Post by xyz on 2007-01-18
This should help, I think:
[ by taurus]("http://www.ubuntuforums.org/showthread.php?t=338620&highlight=unable+to+lookup+via+gethostbyname")

---

### Post by bathtoy on 2007-01-18
Thanks for the speedy response!
The linked solution worked perfectly!
Turns out my /etc/hostname file was missing the name.

---

