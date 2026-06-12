---
title: "Update hanging..."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-12
I just installed 7.04, and in the Update Manager when trying to download the kernel image file, it hangs, or it just randomly stops downloading at other files. Is there another method that works better?

if I keep re-opening it, it seems to make more progress...have it up to 90% now

---

### Post by starcraft.man on 2007-06-12
> **FleetAdmiral74 said:**
> I just installed 7.04, and in the Update Manager when trying to download the kernel image file, it hangs, or it just randomly stops downloading at other files. Is there another method that works better?

if I keep re-opening it, it seems to make more progress...have it up to 90% now

Thats a networking issue with your connection. Not a problem with the update manager. Sounds like for some reason your getting dropped off.

Do the following please in a terminal (Applications > Accessories > Terminal):

```
ifconfig
```

paste the output here in the code tags (# sign).
```

ping ubuntu.com
```

push ctrl + C after 30 seconds/lines and paste the output at the bottom in code tags too.

I'm not a super networking expert so if its not obvious, might need to wait for someone more knowledgeable.

---

### Post by FleetAdmiral74 on 2007-06-12
```
ed@database:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:F2:16:ED:71  
          inet addr:192.168.0.146  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe16:ed71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97726506 (93.1 MiB)  TX bytes:2929938 (2.7 MiB)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

```

I will not post the entire second part unless you need it,

```
64 bytes from arctowski.ubuntu.com (82.211.81.158): icmp_seq=28 ttl=42 time=151 ms
64 bytes from arctowski.ubuntu.com (82.211.81.158): icmp_seq=29 ttl=42 time=153 ms
64 bytes from arctowski.ubuntu.com (82.211.81.158): icmp_seq=30 ttl=42 time=152 ms

--- ubuntu.com ping statistics ---
30 packets transmitted, 30 received, 0% packet loss, time 29095ms
rtt min/avg/max/mdev = 150.667/152.794/158.841/1.587 ms
ed@database:~$ 

```

---

### Post by FleetAdmiral74 on 2007-06-13
```
$ sudo bump
```

---

