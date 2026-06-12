---
title: "Another one not able to get online"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by insanekaosx on 2006-11-08
First off, running Dapper. 


So, we have yet another internet connection issue. I'm running the itnernet through a network *Tried directly into the internet as well, that didn't work on the spot either, so....* I've tried the Nvidea card that came onboard on the computer, and another ethernet card *unlabelled, and I can't remember what it is at the moment* I ran the ifconfig and dhclient, having searched, tried fixes on the forums, and seen this request about everywhere. I probably screwed somethign up somewhere.

I've got the PC wirh Ubuntu running next to me here, thanks ahead for any assistance. Just request anythign you need from me. 

```
insanekaosx@Corbulo:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:CA:89:59:ED
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:A0:C9:0A:C8:1D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:225305 (220.0 KiB)  TX bytes:8118 (7.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24604 (24.0 KiB)  TX bytes:24604 (24.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**********************************************************************

insanekaosx@Corbulo:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   LPF/eth1/00:a0:c9:0a:c8:1d
Listening on LPF/eth0/00:40:ca:89:59:ed
Sending on   LPF/eth0/00:40:ca:89:59:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by Iowan on 2006-11-08
IPV6 has been known to cause problems - There are better links available, but here's one for starters:
[http://ubuntuforums.org/showthread.php?t=292661]("http://ubuntuforums.org/showthread.php?t=292661")

---

### Post by dbott67 on 2006-11-08
Can you please describe your network layout.  What type of internet connection do you have (DSL, cable, dial-up, etc.)?  Do you have a router (D-Link, Linksys, Netgear, etc.)?

Please post the output of:
```
cat /etc/network/interfaces
```
```
route -n
```
```
cat /etc/resolv.conf
```

Thanks,
Dave

---

### Post by insanekaosx on 2006-11-09
I've got a cable connection *RCN* Running through to a Linksys router (EtherPort 10/100), which splits to the Mac I'm using now, and into a wire up to my computer. I had another wire plugged in while I had the PC on the ground in here, but it took up space other people needed, so it now back where it belongs, not yet plugged in. I'll get you those results tommorow :D
       
                                     Mac
Cable company->Modemthinger->router<
                                     PC

Something like that. Again, I'll get the results tommorow, and fill you in. Thank you, Dave :D

-Matt

---

### Post by dbott67 on 2006-11-09
Hi Matt,

I've whipped up a little diagram indicating how it should be setup (it may already be this way, I'm just not sure I follow your last post).  The modem provided by your ISP would sit between the Linksys router and the "internet cloud".

[[IMG]http://img132.imageshack.us/img132/5081/mattslanfo9.th.png[/IMG]](http://img132.imageshack.us/my.php?image=mattslanfo9.png)

By default, most computers are set to use DHCP to automatically configure themselves for the network (especially if you have a Linksys router or similar device).  Just make sure that the 'DHCP server' is turned on in the router (again, it probably is already, as that is the default).

Plug the patch cable in the NIC on your Ubuntu computer and enter the following commands:
```
sudo ifdown eth1
```
```
sudo ifup eth1
```
```
sudo dhclient eth1
```

The eth1 is the variable... your computer may be using eth1 (it seems to be the device receiving packets --- see the TX & RX bytes), but you also have eth0.

-Dave

---

### Post by insanekaosx on 2006-11-09
Yeah, thats how my network is set up. I'm jsut bad at describing thigns >> The two Eth's are because I have the onboard card and the card my friend lent me, which is eth1, the one I have it plugged in trhoguh

I haven't changed router settings at all, so that should still be set at DHCP, I'll take a double look, though... Considering this computer gets on via DHCP *shrug*

Here's those results for ya.


```
insanekaosx@Corbulo:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
```

insanekaosx@Corbulo:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```
```
insanekaosx@Corbulo:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
```
insanekaosx@Corbulo:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
```
insanekaosx@Corbulo:~$ cat /etc/resolv.conf
<brought up nothing>
```

```
insanekaosx@Corbulo:~$ sudo ifdown eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   Socket/fallback

```

```
insanekaosx@Corbulo:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
```
insanekaosx@Corbulo:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   LPF/eth1/00:a0:c9:0a:c8:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Continual thanks.
-Matt

---

### Post by dbott67 on 2006-11-10
Hi Matt,

Here's a few things to try:

To figure out the network hardware detected:
```
sudo lshw -C network
```
You should see 2 interfaces --- the built-in one, plus the one you added.  Example from my computer:
```
dbott@thedrake:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       **[COLOR="Red"]vendor: D-Link System Inc[/COLOR]**
       physical id: b
       bus info: pci@02:0b.0
       **[COLOR="Red"]logical name: eth0[/COLOR]**
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d000-d0ff iomemory:ed800000-ed8000ff irq:185
```
You can see that my D-Link NIC is 'eth0'.  In your case, it should indicate which NIC is associated with which logical name (eth0 or eth1).

When looking at your **/etc/interfaces** file, I notice that 'eth0' is not set to 'auto'.  We could try activating it and see what happens.  Edit the file and put 'auto eth0' above the line:
```
[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet dhcp
```

You can also try manually activating interfaces using the commands:
```
sudo ifdown eth0
```
```
sudo ifup eth0
```
```
sudo dhclient eth0
```

One other issue that may be causing the problem is the ISP cable modem.  I have seen frequent issues where the MAC address of an old network card gets 'stuck' in the arp routing table and causes all sorts of problems.  Try 'resetting' the cable/DSL modem (there should be a switch or button on the back of the unit.  IF not, just unplug it for a couple of minutes.  Also, unplug your router:

1. Power off router
2. Reset / power off cable modem thingy
3. Power on cable modem thingy
4. Wait until the lights stop blinking & what-not
5. Power on router
6. Wait a minute or so
7. Try commands from above in Ubuntu.

Keep me posted.

-Dave

---

### Post by insanekaosx on 2006-11-10
Well, I restarted the network, I ran the up and down again. I tried. It still ain't running. Its odd, the network says its sending and recieving things, but it won't get the DHCP. I will need to try a static connection soon., but I'm going to check on the DHCP of the network first. See if somethigns up in there...

Its not the network, since like I said, this computer is connecting via DHCP just fine. If you want to see any of the outputs again/see if theirs a change, jsut lemme know.

---

### Post by insanekaosx on 2006-11-11
You must be joking ><

So turns out this little thing her that I THOUGHT was a router... its just a hub. 


Stupid thing.

I'm going to take a look at the network around her ea bit, see what I can do.

Old wireless router *also linksys* works as a wired router as well. Going to try and see how this runs now. HOping fo rthe best.


-Matt

---

### Post by insanekaosx on 2006-11-11
Problem solved ><

After all the hatred that brewed through me over this, it was simply a matter of the hub being screwy. The hub I thought was a rotuer, but still.

Using the wireless router, which has wire access as well, as our router now. All is well. I am posting this from the lovely Ubuntu :)

---

