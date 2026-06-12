---
title: "Lost my networking"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by seattle vic on 2008-04-21
Hello,

I've installed virtualbox under Gutsy and have been running both windows 2000 and xp successfully for several months using NAT. I got USB working, but decided to try and connect to the host system to use CUPS as a print server, as I have an an HP 6p laser that only has a parallel port interface.

So I figured I needed a host interface. I followed the vbox doc's to change the /usr/network/interface file to add br0, but when I restarted it, neither the virtual or host networking functions. When I restore the interfaces file to it's original condition, again nothing works.

Here's my interface file before and after:
=================================
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
gateway 192.168.2.1
====================================
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
gateway 192.168.2.1

auto br0
iface br0 inet dhcp
bridge_ports eth0
=======================================

then per the instructions, I added vbox0:

sudo VBoxAddIF vbox0 vic br0

The only thing I can figure is that because my host uses static ip, maybe that's conflicting with asking br0 to be dhcp. But why does nothing work once I revert back to the orginal file? I'm writing this on another machine of course.

Frustated,

Vic

---

