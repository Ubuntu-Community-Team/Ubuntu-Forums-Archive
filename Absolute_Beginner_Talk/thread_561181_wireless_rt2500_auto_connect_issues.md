---
title: "wireless rt2500 auto connect issues"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-09-27
my rt2500 wont connect to a wireless network on startup, however when I use KDE's Wireless Assistant it will connect.

heres my /etc/network/interfaces
```

auto ra0
iface ra0 inet static
        address 192.168.1.77
        netmask 255.255.255.0
        gateway 192.168.1.1

        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid NETGEAR
        pre-up iwconfig ra0 mode Managed
        pre-up iwconfig ra0 key 2627xxxxxx
        pre-up ifconfig ra0 up

```

also tried using the simpler:
wireless-essid NETGEAR
wireless-key 262xxxxxx

but didn't work either.


strange thing is it sets the IP correctly and iwconfig shows that its on the NETGEAR wap but the link quality is 0/100 and its not connected.

---

### Post by Gone fishing on 2007-09-27
Mine looks like:

iface ra0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid fish
wireless-key s:xxxxxxxxxx

auto ra0

I'm using a Gigabyte PCI wireless card with an rt2500 chipset it works fine. However, I've never got the automatic wireless network config tool to work, but manual gui no problem system > administration > network

---

### Post by Austin_KW on 2007-09-27
I use WPA and dhcp, but the sequence (for your config) would be
```

auto ra0
iface ra0 inet static
        address 192.168.1.77
        netmask 255.255.255.0
        gateway 192.168.1.1

        pre-up ifconfig ra0 up
        pre-up iwconfig ra0 mode Managed
        pre-up iwconfig ra0 essid NETGEAR
        pre-up iwconfig ra0 key 2627xxxxxx
        pre-up iwconfig ra0 essid NETGEAR

```

The main difference is doing the config when the interface is up,

---

### Post by PetePete on 2007-09-27
nope still doesn't work..

iwconfig reports that its not connected to anything.

could it be that one of the other settings (GUI ) ive played with is over riding my manual config?

---

### Post by Austin_KW on 2007-09-27
could be,

Does the terminal command "sudo ifup --f ra0" establish a connection, this will force an ifup using the config in the interfaces file, It will also tell you if there is any errors in the interfaces file stopping it completing

---

### Post by PetePete on 2007-09-27
running that worked fine!
```

#pete@pete-laptop:~$ sudo ifup --f ra0
Password:
There is already a pid file /var/run/dhclient.ra0.pid with pid 15444
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:13:d3:xx:xx:77
Sending on   LPF/ra0/00:13:d3:xx:xx:77
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 35872 seconds.

```

weird..

---

### Post by Austin_KW on 2007-09-27
That is more than wierd, Have you got a second ra0 config in the interfaces file, one with DHCP?? because that is not a static IP address.

---

### Post by Austin_KW on 2007-09-27
Change your router SSID from the default NETGEAR to something like PeteNet, because it is also possible you are not connecting wher you think you are!

---

### Post by PetePete on 2007-09-27
sorry should have mentioned that I changed it to DHCP to make it simpler... which is why its gone dhcp.

Austin_KW, I tried that before but made no difference.... and ive scanned all the access points around me and none are netgear .... good idea though, didn't think of that!

is there someplace where i could make a script to execute "ifup --f ra0" with root priv to be run after /etc/init.d/networking has been ran?

---

### Post by Austin_KW on 2007-09-27
Add the command to /etc/rc.local (before the exit). rc.local is run at the end of the boot sequence but it may be overridden by a gui setup that runs at you login.

---

