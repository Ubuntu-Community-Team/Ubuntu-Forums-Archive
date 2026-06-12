---
title: "Routing with ubuntu"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by maxwas on 2006-09-17
I would like to get into doing some routing through my ubuntu test box. 

Is there any gui software i can use for routing, instead of me having to use the command line.

Thx

Max

---

### Post by foolsh on 2006-09-17
firestarter has a pretty good gui and network setup wizard
you can forward ports and port ranges
allow and disallow ipaddress and port ranges
i use it its good :cool: 
although it does not support bridged connections right off the bat you can modifiy the /etc/firestarter/configuration file and change 
```
# --(Internal Interface--)
# Name of internal network interface
INIF="eth*n*"
```
 to 
```
# --(Internal Interface--)
# Name of internal network interface
INIF="br*n*"
```
of course after you installed bridge-utils
and configured your /etc/network/interfaces file to something like this an restart your network services
```
# This file describes the network interfaces available on your system
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
        map eth1

# The primary network interface
iface eth1 inet dhcp

iface eth2 inet static
address 0.0.0.0
netmask 255.255.255.0

iface eth0 inet static
address 0.0.0.0
netmask 255.255.255.0

iface br0 inet static
address 192.168.0.1
netmask 255.255.255.0
bridge_ports eth2 eth0


```

---

