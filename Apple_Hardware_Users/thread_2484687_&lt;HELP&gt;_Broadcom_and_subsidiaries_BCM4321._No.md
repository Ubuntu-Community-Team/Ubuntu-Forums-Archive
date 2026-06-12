---
title: "&lt;HELP&gt; Broadcom and subsidiaries BCM4321. No Netw!!! MacBook 4,1 Late-08 Old Black"
date: 2023-03-06
forum: Apple Hardware Users
---

### Post by leoxavi3r on 2023-03-06
MacBook specs = [https://everymac.com/systems/apple/macbook/specs/macbook-core-2-duo-2.4-black-13-early-2008-penryn-specs.html](https://everymac.com/systems/apple/macbook/specs/macbook-core-2-duo-2.4-black-13-early-2008-penryn-specs.html)

*Ralink RT2870/RT3070* "usb" = On
USB anthena

BUT **Broadcom and subsidiaries BCM4321** **IS offline**
DOES NOT WORK
QUESTION MARK IN FRONT OF WIFI ICON
NO INTERNET
NO NETWORK

SAME CONNECTION

SO LETS GO >>>

**UBUNTU 22.04**
To install vpn from UNIVERSITY
I DID THESE STEPS=
[https://www.ccuec.unicamp.br/ccuec/m...inux_vpn_18_04]("https://www.ccuec.unicamp.br/ccuec/material_apoio/tutorial_linux_vpn_18_04")

NOW WIFI NATIVE DRIVER JUST WORKS THERE IN THE UNIVERSITY
BUT NOT IN MY HOME!!!

I TRIED REMOVED TO ACCESS NETWORK BUT JUST WITH ANTHENA

THESE COMMANDS CAN GIVE YOU SOME INFOS >>>

 ```
sudo systemctl restart NetworkManager
``` works with ethernet cable but not with wifi native

 Some more infos

```
sudo lshw -C network
```
  *-network                 
       descrição: Interface sem fio
       produto: BCM4321 802.11a/b/g/n
       fabricante: Broadcom Inc. and subsidiaries
       ID físico: 0
       informações do barramento: pci@0000:02:00.0
       nome lógico: wls4
       versão: 03
       serial: 00:1e:c2:a3:7b:27
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuração: broadcast=yes driver=wl0 driverversion=6.30.223.271  (r587334) ip=192.168.50.176 latency=0 multicast=yes wireless=IEEE  802.11
       recursos: irq:16 memória:d0500000-d0503fff memória:d0000000-d00fffff
  *-network
       descrição: Ethernet interface
       produto: 88E8058 PCI-E Gigabit Ethernet Controller
       fabricante: Marvell Technology Group Ltd.
       ID físico: 0
       informações do barramento: pci@0000:03:00.0
       nome lógico: ens5
       versão: 13
       serial: 00:1e:c2:10:9c:8b
       capacidade: 1Gbit/s
       largura: 64 bits
       clock: 33MHz
       capacidades: pm vpd msi pciexpress bus_master cap_list rom  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuração: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       recursos: irq:27 memória:d0400000-d0403fff porta de E/S:5000(tamanho=256) memória:d0420000-d043ffff

```
ls -al /etc/resolv.conf
```
lrwxrwxrwx 1 root root 39 jan 21 17:18 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

```
 sudo dmesg | grep -e e100 -e eno1
```
[sudo] senha para leo: 
[    0.055034] ACPI: Reserving DSDT table memory at [mem 0xbeee1000-0xbeee55c5]
 and this too
 ip route show
default via 192.168.50.1 dev ens5 proto dhcp metric 100 
default via 192.168.50.1 dev wls4 proto dhcp metric 20600 
169.254.0.0/16 dev wls4 scope link metric 1000 
192.168.50.0/24 dev ens5 proto kernel scope link src 192.168.50.110 metric 100 
192.168.50.0/24 dev wls4 proto kernel scope link src 192.168.50.176 metric 600 

```
ping -c 5 192.168.50.176
```
PING 192.168.50.176 (192.168.50.176) 56(84) bytes of data.
64 bytes from 192.168.50.176: icmp_seq=1 ttl=64 time=0.116 ms
64 bytes from 192.168.50.176: icmp_seq=2 ttl=64 time=0.123 ms
64 bytes from 192.168.50.176: icmp_seq=3 ttl=64 time=0.080 ms
64 bytes from 192.168.50.176: icmp_seq=4 ttl=64 time=0.110 ms
64 bytes from 192.168.50.176: icmp_seq=5 ttl=64 time=0.079 ms

--- 192.168.50.176 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4094ms
rtt min/avg/max/mdev = 0.079/0.101/0.123/0.018 ms

PLEASE HELP SOS,

LEO

---

### Post by leoxavi3r on 2023-03-06
[IMG]https://i.imgur.com/RI9yYbm.png[/IMG]

---

### Post by QIII on 2023-03-06
Moved to Apple Hardware Users.

---

### Post by leoxavi3r on 2023-03-06
> **QIII said:**
> Moved to Apple Hardware Users.

No problem and thanks, **but**
Do u have some solution for this networking issue?

*Thanks*,
*Leo*

---

### Post by leoxavi3r on 2023-03-07
Up

---

### Post by leoxavi3r on 2023-03-07
> **QIII said:**
> Moved to Apple Hardware Users.

I am supposing u didn't read my post but this is not about hardware
So you moved my post and here nobody is helping my issue

****

---

### Post by leoxavi3r on 2023-03-07
Someone can help me??? 2 weeks without any solution here in this forum

---

