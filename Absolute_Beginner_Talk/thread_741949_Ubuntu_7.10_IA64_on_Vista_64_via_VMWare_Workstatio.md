---
title: "Ubuntu 7.10 IA64 on Vista 64 via VMWare Workstation 6: Network unreachable"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by pojkra on 2008-04-01
Hi,
I'm currently trying to run Ubuntu 7.10 IA64 on Vista 64 via VMWare 6.0.2 and I'm having trouble with gaining internet access. I set the IP of my card in Windows to 192.168.0.1 so I can use it as a gateway, right? I ran sudo network-admin and set gateway and address as you can see here:

```
/etc/network/interfaces:

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0
```

But I'm even unable to ping the IP I specified for eth0:

```
binrapt@binrapt-Ubuntu:~$ vim /etc/network/interfaces
binrapt@binrapt-Ubuntu:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.043 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.030 ms

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.030/0.036/0.043/0.008 ms
binrapt@binrapt-Ubuntu:~$ ping 192.168.0.1
connect: Network is unreachable
binrapt@binrapt-Ubuntu:~$ ping 192.168.0.2
connect: Network is unreachable
binrapt@binrapt-Ubuntu:~$ 
```

I've tried different VMWare network settings (Bridged, NAT, etc) but none of them changed anything but I suppose it's an Ubuntu user error. Somebody care to enlighten me? What am I doing wrong?

Edit:

Problem solved by restarting Ubuntu. Apparently VMware Tools required me to restart Ubuntu to work properly for some reason. After restarting the VM a new icon popped up, "unsupported driver warning" or something like that. But my old settings worked just fine and I could ping everything and I got internet access now.

---

### Post by mick8985 on 2008-04-01
You could have just done

```
 sudo /etc/init.d/networking restart
```

---

