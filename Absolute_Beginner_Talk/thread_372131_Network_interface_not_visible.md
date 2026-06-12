---
title: "Network interface not visible"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2007-02-27
Hi,
I created a bootable USB pendrive (USBEdgy) and booted using it.  However, I am unable to access internet.  If I boot from the harddisk (which is also ubuntu Edgy), I could access the net. The following are the contents of /etc/network/interfaces and  /etc/resolv.conf and ifconfig -a output:

When booted using Harddisk:
```
vijay@vijay-Desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

vijay@vijay-Desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
vijay@vijay-Desktop:~$
vijay@vijay-Desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:65:4D:30
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:49:A7:F5:4B
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:49ff:fea7:f54b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:685074 (669.0 KiB)  TX bytes:187420 (183.0 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:972 (972.0 b)  TX bytes:972 (972.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

When booted from the pendrive:
```
ubuntu@ubuntu-Desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

ubuntu@ubuntu-Desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
ubuntu@ubuntu-Desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:65:4D:30
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Also there is a "default gateway device" in System->Administration->Networking when booted from the harddisk.  But there is no such thing when booted from the pendrive.

Please help how this can be resolved.  Thanks.

---

### Post by vijayanand_sodadasi on 2007-02-28
anybody please??

---

