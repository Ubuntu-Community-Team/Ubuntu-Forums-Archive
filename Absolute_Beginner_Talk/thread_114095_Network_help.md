---
title: "Network help"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by KingTiger on 2006-01-07
is it passible to have a windows xp computer connect to the internet and have a 
Ubuntu computer connect though it?
in other words:
ubuntu computer connects to the windows xp computer (though a network) and it connect to the internet (dialup)

KingTiger

---

### Post by adssse on 2006-01-07
I would say it is possible. I believe you would need windows internet connection sharing and than run that connection out through a nic card and network cable into the ubuntu computer. The ubuntu computer should see this as just a lan connection. My friend shares his connection this way with his windows computers.

---

### Post by Mission 10 on 2006-01-07
Yes, a linux system and a windows system can be on the same network at the same time.

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=KingTiger]is it passible to have a windows xp computer connect to the internet and have a 
Ubuntu computer connect though it?
in other words:
ubuntu computer connects to the windows xp computer (though a network) and it connect to the internet (dialup)

KingTiger[/QUOTE]
Yes.  Actually, either of the PCs is capable of performing Network Address Translation (NAT) for you.  On XP, it is called Internet Connection Sharing.  On Ubuntu, NAT is most easily accomplished through a Firewall program like Firestarter, though you can use the command line "iptables" if you know the syntax.

---

### Post by KingTiger on 2006-01-08
i set up a network and my windows computer can see the ubuntu computer but cant access it and the ubuntu computer can't see the windows computer.
any one have any ideas on how to fix this?

KingTiger

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=KingTiger]i set up a network and my windows computer can see the ubuntu computer but cant access it and the ubuntu computer can't see the windows computer.
any one have any ideas on how to fix this?

KingTiger[/QUOTE]
You might have to elaborate on what you mean by "the ubuntu computer can't see the windows computer", but I am guessing you mean file sharing / Network Neighborhood.

First, you need to tell us how the computers are physically connected.  Then we need to see the output of
```

$ ifconfig
$ route

C:\> ipconfig
C:\> route print

```
on Ubuntu and Windows, respectively.  This will let us know how the network cards are configured in each PC, and how the routing tables are configured in each.

---

### Post by scylax on 2006-01-08
> On Ubuntu, NAT is most easily accomplished through a Firewall program like
> Firestarter, though you can use the command line "iptables" if you know the
> syntax.

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t NAT -A POSTROUTING -s 192.168.0.0/24 -o eth1 -j MASQUERADE 

supposing our LAN's network address is 192.168.0.0/24 and eth1 is the network interface connected to the internet.

---

### Post by KingTiger on 2006-01-08
ya the file sharing / Network Neighborhood (sorry dont know much about netwroks) and they a connected with a crossover cable (not a router)
___________Ubuntu info__________________
$ ifconfig
eth0
       link encap: ethernet hwaddr00:0c:41:22:d4:4e
inet6 addr: fe80::20c:41ff:fe22:d44e164 scope:link
up broadcast running multicast mtu:1500 metric:1
RX packets:0 errors:0 droped:0 overruns:0 frame:0
TX packets:0 errors:0 overruns:0 carrier:0
collisions:0  TXqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
interrupt:9 Base address:0xe800

LO  
      link encap:local loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet addr: ::1/128 acope:host
up loopback running mtu:16436 metric:1
RX packets:15334 errors:0 dropped:0 overruns:0 frame:0
TX packets:15334 errors:0 dropped:0overruns:0 carrier:0
collisions:0 TXqueuelen:0
RX bytes:888756 (867.9eib) TX bytes:888756 (867.9kib)

$route
        kernell ip routing table
destination gateway genmask flags metric ref use iface


____________windows info______________
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 3:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

PPP adapter Netscape:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 172.198.208.8
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 172.198.208.8

C:\>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 00 e8 97 03 40 ...... HP EN1207D-TX PCI 10/100 Fast Ethernet Adapter -
 Packet Scheduler Miniport
0x20004 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    172.198.208.8   172.198.208.8       1
        67.0.48.5  255.255.255.255    172.198.208.8   172.198.208.8       1
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
    172.198.208.8  255.255.255.255        127.0.0.1       127.0.0.1       50
  172.198.255.255  255.255.255.255    172.198.208.8   172.198.208.8       50
      192.168.0.0    255.255.255.0      192.168.0.1     192.168.0.1       20
      192.168.0.1  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255      192.168.0.1     192.168.0.1       20
        224.0.0.0        240.0.0.0      192.168.0.1     192.168.0.1       20
        224.0.0.0        240.0.0.0    172.198.208.8   172.198.208.8       1
  255.255.255.255  255.255.255.255    172.198.208.8   172.198.208.8       1
  255.255.255.255  255.255.255.255      192.168.0.1     192.168.0.1       1
Default Gateway:     172.198.208.8
===========================================================================
Persistent Routes:
  None

KingTiger

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=KingTiger]ya the file sharing / Network Neighborhood (sorry dont know much about netwroks) and they a connected with a crossover cable (not a router)
___________Ubuntu info__________________
$ ifconfig
eth0
       link encap: ethernet hwaddr00:0c:41:22:d4:4e
inet6 addr: fe80::20c:41ff:fe22:d44e164 scope:link
up broadcast running multicast mtu:1500 metric:1
RX packets:0 errors:0 droped:0 overruns:0 frame:0
TX packets:0 errors:0 overruns:0 carrier:0
collisions:0  TXqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
interrupt:9 Base address:0xe800

LO  
      link encap:local loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet addr: ::1/128 acope:host
up loopback running mtu:16436 metric:1
RX packets:15334 errors:0 dropped:0 overruns:0 frame:0
TX packets:15334 errors:0 dropped:0overruns:0 carrier:0
collisions:0 TXqueuelen:0
RX bytes:888756 (867.9eib) TX bytes:888756 (867.9kib)

$route
        kernell ip routing table
destination gateway genmask flags metric ref use iface


____________windows info______________
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 3:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

PPP adapter Netscape:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 172.198.208.8
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 172.198.208.8

C:\>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 00 e8 97 03 40 ...... HP EN1207D-TX PCI 10/100 Fast Ethernet Adapter -
 Packet Scheduler Miniport
0x20004 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    172.198.208.8   172.198.208.8       1
        67.0.48.5  255.255.255.255    172.198.208.8   172.198.208.8       1
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
    172.198.208.8  255.255.255.255        127.0.0.1       127.0.0.1       50
  172.198.255.255  255.255.255.255    172.198.208.8   172.198.208.8       50
      192.168.0.0    255.255.255.0      192.168.0.1     192.168.0.1       20
      192.168.0.1  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255      192.168.0.1     192.168.0.1       20
        224.0.0.0        240.0.0.0      192.168.0.1     192.168.0.1       20
        224.0.0.0        240.0.0.0    172.198.208.8   172.198.208.8       1
  255.255.255.255  255.255.255.255    172.198.208.8   172.198.208.8       1
  255.255.255.255  255.255.255.255      192.168.0.1     192.168.0.1       1
Default Gateway:     172.198.208.8
===========================================================================
Persistent Routes:
  None

KingTiger[/QUOTE]

OK, I will explain to you what that stuff means.

The Ubuntu "ifconfig" command tells me that your network card for Ubuntu hasn't been assigned an IP address.  Normally, the output will look something like this:
```

eth0      Link encap:Ethernet  HWaddr 00:07:E9:56:1C:AD  
          **inet addr:192.168.0.2**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe56:1cad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:59874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79294678 (75.6 MiB)  TX bytes:4801637 (4.5 MiB)

```
The part I put in bold shows where the IP address was assigned.  The easiest thing to do, I think, is to give it a static IP address like this:
```

$ sudo ifconfig eth0 192.168.0.2

```

On Windows, the "ipconfig" command shows your 2 network connections.  The first, "Ethernet adapter Local Area Connection 3", is the ethernet card connected via crossover cable to the Ubuntu machine.  This card has already been assigned IP address 192.168.0.1/255.255.255.0.  We want Ubuntu to use this card as it's gateway or default route.  So on Ubuntu, use this command:
```

$ sudo route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1

```
At this point, you should be able to ping XP from Ubuntu and visa versa.
```

$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.043 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.043 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.040/0.042/0.043/0.001 ms

```

Now to share the Internet, you have to use Internet Connection Sharing on XP, or you can use a program like this one:
[http://www.analogx.com/contents/download/network/proxy.htm]("http://www.analogx.com/contents/download/network/proxy.htm")

File sharing is half-way done at this point.  If you share a folder on XP, you can reach it from Ubuntu by opening Nautilus and entering "SMB://192.168.0.1/<foldername>" in the URL (replace <foldername with the name of the shared folder>.

To do the connection the other way, you need to install the samba package on Ubuntu and then configure the permissions.

All these tasks require lengthy explanations, so if you need further help, just keep asking questions.

---

### Post by KingTiger on 2006-01-08
i still cant ping XP from Ubuntu and visa versa
what now?

KingTiger

---

### Post by blair on 2006-01-08
There are several completely different issues here. Don't confuse them.

1. If you want the Ubuntu PC to pick up an Internet connection that is only available via your Windows box, you need to enable Windows Internet connection sharing (ICS) in Windows and there needs to be a physical network connection between the two boxes. But I would ask why could you possibly need this. This is principally designed for a Windows on a dial up connection and you then establish a direct serial, parallel or Ethernet crossover connection from the second PC to the Windows box acting as your gateway. If the Windows box has an ethernet connection already, simply buy a $50 Linskys router/firewall/Wifi box, plug that into your network connection, plug your Windows box into that and you have 3 or more spare ports on the router for you to plug your Ubuntu box. You are creating unnecessary pain for yourself if you are using ICS. Unless you are really one of those one in a million folks on dial. Even there, you could just move dial line between PCs as needed or buy a $1 phone line splitter at Radio Shack. Bottom line: If you are asking about ICS, you are probably trying to do something you really shouldn't need to be doing. 

2. If you want the Ubuntu box to be able to "see" XP box, you need to enable Samba on the Ubuntu box and configure that per the advice of others above.  You also need to configure the XP box to share files, printers, etc. so that when the Ubuntu machine pings the Windows machine, the Windows machine responds and says "here I am"

3. If you want the XP box to see the Ubuntu box, you need to do do the same thing as in #2. You also need to conifigure the Ubuntu box to advertise its presence to the Windows box when the Windows box is broadcasting and looking for other peers on the LAN. Both PCs must of course be in the same Windows workgroup or it will not work. 

hope this helps.

---

### Post by KingTiger on 2006-01-08
1.I'm on dailup and i would have to buy a driver to get the modem on the ubuntu computer to work (it has the modem in devices but it cant find it in networking)

2.I have samba and winXP can see the ubuntu box in workgroup computers
but cant access it (when i click on it it says \\Fox is not accessible. you might not have permission touse this network resource. Contact the administrator of this server to find out if you have access permissions.
The network path was not found.)
 and when I ping ether computer they cant see the each other

3.they are both in the same workgroup

---

### Post by erikringmar on 2006-01-09
Hi guys,

I have queries along the same lines -- this is a great, long, answer.  I'll try implementing it tomorrow.  Thanks!

Erik

---

### Post by cwaldbieser on 2006-01-09
[QUOTE=KingTiger]1.I'm on dailup and i would have to buy a driver to get the modem on the ubuntu computer to work (it has the modem in devices but it cant find it in networking)

2.I have samba and winXP can see the ubuntu box in workgroup computers
but cant access it (when i click on it it says \\Fox is not accessible. you might not have permission touse this network resource. Contact the administrator of this server to find out if you have access permissions.
The network path was not found.)
 and when I ping ether computer they cant see the each other

3.they are both in the same workgroup[/QUOTE]

After you entered the ifconfig and route commands on Ubuntu, did the output of the commands change?  It is weird that you can actually see the Ubuntu computer from Windows if the Ubuntu computer doesn't have an IP address!

Do you get any kind of error message when you try to assign the IP address?

---

### Post by KingTiger on 2006-01-10
here is the output after i entered the commands

$ ifconfig
eth0
link encap: ethernet hwaddr00:0c:41:22:d4:4e
inet addr: 192.168.0.2 bcast: 192.168.0.255 mask:255.255.255.0
inet6 addr: fe80::20c:41ff:fe22:d44e/64 scope:link
up broadcast running multicast mtu:1500 metric:1
RX packets:0 errors:0 droped:488 overruns:0 frame:0
TX packets:0 errors:92 overruns:0 carrier:0
collisions:0 TXqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
interrupt:9 Base address:0xe800

LO
link encap:local loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet addr: ::1/128 acope:host
up loopback running mtu:16436 metric:1
RX packets:15334 errors:0 dropped:0 overruns:0 frame:0
TX packets:15334 errors:0 dropped:0overruns:0 carrier:0
collisions:0 TXqueuelen:0
RX bytes:888756 (867.9eib) TX bytes:888756 (867.9kib)

$route
kernell ip routing table
destination gateway        genmask           flags metric ref use iface
localnet      *                 255.255.255.0    u         0     0   0    eth0
default       192.168.0.1    0.0.0.0              ug      0      0   0   eth0

KingTiger

---

### Post by cwaldbieser on 2006-01-10
[QUOTE=KingTiger]here is the output after i entered the commands

$ ifconfig
eth0
link encap: ethernet hwaddr00:0c:41:22:d4:4e
inet addr: 192.168.0.2 bcast: 192.168.0.255 mask:255.255.255.0
inet6 addr: fe80::20c:41ff:fe22:d44e/64 scope:link
up broadcast running multicast mtu:1500 metric:1
RX packets:0 errors:0 droped:488 overruns:0 frame:0
TX packets:0 errors:92 overruns:0 carrier:0
collisions:0 TXqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
interrupt:9 Base address:0xe800

LO
link encap:local loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet addr: ::1/128 acope:host
up loopback running mtu:16436 metric:1
RX packets:15334 errors:0 dropped:0 overruns:0 frame:0
TX packets:15334 errors:0 dropped:0overruns:0 carrier:0
collisions:0 TXqueuelen:0
RX bytes:888756 (867.9eib) TX bytes:888756 (867.9kib)

$route
kernell ip routing table
destination gateway        genmask           flags metric ref use iface
localnet      *                 255.255.255.0    u         0     0   0    eth0
default       192.168.0.1    0.0.0.0              ug      0      0   0   eth0

KingTiger[/QUOTE]

That actually looks good.  It says your Ubuntu NIC has IP 192.168.0.2/24 (that is shorthand for saying the "192.168.0" part is the network, and the 2 represents the actual NIC).  On the Windows PC, you have a NIC with IP address 192.168.0.1/24, so they are on the same network, and should be able to communicate.    So from Windows, you should be able to:
```

C:\>ping 192.168.0.2

```
and get a response.  If you are running Firestarter or some other firewall on Ubuntu, you might need to adjust the settings to let you ping.  Likewise, you might need to adjust the Windows firewall settings to ping from Ubuntu.

If you *still* can't ping Ubuntu, try posting:
```

$ sudo iptables -nL

```
That will show us any packet filtering (firewall) rules you might have in place.

---

### Post by blair on 2006-01-10
OK. I see that you have a legimate need for ICS. Also note that the Windows machine in this setup is your router, DNS server and DHCP server. For routing and DNS, it is all done by an OS service at a higher level in software, not at the chip level, thus, performance will be relatively poor compared to a hardware router.

---

