---
title: "No WiFi on rev.3 MBP After Reboot"
date: 2008-06-18
forum: Apple Hardware Users
---

### Post by martinbures on 2008-06-18
Hi - I'm having a strange problem here.  I just did a fresh install of Hardy on a rev. 3 MBP.  I followed the instructions on the wiki(I have done these installs many times) and installed MadWiFi from the svn repo first.  That turned out to be pretty flaky, so I then deleted that, downloaded the most recent release, and that worked fine.  I turned the machine off for the evening and today, no wifi.  The hardware is detected, the modules are loaded but the interface does not show up:

```

martin@martin-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:63:97:41:46  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fe97:4146/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2632057 (2.5 MB)  TX bytes:451820 (441.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94600 (92.3 KB)  TX bytes:94600 (92.3 KB)
```

output of lspci -v:
```
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
	Subsystem: Apple Computer Inc. Unknown device 0087
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at d7300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
	Subsystem: Marvell Technology Group Ltd. Unknown device 00ba
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at d7200000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 3000 [size=256]
	Expansion ROM at db600000 [disabled] [size=128K]
	Capabilities: <access denied>

```

If I reboot into OS X, Wifi works properly.
any ideas?

Thanks.
martin.

---

### Post by cyberdork33 on 2008-06-18
the stable release does not support these cards. You have to get a snapshot.

---

### Post by martinbures on 2008-06-19
Thanks!  I am a dummy.

martin.

---

