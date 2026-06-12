---
title: "Implementing 6 to 4 tunneling"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-06-07
i wanna enter the world of ipv6. Surfing the inet ive discovered the router advertisement daemon (radvd) script to finally implement it. Here it is:

#/etc/radvd.conf
interface eth0
{
        AdvSendAdvert on;
        MinRtrAdvInterval 3;
        MaxRtrAdvInterval 10;
        AdvHomeAgentFlag off;
        prefix 2002:c9ea:97c9:cafe::/64
        {
                AdvOnLink on;
                AdvAutonomous on;
                AdvRouterAddr off;
                Base6to4Interface eth1;
        };
};

When i execute this scipt as ./ipv6-setup6to4.sh   |sudo sh -x the following error pops up:

"Error: an inet prefix is expected rather than "2002:c9ea:97c9:201.234.151.201"

The problem is that everytime i make a ping6 the host is unreachable. Also, in my LAN the hosts receive only local ipv6 addresses (fe80) and not global ones. Here is the ifconfig of the machine that plays the router role:

eth0      Link encap:Ethernet  HWaddr 00:40:F4:EA:F6:FD  
          inet addr:201.234.151.201  Bcast:201.234.151.223  Mask:255.255.255.224
          inet6 addr: fe80::240:f4ff:feea:f6fd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1888216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:54943 txqueuelen:1000 
          RX bytes:505845815 (482.4 MiB)  TX bytes:223104602 (212.7 MiB)
          Interrupt:12 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:08:54:22:3B:AB  
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe22:3bab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:502319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:223237415 (212.8 MiB)  TX bytes:421964026 (402.4 MiB)
          Interrupt:10 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tun6to4   Link encap:IPv6-in-IPv4  
          inet6 addr: 2002:c9ea:97c9::1/16 Scope:Global
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:4092 (3.9 KiB)

If anyone can help me with this id really appreciate it
Regards,

---

### Post by FleetAdmiral74 on 2007-06-07
Might have luck in the network forum, this is anything but Beginner Talk...

---

