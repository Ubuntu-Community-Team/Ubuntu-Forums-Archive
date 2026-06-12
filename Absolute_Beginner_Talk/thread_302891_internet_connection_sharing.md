---
title: "internet connection sharing?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by darkenedday on 2006-11-19
So, I'm not quite as new to linux as some but I am still by FAR a noob, I have one pc with 5 network cards in it, I would like to use this as a router as I have heard some have set up, with internet connection sharing, this would also act as a server (already does just no internet from the crossover cables to my pc) I REFUSE to put windows back on here so I've been working for 3 days on trying to get this to work, Firestarter lets you bridge the connection but only with one card, and I really can't even get that to work, I have to connect to two pc's and an xbox, please help me out here

thanks in advance!

---

### Post by Peter76 on 2006-11-19
Hi, I have done this using a package called ipmasq; it's in universe. I recall that after Dapper you had to to dpkg-reconfigure ipmasq to get it to work properly... For the rest; it just did the job! Have a look, and post back if it works, or you have other troubles

---

### Post by darkenedday on 2006-11-19
ok, so I tried ipmasq, and when I did dpkg-reconfigure it only asks alot of ppp related questions, I'm running a LAN not dial-up (i think that's what ppp is) so now I'm totally lost, and another thing I realised that I didn't think should be happening, when I connect another box to this one with crossover cable the lights come on on the network cards, and tey are enabled on both boxes however I can't so much as access this one (the one with loads of shared files) as a server, let alone get internet connection sharing to work, I'm lost, I apologise for being such a noob, but I have no idea what i'm doing here, help please :-)

THANKS!

---

### Post by Peter76 on 2006-11-19
ok, can you post the output from ifconfig here? And are you running a dhcp server ( if not, wait with that:-)

---

### Post by darkenedday on 2006-11-19
eth0      Link encap:Ethernet  HWaddr 00:10:4B:87:FA:96
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:10:5A:D0:D8:40
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fed0:d840/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:268263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:300384785 (286.4 MiB)  TX bytes:44221713 (42.1 MiB)
          Interrupt:12 Base address:0xc000

eth2      Link encap:Ethernet  HWaddr 00:10:5A:D1:2D:AC
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fed1:2dac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22410 (21.8 KiB)  TX bytes:192871 (188.3 KiB)
          Interrupt:11 Base address:0xe000

eth3      Link encap:Ethernet  HWaddr 00:40:F4:CC:E9:FB
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fecc:e9fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:14281 (13.9 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:405285 (395.7 KiB)  TX bytes:405285 (395.7 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.77.1  Bcast:192.168.77.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.39.1  Bcast:172.16.39.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)




     I'm not running much of any server right now because none of it seems to work, but dhcp does seem like the best option

---

### Post by Peter76 on 2006-11-19
Ok, could you also post your /etc/network/interfaces?
( Sorry, it's a bit digging up for me as well;-)
And which network card is connected to the internet?
and what are the vmnet cards?????

---

### Post by darkenedday on 2006-11-19
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet static
address 192.168.1.113
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth3 inet static
address 192.168.1.111
netmask 255.255.255.0

auto eth3


iface br0 
bridge_ports all



it's not a problem I deeply appreciate the help, just ignore the vmnet cards they're simply for VMware virtual machine, i have windows vista beta 2 running in one (it blows btw, worse than ME even)

---

### Post by darkenedday on 2006-11-19
eth1 is the internet card btw

---

### Post by Peter76 on 2006-11-19
Ok, so if I understand what you want is this: On one ethernetcard you have your internet connection comming in ( from now on eth0 ) and you want to share this with the rest of the ethernet cards.

Make a backup of your /etc/network/interfaces and change it to something like this:


auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

iface eth1 inet static
address 192.168.3.1
netmask 255.255.255.0
gateway 192.168.1.254

iface eth2 inet static
address 192.168.4.1
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0
auto eth1
auto eth2

What this comes down to is: configure your incoming interface to dhcp; and make the rest static. The gateway address is the ip of your router. What is very important is that the third number should be different for all nics; so check what ip you get on the incoming nic ( if the eth1 is this; the ip is 192.168.1.105, so I would say the next is nic gets 192.168._2_.1 , and so on. Look at the example above. Post your new /etc/network/interfaces, so I can have a look at it. In the mean time I'm going to dig up some stuff about ipmasq. Good Luck, and see you in a couple of minutes

---

### Post by darkenedday on 2006-11-19
auto lo
 iface lo inet loopback
 address 127.0.0.1
 netmask 255.0.0.0
 
 iface eth0 inet static
 address 192.168.3.1
 netmask 255.255.255.0
 gateway 192.168.1.1
 
 iface eth1 inet dhcp

 
 iface eth2 inet static
 address 192.168.4.1
 netmask 255.255.255.0
 gateway 192.168.1.1

 
 iface eth3 inet static 
 adress 192.168.5.1
 netmask 255.255.255.0
 gateway 192.168.1.1
 
 auto eth0
 auto eth1
 auto eth2
 auto eth3

thanks for explaining that to me

---

### Post by Peter76 on 2006-11-19
Ok, looks good, now do:

sudo /etc/init.d/networking restart

and

ifconfig

if all is well the ifconfig output should give you your new configuration? Yes????
Post, and we're on to the next step...

---

### Post by darkenedday on 2006-11-19
mike@Apollo:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          SIOCDELRT: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 10235
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:5a:d0:d8:40
Sending on   LPF/eth1/00:10:5a:d0:d8:40
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Operation not permitted
SIOCDELRT: No such process
SIOCADDRT: Network is unreachable
Failed to bring up eth0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:5a:d0:d8:40
Sending on   LPF/eth1/00:10:5a:d0:d8:40
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 128608 seconds.
SIOCADDRT: Network is unreachable
Failed to bring up eth2.
Don't seem to be have all the variables for eth3/inet.
Failed to bring up eth3.


thats what i got when i typed in the restart command, I'm 90% sure my xbox is on eth2 and my step-brother-in-law's laptop is on eth3 (i have no idea how to find out what card is what it doesn't seem to go in any logical order, and i'm a noob, they're both powered on)so I have no idea why eth 3 and eth2 wont come up I don't even see eth0 in there, which may be a good thing maybe on of them is on eth0

this is ifconfig

ike@Apollo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:4B:87:FA:96
          inet addr:192.168.3.1  Bcast:192.168.3.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:10:5A:D0:D8:40
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fed0:d840/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:278120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:307176211 (292.9 MiB)  TX bytes:45383810 (43.2 MiB)
          Interrupt:12 Base address:0xc000

eth2      Link encap:Ethernet  HWaddr 00:10:5A:D1:2D:AC
          inet addr:192.168.4.1  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fed1:2dac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24600 (24.0 KiB)  TX bytes:196296 (191.6 KiB)
          Interrupt:11 Base address:0xe000

eth3      Link encap:Ethernet  HWaddr 00:40:F4:CC:E9:FB
          inet addr:169.254.226.65  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::240:f4ff:fecc:e9fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:20930 (20.4 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:411285 (401.6 KiB)  TX bytes:411285 (401.6 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.77.1  Bcast:192.168.77.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.39.1  Bcast:172.16.39.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Why does eth3 give me some weird inet addr? it's correct in my /etc/network/interfaces

---

### Post by Peter76 on 2006-11-19
I don't get it either why eth3 get's this ip. Could you unplug all your cables except the one on eth1 and do a reboot and see what is happening then?

---

### Post by Peter76 on 2006-11-19
Also, in your old interfaces file at the end was this:


iface br0
bridge_ports all

Is that still there and what does it do? If you don't need it could you remove it?

---

### Post by darkenedday on 2006-11-19
I'll reboot now, I did take out that line, it normally set up a network bridge but it didn't work

---

### Post by Peter76 on 2006-11-19
Ok, I'm still there

---

### Post by darkenedday on 2006-11-19
ok so this is my new ifconfig 

mike@Apollo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:4B:87:FA:96  
          inet addr:192.168.3.1  Bcast:192.168.3.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:10:5A:D0:D8:40  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fed0:d840/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:921278 (899.6 KiB)  TX bytes:142272 (138.9 KiB)
          Interrupt:12 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr 00:10:5A:D1:2D:AC  
          inet addr:192.168.4.1  Bcast:192.168.4.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000 

eth3      Link encap:Ethernet  HWaddr 00:40:F4:CC:E9:FB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.77.1  Bcast:192.168.77.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.39.1  Bcast:172.16.39.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

now eth3 doesn't even show up?

EDIT
nevermind I must've missed it

---

### Post by Peter76 on 2006-11-19
Don't get the problem with eth3... Need to go to sleep now... I'll be back tomorrow at same time. You can ttry if the internet sharing works now with ipmasq. Do dpkg-reconfigure ipmasq again and do following options:

should ppp connections recompute firewall -> no
When should ipmasq start -> after network services are up

And then:

sudo /etc/init.d/ipmasq restart and check if it works.

Also look through dmesg if you can find something about eth3. If you not here tomorrow send me a pm when you're here and I'l try to get back. Good luck

---

