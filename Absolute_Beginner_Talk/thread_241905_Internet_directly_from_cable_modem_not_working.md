---
title: "Internet directly from cable modem not working"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by adiofm on 2006-08-22
Installed Ubuntu 6.06, everything is configured, I have two network cards on the system, they are both reading as Eth0 and Eth1. They are set to DHCP. I connect Ethernet cable, no internet. I check the Network setting properties and set the DNS to the same as my windows machine, still nothing. I look at network tools, the card that is connected via Ethernet cable is recieving lots of packets. I'm not getting any page up on firefox.

Anyone know what's up?

---

### Post by David Corrales on 2006-08-23
Let's see if you're having a problem receiving an ipaddress. This just happened to me on a box because Ubuntu was loading an incorrect driver.
Go to a console and type **ifconfig**.
The NIC connected to the cable should have an IP assigned to. Additionally, you can run **sudo dhclient** to see if you're getting any DHCP offers.
Once that's settled, we can move on into the troubleshooting :)

---

### Post by nanotube on 2006-08-23
another thing - cable modem needs to be rebooted when you connect a new device to it, since the IP it requests is dependent on the MAC address of whatever you connect to it.
so, after connecting your comp to the cable modem, reboot the cable modem, and then see how that goes. (make sure you have your network settings to get everything automatically through dhcp, unless your ISP explicitly says otherwise)

---

