---
title: "LAN problem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by personado on 2008-01-29
Good day everyone,
I am new to Linux. Did few reading about Ubuntu, and decided to install it alongside with WinXP.
Under the latter there is no problem, however under Ubuntu 7.10 I have a LAN problem. I just cannot ping any node.
After issuing the lshw -C network command, I got the following:

 *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 81
       serial: 00:10:dc:78:b8:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=190.104.100.191 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

So it seems to me that the network driver is installed. What is the problem? Plz help.

---

### Post by OffAxis on 2008-01-29
How's your network set up?

your ip is a bit odd; is this being assigned directly from your ISP (no router or firewall between)?

Do you only have one network card?

When using the 
```
lshw -C network
```
command it'll show things that register as 'network' components. Sometimes ethernet cards get registered as type 'bridge', and would not show up with this command.

A more useful command in this instance would be
```
ifconfig
```

What's that look like?

---

