---
title: "HELP!! Wireless"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-06-18
****
Hello
i
I have managed to connect my wirless lan cardbus EW-7108PCg IEEE 802.11g Edimax, but, as I will show, it does not seem to recognice the driver. Moreover, It found the WLAN that I have set up, but can not connect to it.
Here are the tests I did:

@wow:~$ ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:35 errors:0 dropped:0 overruns:0 frame:0
TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2632 (2.5 KiB) TX bytes:2632 (2.5 KiB)

ra0 Link encap:Ethernet HWaddr 00:0E:2E:94:B7:CA
inet6 addr: fe80::20e:2eff:fe94:b7ca/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:14614 errors:0 dropped:0 overruns:0 frame:0
TX packets:851 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1071983 (1.0 MiB) TX bytes:200 (200.0 b)
Interrupt:9

@wow:~$ ping 192.168.0.1
connect: Network is unreachable
@wow:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:0e:2e:94:b7:ca
Sending on LPF/ra0/00:0e:2e:94:b7:ca
Listening on LPF/eth0/00:a0:cc:c0:15:29
Sending on LPF/eth0/00:a0:cc:c0:15:29
Sending on Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15

Moreover when running the device manager it gives me that the vendor is RALink Device is unknown (0x0301) Bus type PCI

In network tools it confirms unknown interface (raO)
IPv6 fe80::20e and so on
I was thinking that maybe disabling IPv6 could do the trick.

Running wireless assistant it shows me the network but does not connect. When I run it it asks: "you might have insufficient permission for wireless assistant to function properly"
"Did you run it using 'sudo'?" it asks, I organiced with synaptic. Should I run it in terminal?

Any help would be grately apreciated
__________________

---

### Post by killkoy on 2006-06-18
i get the same [http://www.ubuntuforums.org/showthread.php?t=197909&page=2](http://www.ubuntuforums.org/showthread.php?t=197909&page=2)
I think i have the same network card as you. This guide might be helpfull:
[https://wiki.ubuntu.com/WifiDocs/Driver/RalinkRT2500](https://wiki.ubuntu.com/WifiDocs/Driver/RalinkRT2500)
and maybee this:
[http://www.ubuntuforums.org/showpost.php?p=1090862&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1090862&postcount=29)
any help with this would probably be useful for me as well,:p as you can see from the above thread

---

### Post by wannabesurfer on 2006-06-18
I will keep you updated.... but did you manage to fix it, are you connected with the card?????

---

### Post by killkoy on 2006-06-19
ok i managed to connect to the card by using system/administration/network but only when my network was encrypted using wep with a ascii key entry method. this isnt ideal for me as all other pcs are set up using wpa encryption, but its a start and might enable me to get software /files/help that allows me to use wpa encryption.

---

### Post by uzi09 on 2006-06-19
have you tried the network manager tool? check it out here:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

and its wiki.....
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

