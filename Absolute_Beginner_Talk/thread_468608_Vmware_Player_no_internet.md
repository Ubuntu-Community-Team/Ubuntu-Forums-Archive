---
title: "Vmware Player no internet"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by ghost_ryder35 on 2007-06-09
I installed VMware Server but it was ungodly slow, so i switched to Vmware player.  I do not have any internet connectivity with my vitual machines XP and Debian.  Both of them get an address from the vmnet whatever but they cannot surf the web.  What is wrong here, when i first installed them they had internet, now they do not.  I tried going back to VMWARE server but it says i have to uninstall something first but all of VMware Server, and Vmware Player are uninstalled compltetly according to Synaptic Package manager.  If I can get either one to work online that would be awesome,  it would be awesome to get Vmware Server back too but I mainly just want the internet to be working in my Virtual Machines.  And yes it does work on Ubuntu.  I'm running Ubuntu 7.04 using my BCMxx wireless card.

---

### Post by ghost_ryder35 on 2007-06-09
need help with this one, its really starting to piss me off

---

### Post by ghost_ryder35 on 2007-06-09
here is what "ifconfig" says



inick@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:DF:3E:AE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:46:4E:F4  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe46:4ef4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:915070 errors:0 dropped:196546 overruns:0 frame:0
          TX packets:766421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:857521996 (817.7 MiB)  TX bytes:282139268 (269.0 MiB)
          Interrupt:10 

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:DF:3E:AE  
          inet addr:169.254.7.84  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:768 (768.0 b)  TX bytes:768 (768.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.199.1  Bcast:172.16.199.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.19.1  Bcast:192.168.19.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

nick@Ubuntu:~$

---

### Post by straps on 2007-06-09
Do you see the 2 interfaces on host OS?

When you run vmware-config.pl it asks how many interfaces do you want to map. Have you mapped eth0 and eth1?

I have Feisty with vmware server and everything works very well; in vmware-config.pl I have selected:
> Do you want NAT networking for your Virtual Machines? NO
Do you want Host Only Networking? NO
Do you want Bridge Networking? YES


What is the output for:
[B]ifconfig -a
route -n
cat /etc/resolv.conf
[/B]on you debian host?

Bye

---

### Post by ghost_ryder35 on 2007-06-09
> **straps said:**
> Do you see the 2 interfaces on host OS?

When you run vmware-config.pl it asks how many interfaces do you want to map. Have you mapped eth0 and eth1?

I have Feisty with vmware server and everything works very well; in vmware-config.pl I have selected:



What is the output for:
[B]ifconfig -a
route -n
cat /etc/resolv.conf
[/B]on you debian host?

Bye

nick@Ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:22:DF:3E:AE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:46:4E:F4  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe46:4ef4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4497 errors:0 dropped:1425 overruns:0 frame:0
          TX packets:4247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3472244 (3.3 MiB)  TX bytes:634089 (619.2 KiB)
          Interrupt:10 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:DF:3E:AE  
          inet addr:169.254.7.84  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.199.1  Bcast:172.16.199.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.19.1  Bcast:192.168.19.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

nick@Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.19.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
172.16.199.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0


nick@Ubuntu:~$ cat /etc/resolv.conf
search domain_not_set.invalid
nameserver 192.168.0.1
nameserver 216.165.129.157

---

### Post by veloce on 2007-06-10
Why do you have both eth0 and eht1?  If you just have wireless, then you should just have one interface?  If you have built in ethernet card that you are not using, I would suggest turning it off in your bios settings.  

Then re-run vmware-config.pl (or if you are using vmware server 1.0.3 vmware-config-network.pl) setting all the networks off except bridged (as suggested above).

---

