---
title: "Cannot connect to the internet"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-10-26
I´m fed up with this. Its been 6 months since i first tried to access directly to the internet (without a server) and everything i got was nothing but headaches. It seems like its a speed problem, like my ISP works at 10 mbps and in Ubuntu they are installed to work by default at 100 mbps. Ive tried mii-tool and ethtool but got no luck. Let´s see if someone here can help me out:

/etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 190.15.199.211
netmask 255.255.255.0
gateway 190.15.199.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:11:2F:B6:28:F6
          inet addr:190.15.199.211  Bcast:190.15.199.255 Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:420 (420.0 b)  TX bytes:42 (42.0 b)
          Interrupt:209 Base address:0x8800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1880 (1.8 KiB)  TX bytes:1880 (1.8 KiB)

```

lspci:

```

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

resolv.conf:

```

nameserver 190.15.222.2
nameserver 190.15.221.2

```

Thanks in advance

---

### Post by ferpadro on 2007-10-26
Ok, i figured out something. I executed "sudo ethtool eth0" and threw this:

```

fernando@Athena:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: no

```

It seems the problem is with no detecting the link. How can i change that?

---

### Post by rudeboyskunk on 2007-10-27
I had a very very similar problem about a year ago.  Turned out the ethernet card sucked and I had to get a new one.  Would work for like 5 minutes (tops) and then crap out.

---

### Post by ferpadro on 2007-10-27
Thats not an excuse for me. This network card works ok on windows and when running behind a server in Ubuntu. So afterall i assume its not the card´s fault. How come Ubuntu users has not asked the Ubuntu devs to include a GUI to change network media speed? It is a must-need feature

---

### Post by Threbus5 on 2007-10-27
Your /etc/network/interfaces: lists five interfaces. Are you using them all?

Sometimes Debian based Linux grabs a default route other than just the active one that you Think it should. For example, one of the auto dhcp interfaces might actually have assumed the role of default.  

The ifconfig , without an ifconfig -a (I believe) will only show the active interfaces - with the potential that one of the DHCPs is still the default.

Option "A"  try a netstat -r to obtain the default route and see if it uses the eth0. If it does not, delete the route and make one that includes eth0 as the default.

Option "B":  disable all interfaces except eth0 and restart the machine.

I have only two interfaces in my laptop. They both use the same static address. In order to use one I disable the other.

Take care.

---

### Post by ferpadro on 2007-10-27
Yeah, sorry, my fault. I forgot to paste my updated /etc/network/interfaces. Here it is:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 190.15.199.211
netmask 255.255.255.0
gateway 190.15.199.1

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

```

I did a netstat -r and it threw me this (along with a ip route i executed after that):

```

root@Athena:/home/fernando# netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth1
190.15.199.0    *               255.255.255.0   U         0 0          0 eth0

root@Athena:/home/fernando# ip ro
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.1
190.15.199.0/24 dev eth0  proto kernel  scope link  src 190.15.199.211
default via 190.15.199.1 dev eth0

```

I dont see any mistake here. I still think it is a media speed problem, coz if i execute "ethtool eth0" repeteadly it says "link up","link down","link up","link down" and so on, like it happened to me in windows when i put other speed than 10 base T

---

