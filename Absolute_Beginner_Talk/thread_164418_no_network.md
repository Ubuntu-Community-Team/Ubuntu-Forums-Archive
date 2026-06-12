---
title: "no network"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-04-22
i installed ubuntu 4.1 on a computer with no network cable in while installing and now it wond connect to the network and i cant find the update utility

---

### Post by johnny2211 on 2006-04-22
Unplug the network cable, then plug it back in. After that type: dmesg | grep eth

We are trying to find what is the name of the interface. Probably eth0.

After that edit /etc/network/interfaces

Case 1. You don't have a DHCP server and are using static addresses
-------cut-------
auto eth0
iface eth0 inet static
      address 192.168.0.2 #or whatever
      netmask 255.255.255.0 #probably the same
      gateway 192.168.0.1 #if you go on the internet through a router
-------cut--------

Case 2. You have a DHCP server and have dynamic addresses
-------cut-------
auto eth0
iface eth0 inet dhcp
-------cut-------


Ofcourse I can't know your ip configuration you will have to change the numbers and the eth number to reflect your configuration.

Have Fun

---

