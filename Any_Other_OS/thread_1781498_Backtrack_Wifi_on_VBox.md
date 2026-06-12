---
title: "Backtrack Wifi on VBox"
date: 2011-06-13
forum: Any Other OS
---

### Post by layers on 2011-06-13
I needed to use Backtrack yesterday, but do not have currently the cd. So, after installing it in vbox, i see that the wireless hardware is not really being used by vbox, but only emulated. I have been trying to make vbox use the real wireless adapter in my laptop (bridged), but to no avail. 
Does anyone know how to get this working?

---

### Post by layers on 2011-06-13
has anyone tried 
[http://ubuntuforums.org/showpost.php?p=4507341&postcount=14](http://ubuntuforums.org/showpost.php?p=4507341&postcount=14)

---

### Post by uRock on 2011-06-13
Moved to Other OS/Distro Talk

---

### Post by layers on 2011-06-13
On the host machine I have
```
eth0      Link encap:Ethernet  HWaddr 78:84:3c:02:64:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:213669 (213.6 KB)  TX bytes:213669 (213.6 KB)

wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:f5:64:b1  
          inet addr:192.168.178.63  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::4e0f:6eff:fef5:64b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64170235 (64.1 MB)  TX bytes:10003933 (10.0 MB)
```

and the guest is 

```
root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:5c:1d:de  
          inet addr:192.168.178.66  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe5c:1dde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3266 (3.2 KB)  TX bytes:1906 (1.9 KB)
          Interrupt:10 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

```

---

### Post by layers on 2011-06-14
shameless bump?

---

### Post by Siph0n on 2011-06-15
What I did was edit the interfaces file in backtrack. I commented out everything except lo and wlan0 . Or you may also be able to do an "ifconfig wlan0 up"

---

### Post by PiixJu on 2011-06-16
maybe it's easier to use grub to boot backtrack iso?

---

