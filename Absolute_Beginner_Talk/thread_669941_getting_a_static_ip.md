---
title: "getting a static ip"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by ziggy54354 on 2008-01-16
Hi guys, completely new to ubuntu/linux and i'd like to create a static ip for my box. I have network interfaces, wired, and wireless. I am using the wireless one. 

so right now im editing /etc/network/interfaces and changing to:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.9
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

and then doing:
sudo /etc/init.d/networking restart

this is however not working... could someone help me out???

---

### Post by zero-9376 on 2008-01-16
just wondering why you aren't using the network configuration tool in system>administration>network. 
if you are trying to learn i would make the changes in there and then see what happens to the interfaces file

---

### Post by ziggy54354 on 2008-01-16
haha, ok i didn't even know about that... like i said im completely new! I'll give that a shot though thanks!

---

