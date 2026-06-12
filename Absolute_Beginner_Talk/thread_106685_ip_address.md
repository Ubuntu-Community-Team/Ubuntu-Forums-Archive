---
title: "ip address"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-21
i have got this computer with windows xp home on, now the question is where on my computer will i 
find the right information like my IP address > port subnet mask >gatewawy address, because  this is needed when getting ubuntu going,can anybody help

---

### Post by Gandalf on 2005-12-21
does the Network panel (the two computer screen on the panel above) provide this information? if not then open a terminal (Applications -> Accessories -> Terminal) and type
```

ifconfig

```

you will have info on all network interfaces, usually your interrest is eth0 (or eth1 in case of wlan connection) you can ignore the lo interface, here's a sample of the result
```

eth1      Link encap:Ethernet  HWaddr 00:0E:35:75:95:F2
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe75:95f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4950 errors:0 dropped:2 overruns:0 frame:0
          TX packets:3543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4815847 (4.5 MiB)  TX bytes:373138 (364.3 KiB)
          Interrupt:18 Memory:e0206000-e0206fff

```

your only interrest will be the line
```

inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0

```
the inet addr is your ip address, the Mask is your netmask and of course Bcast is the broadcast address...

now to get the gateway do
```

arp -a

```

sample of the result
```

? (192.168.2.1) at 00:11:95:84:D0:4B [ether] on eth1

```
which is in my case 192.168.2.1

Hope that helps

---

### Post by Lambert on 2005-12-21
Do you mean you need to find the information on you xp box? Gandalf gave you how to for ubuntu if that's what you need.
 
If you need it for xp then do this.
 
start>run   type in cmd press enter. You should get a window that looks like a terminal then type ipconfig /all
 
the same information gandalf pointed out will print to screen but in the format that xp reports it.

---

