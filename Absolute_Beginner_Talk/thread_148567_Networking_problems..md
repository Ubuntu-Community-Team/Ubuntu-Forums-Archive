---
title: "Networking problems."
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by joewhite on 2006-03-22
When I installed Ubuntu all I had to do to get my network working was activate Eth0 just the one time. It detected everything fine and I had no startup errors. Now when I boot up the Internet is switched off until I manually reactivate it through the console in KDE by typing 'sudo dhclient eth0'. I also have to reactivate my printer with 'sudo ifconfig lo up' and 'sudo /etc/init.d/cupsys restart'. The boot-up screen indicates all services are starting OK accept for failing to resolve ntp.ubuntu.org and a Samba daemon error. All these problems seem to be related since they started at the same time. Although it would be quicker to make a start up script with the above commands as a temporary fix I want to get things back to the way they were so I don't have any more problems. I have a Belkin Wireless G router but even without it connected I have the same problems. Any ideas?

---

### Post by steve.horsley on 2006-03-22
Have a look at /etc/network/interfaces. Check they are set for auto. Use **man interfaces** for details. Here is a copy of mine for reference:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


---

### Post by joewhite on 2006-03-22
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp

auto eth0

iface eth1 inet 

Mine looks OK.

---

