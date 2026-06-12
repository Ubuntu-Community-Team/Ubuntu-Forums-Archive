---
title: "How to invoke network configuration on Ubuntu server from command line"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by kenquad on 2006-07-22
Hi all:

Just getting started with Ubuntu server for a small office environment.  Network needs configuring but netconfig comes up with command not found.  Is there a tool in the server version or do I need to edit a configuration file?  If so, where would that file be located?

Thanks,
Ken Ha Quad

---

### Post by cwaldbieser on 2006-07-22
> **kenquad said:**
> Hi all:

Just getting started with Ubuntu server for a small office environment.  Network needs configuring but netconfig comes up with command not found.  Is there a tool in the server version or do I need to edit a configuration file?  If so, where would that file be located?

Thanks,
Ken Ha Quad

/etc/network contains the config files.
The "ifconfig" command can be used to configure network interfaces interactively.  The "route" command can set up static routes.  "dhclient" can be used to set up a network card via DHCP.

---

### Post by chalex on 2006-07-22
Also check out 
/etc/init.d/networking {start stop restart}

---

### Post by lamego on 2006-07-22
The network interfaces configuration is stored on:
/etc/network/interfaces
An example for setting up eth0 with dchp:
```
iface eth0 inet dhcp
```
Another example now using a static IP
```
iface eth0 inet static
address 172.16.129.98
gateway 172.16.129.1
netmask 255.255.255.0 
```

---

### Post by dismalley on 2006-09-19
I have been unable to us
ifconfig eth0 # 

I get
error fetching interface information: Device not found

With # being the IP I need to change.  Even then I am only changing the last set of numbers

---

