---
title: "Another Networking Problem in Gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by NZ-Wanderer on 2007-10-23
Hi there
I seem to have developed a little problem with Gutsy which I cannot seem to solve...

My main machine dual boots Gutsy and Vista Ultimate (with VMware in Gutsy having a XP install)
My second machine boots Vista Ultimate
My third machine boots XP Professional

When all 3 computers are running windows I have no problem seeing/reading/writing to them..
When main computer is in Gutsy, the windows computers can't see it at all, and I cannot see the windows computers in Gutsy.
I also cannot see Gutsy from within my VMWare server running in Gutsy (XP installed in there)

All computers connect to a 5 port Gigabit Ethernet switch which in turn connects to a Router.
The Network card in my main machine is a Nvidia nforce 500 SLI MCP builtin Gigabit MAC with external Attansic PHY (I read that from motherboard box)

I have configured the smb password in terminal (that's about the extent of my knowledge)

Any help please???

---

### Post by wieman01 on 2007-10-23
Have you tried this guide?

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto")

It's the best guide I have seen so far for SAMBA. Follow it down to the letter, it should work for Vista as well.

All computers can browse the web, etc., right?

---

### Post by NZ-Wanderer on 2007-10-23
> **wieman01 said:**
> Have you tried this guide?
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto")
It's the best guide I have seen so far for SAMBA. Follow it down to the letter, it should work for Vista as well.
All computers can browse the web, etc., right?

*** Hang head in shame *** - No I hadn't tried that, never had any problems with it before...

Yes, all computers connect to the Internet with no problems at all (including the xp install inside Gutsy)

I ran the commands you put in the other thread by the way, and here is the result of them if it is of any use:

```
simplicity@Kubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.241.0    *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.111.0   *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.2     0.0.0.0         UG    0      0        0 eth0
simplicity@Kubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.241.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.111.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth0
simplicity@Kubuntu:~$ sudo ifdown -v eth0
[sudo] password for simplicity:
ifdown: interface eth0 not configured
simplicity@Kubuntu:~$ sudo ifup -v eth0
Ignoring unknown interface eth0=eth0.
simplicity@Kubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:AE:58:E0
          inet addr:192.168.1.13  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:feae:58e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1725481 (1.6 MB)  TX bytes:657694 (642.2 KB)
          Interrupt:18 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.241.1  Bcast:172.16.241.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.111.1  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

simplicity@Kubuntu:~$

```

---

### Post by wieman01 on 2007-10-23
Ah... Kubuntu. Nice. :-)

So it's no networking problem but has rather to do with SAMBA. Why don't you check out that guide first and post here or over there if you have encounter problems? As said, the guide is pretty good and apparently works for Vista users as well.

---

### Post by NZ-Wanderer on 2007-10-23
> **wieman01 said:**
> Ah... Kubuntu. Nice. :-)
So it's no networking problem but has rather to do with SAMBA. Why don't you check out that guide first and post here or over there if you have encounter problems? As said, the guide is pretty good and apparently works for Vista users as well.

Thank you, am heading over there now :) :)

---

### Post by wieman01 on 2007-10-23
No problem. I have subscribed to that thread, so I will notice if you post over there.

---

### Post by NZ-Wanderer on 2007-10-23
> **wieman01 said:**
> Ah... Kubuntu. Nice. :-)
So it's no networking problem but has rather to do with SAMBA. Why don't you check out that guide first and post here or over there if you have encounter problems? As said, the guide is pretty good and apparently works for Vista users as well.

Thanks, I went through "most" of that tutorial (couldn't do the static IP part), and let Kubuntu put in my shares rather than type them in by hand :)

It Worked, didn't seem to for a start, but a little rebooting on all machines and they slowly started working, so all is well in my Kubuntu land :) :) - I can even now read and write to my vmware XP in Gutsy :)

Thanks very much for taking the time to help :)

---

### Post by wieman01 on 2007-10-24
> **NZ-Wanderer said:**
> Thanks, I went through "most" of that tutorial (couldn't do the static IP part), and let Kubuntu put in my shares rather than type them in by hand :)

It Worked, didn't seem to for a start, but a little rebooting on all machines and they slowly started working, so all is well in my Kubuntu land :) :) - I can even now read and write to my vmware XP in Gutsy :)

Thanks very much for taking the time to help :)
Excellent. As I said, it's the best tutorial I know. Has worked for a great deal of people including myself. See you around.

---

