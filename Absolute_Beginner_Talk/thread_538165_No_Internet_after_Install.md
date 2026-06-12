---
title: "No Internet after Install"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ericsaxalto on 2007-08-29
I have cable internet (wireless) in the house.  I received the laptop on Monday and immediately loaded Ubuntu 7.04.  I've been waiting a while to do this.  I seem to have a functional desktop, but I cannot get any internet access.  Even when I plugged into the router (Linksys wireless G cable gateway) I couldn't connect.  I tried using the Networking tabs to enter the IP address and everything appears to have been recognized.  I really don't want to have to re-install windows on the machine but I can't figure out if I just have the settings wrong or if it's a hardware issue.  I have a Gateway MT6705 Intel Dual Core processor, ethernet card, and wireless and 802.11 wireless g Lan.  If you have any suggestions I would appreciate the help.  Right now Firefox just tells me "Firefox cannot find server".:confused:

---

### Post by jasonlfunk on 2007-08-29
if you're network uses DHCP, which it probably does - change your Network settings back to Automatic and then enter ```
sudo dhclient
``` in a terminal and see what it says.

---

### Post by wormser on 2007-08-29
Can you get us more information.  Post the results of the following commands.  Applications> Accessories> Terminal

```
lspci
```
```
ifconfig
```
```
ping ubuntuforums.org
```
```
ping 82.211.81.186
```

---

### Post by ericsaxalto on 2007-08-29
Thanks for you suggestions, but I'm still really new at this.  I went to Network settings and I don't know how to set the network settings back to automatic.  I did fid terminal and I can try the codes.  Please advise.

---

### Post by peebly on 2007-08-29
> **ericsaxalto said:**
> Thanks for you suggestions, but I'm still really new at this.  I went to Network settings and I don't know how to set the network settings back to automatic.  I did fid terminal and I can try the codes.  Please advise.

A little bit more info on the wireless card would be helpful i.e model no etc.

also is the wireless card actually working, i.e any lights on it.

---

### Post by ericsaxalto on 2007-08-29
When I typed in the first command "sudo dhclient" it asked for a password.  I entered the password and it said

Listening on LPF/wlan0/00:c0:a8:d7:a8:c0
Sending on LPF/wlan0/00:c0:a8:d7:a8:c0
Listening on LPF/eth0/00:e0:b8:c4:be:73
Sending on LPF/eth0/00:e0:b8:c4:be:73
Sending on Socket/fallback
DHCPDISCOVER on Wlan0 to 255.255.255.255 port 67 interval 8   

---- and many other lines of command that only differend in the last number after "interval"

---

### Post by ericsaxalto on 2007-08-29
Sure thing,

PC: Gateway MT6705.  The wireless light is on.  When I go System to Administration to Networking it shows that both the ehternet card and the wireless are activated.

---

### Post by ericsaxalto on 2007-08-29
to "lspci" it told me 

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2
0000:00:1d.1 USB Controller: INtel Corporation 82801G (ICH7 Family) USB UHCI#3
etc...

It also told me:

PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:lf.0 ISA bridge: Intel Corporation 82801GBM (Ich7-M)LPC Interface Bridge (rev 02)

Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4352 (rev 14)
0000:03:09 CardBus bridge: Texas Instruments: Unknown device 8039
Firewire - also Texas Instruments : Unknown device 803a
0000:03:09.2 Mass storage controller: Texas InstrumentsL Unknown device 803.b

---

### Post by ericsaxalto on 2007-08-29
> **ericsaxalto said:**
> to "lspci" it told me 

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2
0000:00:1d.1 USB Controller: INtel Corporation 82801G (ICH7 Family) USB UHCI#3
etc...

It also told me:

PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:lf.0 ISA bridge: Intel Corporation 82801GBM (Ich7-M)LPC Interface Bridge (rev 02)

Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4352 (rev 14)
0000:03:09 CardBus bridge: Texas Instruments: Unknown device 8039
Firewire - also Texas Instruments : Unknown device 803a
0000:03:09.2 Mass storage controller: Texas InstrumentsL Unknown device 803.b

When I typed "ifconfig" it replied:
eth0
Link encap:Ethernet HWaddr 00:E0:B8:C4"BE73
UP BROADCAST MULTICAST MTU:1500 METRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0b) TX bytes:0 (o.ob)

lo
Link encap:local loopback 
inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
Rx Packets:7 errors:0 dropped:0 overruns:0 frame:0
TX packets7: errors:0 dropped:0 overruns:0 carrier:0
Collisions:0 txqueuelen:0
RX bytes:372 (372.0b) TX bytes: 372 (372.0b)

wlan0
Link encap: Ethernet HWaddr 00:C0:A8:D7:A8:C0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets:0 errors:0 dropped:0 Overruns:0  frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisions:0 txqueuelen:1000
Rx bytes:0 (0.0b)  TX bytes:0 (0.0 b)

---

### Post by ericsaxalto on 2007-08-29
It tells me that Ubuntuforums.org 

ping: unknown host ubuntuforms.org

To the last command it replies:

"Network is unreachable"

---

### Post by wormser on 2007-08-29
This looks like it is a hardware issue.  
> Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4352 (rev 14)
I  am not that great with hardware problems so I can only help a bit.  Maybe somebody else can figure it out.  Start searching google for a guide.

This looks like the model number of the card.
> Marvell Yukon 88E8038 PCI-E Fast Ethernet Controller

---

