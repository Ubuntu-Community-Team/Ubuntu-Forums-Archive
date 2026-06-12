---
title: "Slow application start up, interface &quot;ath0&quot; and config from network tools"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Catfish81 on 2007-03-18
Hi all,

I'm new to Ubuntu but used Linux for a few years.

I'm posting here for three reasons.
1. My Ubuntu install seems to *start* applications (and the initial desktop/WM) very slowly, and
2. I don't know what the interface "ath0" is. What is it? It appears in ifconfig's output and also in the Network Tools program.
3. I can't modify anything via the Network Tools program. I select an interface and press "Configure" button but it says "You are not allowed to access the system configuration". I'm an admin user and can sudo and stuff when it asks for a password but wontwork here.


In relation to point 1. I have already edited my /etc/hosts file as discussed on these forums already. Ive tried disabling ipv6 as discussed here too. None of these have fixed the problem. I could really go for a fix on this because its painful starting things up and they take a minute to load.

---

### Post by apjone on 2007-03-18
what version of ubuntu do you run? ath0 maybe wireless. post your /etc/network/interfaces (hide any ip's that may be confidential)
What is the spec of your machine, cpu, ram etc. 

Post the above and i will get back to you

---

### Post by Catfish81 on 2007-03-19
hi apjone,

pc specs:
amd XP 2700+ cpu
1Gb DDRAM
onboard NIC
PCI Netgear Wireless NIC (not sure on model can get if required)
Radeon 9800 Pro
3 IDE HDDs, using cable select (maybe this could interfere with slowing things down?)

I'm using Ubuntu 6.10. Here's what uname -a puts out:
> Linux delta 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Here's the interfaces file:

> catfish@delta:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.81
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid Catfish
wireless-key s: ***blanked***

auto wlan0
iface wlan0 inet dhcp


I went into System -> Admin -> Networking last night and changed my wireless settings in there but I don't even use wlan. I just run ethernet. I was just interested to see how Ubuntu goes with wireless networking. I see that ath0 is the wireless interface now. But why does ifconfig output this:

> catfish@delta:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:09:5B:E8:F6:B8  
          inet6 addr: fe80::209:5bff:fee8:f6b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:11:2F:08:93:68  
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe08:9368/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18175150 (17.3 MiB)  TX bytes:3062051 (2.9 MiB)
          Interrupt:185 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-E8-F6-B8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196880 errors:0 dropped:0 overruns:0 frame:13416
          TX packets:793371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:16251035 (15.4 MiB)  TX bytes:39059638 (37.2 MiB)
          Interrupt:209 Memory:f8b20000-f8b30000 



Now my question is what is interface wifi0 ??! As I can see it is actually sending and recieving stuff!
EDIT: looks like ath0 and wifi0 are both the wireless connection. But why are there two interfaces for the one connection?

---

