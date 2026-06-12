---
title: "Wireless suddenly broken"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by matthew_petty on 2007-10-07
Hey guys -

I've had nothing but a great experience putting Feisty on my HP DV9000 laptop. Wireless was working great yesterday, but after a reboot it stopped. I'm running right now off of a live CD, so I know there isn't a hardware issue.

I'm using a restricted driver: Intel(R) PRO/Wireless 3945 Network Connected Driver for Linux

I set up some things to share my wireless connection through my wired connection. I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Using iwlist, I can see the access point that I had been connecting to, and I still have a good signal. Even if I manually select the ESSID and choose DHCP, none of my packets are making it through...

Please help!

---

### Post by Beggar on 2007-10-07
Are you gettings and IP address from the router?

```
ifconfig
```

---

### Post by matthew_petty on 2007-10-07
Nope...

I did have it temporarily working by restarting /etc/init.d/dnsmasq and reconfiguring ipmasq, but I rebooted again and I'm back to square one, because that isn't working this time.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1B:24:34:8F:6C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x5000 Memory:da000000-da020000 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:D3:98:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:135 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 Memory:d8000000-d8000fff 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:24:34:8F:6C  
          inet addr:169.254.5.88  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x5000 Memory:da000000-da020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

iwconfig
```
eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:135   Missed beacon:0

```

iwlist
```

eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:81:4C:46
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=40/100  Signal level=-85 dBm  Noise level=-85 dBm
                    Extra: Last beacon: 96ms ago
          Cell 02 - Address: 00:0F:B5:1B:46:5E
                    ESSID:"Daedelus"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=37/100  Signal level=-87 dBm  Noise level=-87 dBm
                    Extra: Last beacon: 1004ms ago

```

---

### Post by matthew_petty on 2007-10-07
Well, I manually set my IP address, netmask, gateway, and DNS servers. Now, I can resolve hostnames but nothing is making it through. When I ping, I get a sendmsg error "Operation is not allowed." 

Does ipmasq and its firewall stuff have something to do with it?

ipmasq -d
```
#: Interfaces found:
-e #:   eth1	192.168.1.25/255.255.255.0
#: Turn off forwarding for 2.1 kernels
#: Disable automatic IP defragmentation
echo "0" > /proc/sys/net/ipv4/ip_forward
#: Flush all and set default policy of deny.
/sbin/iptables -P INPUT DROP
/sbin/iptables -P OUTPUT DROP
/sbin/iptables -P FORWARD DROP
/sbin/iptables -F INPUT
/sbin/iptables -F OUTPUT
/sbin/iptables -F FORWARD
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -F PREROUTING
/sbin/iptables -t mangle -F OUTPUT
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
/sbin/iptables -t nat -F PREROUTING
/sbin/iptables -t nat -F POSTROUTING
/sbin/iptables -t nat -F OUTPUT
#:
#: **********************************************************
#: ***                   CUSTOM CHAINS                    ***
#: **********************************************************
#:
#:
#: **********************************************************
#: ***                   FORWARD CHAIN                    ***
#: **********************************************************
#:
#: Forward packets among internal networks
#:
#: **********************************************************
#: ***                    INPUT CHAIN                     ***
#: **********************************************************
#:
#: Accept all packets coming in from the loopback interface
/sbin/iptables -A INPUT -j ACCEPT -i lo
#: Deny and log all packets trying to come in from a 127.0.0.0/8 address
#: over a non-'lo' interface
/sbin/iptables -A INPUT -j LOG -i ! lo -s 127.0.0.1/255.0.0.0
/sbin/iptables -A INPUT -j DROP -i ! lo -s 127.0.0.1/255.0.0.0
#: Accept dumb broadcast packets on internal interfaces
/sbin/iptables -A INPUT -j ACCEPT -i eth1 -d 255.255.255.255/32
#: Accept packets from internal networks on internal interfaces
/sbin/iptables -A INPUT -j ACCEPT -i eth1 -s 192.168.1.25/255.255.255.0
#: Accept multicast packets (adresses 224.0.0.0) from internal interfaces
/sbin/iptables -A INPUT -j ACCEPT -i eth1 -d 224.0.0.0/4 -p ! 6
#: Disallow and log packets trying to come in over external interfaces
#: from hosts claiming to be internal
#: Accept dumb broadcast packets on external interfaces
#: Accept incoming packets from external networks on external interfaces
#:
#: **********************************************************
#: ***                  IP MASQUERADING                   ***
#: **********************************************************
#:
#: Masquerade packets from internal networks
#:
#: **********************************************************
#: ***                    OUTPUT CHAIN                    ***
#: **********************************************************
#:
#: Allow packets to go out over the loopback interface
/sbin/iptables -A OUTPUT -j ACCEPT -o lo
#: Allow dumb broadcast packets to leave on internal interfaces
/sbin/iptables -A OUTPUT -j ACCEPT -o eth1 -d 255.255.255.255/32
#: Allow packets for internal hosts to be delivered using internal interfaces
/sbin/iptables -A OUTPUT -j ACCEPT -o eth1 -d 192.168.1.25/255.255.255.0
#: Allow multicast packets (adresses 224.0.0.0) to be delivered using
#: internal interfaces
/sbin/iptables -A OUTPUT -j ACCEPT -o eth1 -d 224.0.0.0/4 -p ! 6
#: Deny and log packets attempting to leave over external interfaces claiming
#: to be for internal networks
#: Allow dumb broadcast packets to leave on external interfaces
#: Allow packets for external networks leave over external interfaces
#:
#: **********************************************************
#: ***                      SERVICES                      ***
#: **********************************************************
#:
#: Turn on forwarding for 2.1 kernels
#: Enable automatic IP defragmentation
echo "1" > /proc/sys/net/ipv4/ip_forward
#: Set masqerading timeouts:
#:   2 hrs for TCP
#:   10 sec for TCP after FIN has been sent
#:   160 sec for UDP (important for ICQ users)
#: Run the deprecated /etc/ipmasq.rules, if present
#: Deny but do not log outside IGMP traffic.
/sbin/iptables -A INPUT -j DROP -d 224.0.0.1
/sbin/iptables -A OUTPUT -j DROP -d 224.0.0.1
/sbin/iptables -A FORWARD -j DROP -d 224.0.0.1
#: Deny and log anything that may have snuck past any of our other rules
/sbin/iptables -A INPUT -j LOG -s 0.0.0.0/0 -d 0.0.0.0/0
/sbin/iptables -A INPUT -j DROP -s 0.0.0.0/0 -d 0.0.0.0/0
/sbin/iptables -A OUTPUT -j LOG -s 0.0.0.0/0 -d 0.0.0.0/0
/sbin/iptables -A OUTPUT -j DROP -s 0.0.0.0/0 -d 0.0.0.0/0
/sbin/iptables -A FORWARD -j LOG -s 0.0.0.0/0 -d 0.0.0.0/0
/sbin/iptables -A FORWARD -j DROP -s 0.0.0.0/0 -d 0.0.0.0/0

```

---

