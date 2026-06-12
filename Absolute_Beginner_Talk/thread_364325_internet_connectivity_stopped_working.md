---
title: "internet connectivity stopped working"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by ctokar on 2007-02-18
Hello,
This is my situation. My ISP recently gave me a static ip address. Previously, both my xp and kubuntu partitions were able to connect and browse the internet. Now, only XP is able to, not kubuntu.

on XP, which works fine when I ipconfig /all:
-----------------------------------------------------------------------------------------
Windows IP Configuration

        Host Name . . . . . . . . . . . . : chris-e92d23733
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : classcom.pl

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Network
 Connection
        Physical Address. . . . . . . . . : 00-13-CE-C3-EE-F6

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : classcom.pl
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-14-22-E4-78-57
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 195.150.76.36
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 172.27.45.1
        DHCP Server . . . . . . . . . . . : 192.168.240.254
        DNS Servers . . . . . . . . . . . : 172.27.45.1
                                            195.150.77.18
        Lease Obtained. . . . . . . . . . : Sunday, February 18, 2007 9:08:12 AM

        Lease Expires . . . . . . . . . . : Sunday, February 18, 2007 3:08:12 PM

-----------------------------------------------------------------------------------------

I went into the kubuntu network gui and and tried every possible configuration if manual/dhcp, netmask, gateway to  no avail. I cannot ping, but somehow my dns servers are being populated in the gui.

Is there an obvious problem I am missing? Why did windows work right away when my isp flipped the switch to give me the static ip and kubuntu didn't?

Thanks

---

### Post by energiya on 2007-02-18
What does
```

ifconfig

```
say ?

---

### Post by ctokar on 2007-02-18
ifconfig says:

eth0      Link encap:Ethernet  HWaddr 00:14:22:E4:78:57
          inet addr:195.150.76.36  Bcast:195.150.76.255  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20307 (19.8 KiB)  TX bytes:0 (0.0 b)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Topsiho on 2007-02-18
This is my result with ifconfig:

jaap@Bromo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:FC:2B:87:E9
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe2b:87e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12731475 (12.1 MiB)  TX bytes:602304 (588.1 KiB)
          Interrupt:169 Base address:0x8f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

The subnetmask is 255.255.255.0, which means the first three numbers identify the net, and the last one the computer on that net.
Your mask is 255.255.255.255, which means that all 4 numbers identify the net, and there is no number that identify your computer.
Strange thing is that in Windows your configuration does seem to work.

Good luck,

Topsiho

---

