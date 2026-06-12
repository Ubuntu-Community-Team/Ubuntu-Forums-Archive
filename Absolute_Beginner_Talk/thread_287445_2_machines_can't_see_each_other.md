---
title: "2 machines can't see each other"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by benner on 2006-10-28
i have 1 a desktop running Edubuntu edgy and a notebook with windows/kubuntu dual boot that has dapper but is currently downloading the upgrade as i type.  the two are connected to the Internet through a router (Netgear w/ wireless) and the two machines are both using Ethernet cables.  they connect to the Internet just fine.  they can ping each other just fine.  the network connection tool in edgy looks easier than ever and yet i can't get it sorted out. 

if config on this machine is:

ben@ben-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:02:07:3B:91  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe07:3b91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2129938 (2.0 MiB)  TX bytes:392791 (383.5 KiB)
          Interrupt:3 Base address:0x6f80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 b)  TX bytes:700 (700.0 b)


the other machine is named: ben-laptop  and it's ip is 192.168.1.4

suggestions?  

many thanks in advance...

---

### Post by Bachstelze on 2006-10-28
What exactly do you want to do ? File sharing ?

---

### Post by benner on 2006-10-28
yes.  sorry if that wasn't clear.  i want to be able to share files between them whether the notebook is running windows (xp) of kubuntu.

---

