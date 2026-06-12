---
title: "Cannot access network in Ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by mikeyandmary on 2007-04-14
Hi all,

I am having problems accessing my local network when on Ubuntu. The machine is a Celeron 2800 with onboard NIC and (currently) d-link NIC. It dual boots XP Pro and Ubuntu 6.06LTS

I can access the network perfectly using XP and the other computers (1 PC and 2 laptops) run perfectly on the network in either XP or ubuntu. 

I have tried restarting the router, new cables, new NIC, using ifdown then ifup... The problem seems to be from the point the PC is switched on. The router shows no connection and in network tools it says there is no IP address. The problem occurs on  the onboard and pci network cards. 

I would love to permanently remove all microsoft software & OS from my computers but am wary to until I know this problem is solved. 

PLEASE HELP!!!! :confused: :confused: :confused:

---

### Post by mahy on 2007-04-14
It'll help greatly if you tell us your network's whereabouts. DHCP? Static IP? Output of ifconfig... and so on

---

### Post by mikeyandmary on 2007-04-14
Network is DHCP
Address range is 192.168.2.101 to 192.168.2.150
Router is D-Link DI-524UP

ifconfig gives
eth2   Link encap:Ethernet  HWaddr *"mac address"*
          inet6 addr: fe80::219:5bff:fe45:30ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 MiB)  TX bytes:0 (0.0 MiB)
          Interrupt:209 Base address:0x8000

---

### Post by Austin_KW on 2007-04-14
Output of "cat /etc/network/interfaces"

and "sudo dhclient eth2"
[edit]
"sudo dhclient eth0"
"sudo dhclient eth1"

---

