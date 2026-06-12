---
title: "Newbie with network problems"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by homerhendrix on 2007-12-16
Hello, I just installed Ubuntu for the first time.  The desktop that I installed it from previously had windows xp running through DHCP and it worked fine.  Ubuntu also connected through ethernet does not seem to seem to work though.  I can ping my router, but when I try to go to a webpage it gets stuck at the waiting for [www.google.com](www.google.com).  I've done fairly extensive searching for an issue like mine but so far have been unable to find a solution.  I'll give an exhaustive rundown on exactly what is happening:

The ubuntu box is set up under network settings for DHCP, and under the DNS tab I've got it set to the same DNS of every other box (192.168.0.1)

My router is a Linksys WRT300N, and along with the desktop and PS3 connected through ethernet it has two windows xp laptops that are wirelessly connected.  Here is ipconfig /all copy and pasted from one of the wireless laptops:
Windows IP Configuration

        Host Name . . . . . . . . . . . . : Lifebook
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-0B-5D-9E-27-E8

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Atheros AR5006X Wireless Network Ada
pter
        Physical Address. . . . . . . . . : 00-11-F5-86-1F-08
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Sunday, December 16, 2007 11:09:20 A
M
        Lease Expires . . . . . . . . . . : Monday, December 17, 2007 11:09:20 A
M


Going to terminal I can ping my router fine (192.168.1.1)
Again in the terminal I can ping the DNS fine (192.168.0.1)

Here is the ifconfig from the Ubuntu box

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:D8:B0:14:DA  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feb0:14da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9665 (9.4 KB)  TX bytes:8944 (8.7 KB)
          Interrupt:22 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Here is the route -n
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

Here is the results of pinging [www.google.com](www.google.com)
ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.19.99) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6010ms

Here is host [www.google.com](www.google.com)
host [www.google.com](www.google.com)
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 74.125.19.99
[www.l.google.com](www.l.google.com) has address 74.125.19.104
[www.l.google.com](www.l.google.com) has address 74.125.19.103
[www.l.google.com](www.l.google.com) has address 74.125.19.147

Copy and paste from running iptables
iptables -L -v
WARNING: Error inserting x_tables (/lib/modules/2.6.22-14-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
FATAL: Error inserting ip_tables (/lib/modules/2.6.22-14-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.


And another copy and pasted command
sudo cp /etc/network/interfaces/etc/network/interfaces.back
[sudo] password for mike:
cp: missing destination file operand after `/etc/network/interfaces/etc/network/interfaces.back'
Try `cp --help' for more information.


These seem to be the types of troubleshooting that problems similar to mine went through.  Please do not assume I know anything about Ubuntu or linux as a whole and walk me through any steps (I tried to disable ipv6 but could not without root access whatever that means).

Thanks for any and all help!  Sorry if I've overloaded with information.

---

### Post by HermanAB on 2007-12-16
OK, you got an IP address and your ethernet adaptor works, but the DHCP setup on the router may be a little incomplete.

To go online, you need a couple things more:
a. DNS IP addresses
b. Default route

Verify the DNS settings:
$ sudo cat /etc/resolv.conf

It should have the same DNS information as in Windows when you do:
c:\> ipconfig /all

If necessary edit the resolv.conf file with gedit so it looks like:
$ sudo gedit /etc/resolv.conf
nameserver w.x.y.z
nameserver w.x.y.z

The next thing to test is the routing table:
$ sudo route
(long wait)

It should show a default gateway (UG) for 192.168.1.0 (your router subnet).

If not, add a default route:
$ sudo route add default gw 192.168.1.1 eth0

Your internet connection should now work.

---

Looking at the info you supplied, it seems that the router DNS setting is bad, therefore DHCP will dish out a bad DNS address.  I presume that the Windows PC has its DNS setting overridden (to ignore the DHCP) and set to the DNS of your ISP.  You have to fix the router.

Cheers,

Herman

---

### Post by homerhendrix on 2007-12-16
Herman

Thanks so much for your help!  I don't entirely understand how you wanted me to edit the files, but I'll copy and paste the results from the two commands you gave me, and if you have the time and patience maybe you can walk me through exactly how to change what.  

The first command:

$sudo cat /etc/resolv.conf
domain WORKGROUP
nameserver 192.168.0.1


And the second command you gave me:

$sudo route
Kernel IP routing table
Destination     Gateway         Genmask              Flags Metric Ref    Use Iface
192.168.1.0    *                     255.255.255.0    U        0        0        0 eth0
link-local           *                     255.255.0.0        U       1000   0        0 eth0
default             192.168.1.1    0.0.0.0               UG     100     0        0 eth0

Thanks again for your help!

---

