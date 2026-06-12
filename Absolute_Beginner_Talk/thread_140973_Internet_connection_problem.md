---
title: "Internet connection problem"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by BluePhoenix on 2006-03-07
I'm trying to get my internet connection working but Ubuntu doesn't automatically detect my network settings. I can use the same computer to connect to my ADSL modem/firewall/router. In Windows the connection is set up  to a static IP (not DHCP) with the following settings:

IP address 10.140.47.240
Subnet 255.255.0.0
Gateway 10.140.0.1

I've tried these setting with eth0 but without any luck.

Thanks,
Alex

---

### Post by LordBug on 2006-03-07
Can you provide the output of "ifconfig" for us to look at?

---

### Post by BluePhoenix on 2006-03-08
**[COLOR="Red"]ifconfig output:[/COLOR]**

eth0      Link encap:Ethernet  HWaddr 00:11:09:30:59:2A  
          inet addr:10.140.47.240  Bcast:10.255.255.255  Mask:255.255.0.0
          inet6 addr: fe80::211:9ff:fe30:592a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9083 (8.8 KiB)  TX bytes:9113 (8.8 KiB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:220801 (215.6 KiB)  TX bytes:220801 (215.6 KiB)

---

### Post by Jucato on 2006-03-08
have you tried to run ```
sudo pppoeconf
```?

---

### Post by mips on 2006-03-08
1. What **brand & model** router do you have ?
2. Post output of Windows **ipconfig /all** command here.
3. Post contents of Linux **/etc/networking/interfaces** file here.

---

### Post by jamesr on 2006-03-08
Can you ping anything. Try in sequence

```
ping 10.140.47.240
ping 10.140.0.1
ping www.google.com
 
cntrl C to stop ping

```

---

### Post by BluePhoenix on 2006-03-09
**[COLOR="Red"]_Here is everything requested in one go:_[/COLOR]**

**[COLOR="Red"]Network Interfaces[/COLOR]**

[I]alexis@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet static
address 10.140.47.240
netmask 255.255.0.0
gateway 10.140.0.1

auto eth0

iface dsl-provider inet ppp
provider dsl-provider[/I]

**[COLOR="Red"]Windows IPCONFIG[/COLOR]**
[I]
Windows IP Configuration

        Host Name . . . . . . . . . . . . : homedesktop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : cyta.adsl

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : cyta.adsl
        Description . . . . . . . . . . . : NVIDIA nForce MCP Networking Controller
        Physical Address. . . . . . . . . : 00-11-09-30-59-2A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.140.47.240
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . : 10.140.0.1
        DHCP Server . . . . . . . . . . . : 10.140.0.1
        DNS Servers . . . . . . . . . . . : 192.168.5.102
                                            192.168.5.101
        Lease Obtained. . . . . . . . . . : 08 March 2006 21:24:59

        Lease Expires . . . . . . . . . . : 15 March 2006 07:33:30
[/I]

**[COLOR="Red"]Ping Results[/COLOR]**
                                                                               
[I]               
alexis@ubuntu:~$ ping 10.140.0.1
PING 10.140.0.1 (10.140.0.1) 56(84) bytes of data.
From 10.140.0.1 icmp_seq=1 Packet filtered
From 10.140.0.1 icmp_seq=2 Packet filtered
From 10.140.0.1 icmp_seq=3 Packet filtered
From 10.140.0.1 icmp_seq=4 Packet filtered
From 10.140.0.1 icmp_seq=5 Packet filtered
From 10.140.0.1 icmp_seq=6 Packet filtered
From 10.140.0.1 icmp_seq=7 Packet filtered
From 10.140.0.1 icmp_seq=8 Packet filtered
From 10.140.0.1 icmp_seq=9 Packet filtered
From 10.140.0.1 icmp_seq=10 Packet filtered

--- 10.140.0.1 ping statistics ---
10 packets transmitted, 0 received, +10 errors, 100% packet loss, time 9009ms

alexis@ubuntu:~$ ping 10.140.47.240
PING 10.140.47.240 (10.140.47.240) 56(84) bytes of data.
64 bytes from 10.140.47.240: icmp_seq=1 ttl=64 time=0.048 ms
64 bytes from 10.140.47.240: icmp_seq=2 ttl=64 time=0.053 ms
64 bytes from 10.140.47.240: icmp_seq=3 ttl=64 time=0.053 ms
64 bytes from 10.140.47.240: icmp_seq=4 ttl=64 time=0.053 ms
64 bytes from 10.140.47.240: icmp_seq=5 ttl=64 time=0.053 ms
64 bytes from 10.140.47.240: icmp_seq=6 ttl=64 time=0.042 ms
64 bytes from 10.140.47.240: icmp_seq=7 ttl=64 time=0.054 ms
64 bytes from 10.140.47.240: icmp_seq=8 ttl=64 time=0.053 ms
64 bytes from 10.140.47.240: icmp_seq=9 ttl=64 time=0.053 ms
64 bytes from 10.140.47.240: icmp_seq=10 ttl=64 time=0.050 ms

--- 10.140.47.240 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8998ms
rtt min/avg/max/mdev = 0.042/0.051/0.054/0.005 ms
alexis@ubuntu:~$ ping [http://www.google.com](http://www.google.com)
ping: unknown host [http://www.google.com](http://www.google.com)
alexis@ubuntu:~$[/I]

---

### Post by BluePhoenix on 2006-03-09
My modem/router/firewall was installed by my ISP provider. I  can't change any settings on it even though I would like to because it has wireless and I could use that for my laptop. It's a ECI B-FOCUS Router 352+. I managed to find a manual on the net but its in Hebrew!

---

### Post by BluePhoenix on 2006-03-09
A few more things I forgot to mention:

I also noticed that WinXP is configured using DHCP. I also tried this in Ubuntu without any luck. Also the *pppoeconf * utilty was not successful.

---

### Post by mips on 2006-03-09
Try turning off IPv6 and manually configure your DNS servers.

---

### Post by BluePhoenix on 2006-03-09
Yay... it now works. I added the DNS servers manually and now I can surf! In fact I'm posting from within Ubuntu right now. 

Thanks for your help everyone especially mips for pin-pointing the problem!

---

