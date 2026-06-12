---
title: "Wireless Access for New User!"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by JiggyFilipino on 2006-02-12
I have just installed Ubuntu because WinXP was messed up. Now I am trying to access the internet using my wireless card but it is not working and I have NO idea how to turn the card "on". It does show the card in the "Device Manager" but it is not working and I am getting tired of trying different things. Does anyone have ANY ideas on what I can do to make it show up. I am using a Motorola WR825 Wireless Network Card on a Compaq Presario Lapton 2103US. My Wired Ethernet is working (obviously because I am writing this) but I wireless is out. Any ideas?

---

### Post by UbuntuLinuxUser on 2006-02-12
bump

---

### Post by Jason_25 on 2006-02-12
Does it show up in system > administration > networking?

---

### Post by alamba on 2006-02-12
Does your system have a hard wireless button? If yes you need to press that and make sure the light is on. If not, post the following here:

1. ifconfig
2. netstat -rn
3. lspci

Also, have to tried to "activate" your wireless card from system>>admin>>networking? Click on properties and put in your SID, etc.

A

---

### Post by UbuntuLinuxUser on 2006-02-12
[QUOTE=alamba]Does your system have a hard wireless button? If yes you need to press that and make sure the light is on. If not, post the following here:

1. ifconfig
2. netstat -rn
3. lspci

Also, have to tried to "activate" your wireless card from system>>admin>>networking? Click on properties and put in your SID, etc.

A[/QUOTE]

I tried installing the driver, but it says "hardware isn't present"so I can't activate.

---

### Post by alamba on 2006-02-12
hmm...that error only tells me 2 things:
1. You have a hard button that you have'nt switched on
2. Your specific hardware does'nt have inbuilt drivers in ubuntu

Options:
1. Turn the button on
2. Check google for your NIC drivers, if you find it - great. If not search the forums for ndiswrapper and use the windows drivers.

A

---

### Post by Tiede on 2006-02-12
Have you tried enabling your driver with the ndiswrapper package? If you still have your MSWindows partition, you can try copying the .inf and the .sys file for your card to ~/wireless-card/ and then in a terminal, type
```
sudo apt-get install ndiswrapper ndisgtk
cd ~/wireless-card/
ndiswrapper -i *.inf
ndiswrapper -l
```
the first step installs ndiswrapper, the second will move to the directory you copy the windows driver files (.inf and .sys) to, the third will enable your wireless card for ubuntu, and the last one is just to verify whether or not the card is installed correctly.
If it is, the output will be ```
Installed ndis drivers:
whateveritis driver present, hardware present

```
if so, you can continue by going to System->Admin->Windows Wireless Drivers. the rest, you should be able to do on your own.

---

### Post by JiggyFilipino on 2006-02-12
Hey guys! Thanks for the reply.

To Answer some of the questions. No I don't have a wireless button for the wireless on this laptop. I have to use a PCMCIA card to access the internet. Also, the card does not show up on Systems>Admin>Networking. I will post what I have though from one of the posts, maybe someone can help:)

from ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0F:20:1F:EF:95
          inet addr:191.168.2.1  Bcast:191.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe1f:ef95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37439269 (35.7 MiB)  TX bytes:2092915 (1.9 MiB)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13592879 (12.9 MiB)  TX bytes:13592879 (12.9 MiB)

NETSTAT:
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
191.168.2.2     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         191.168.2.2     0.0.0.0         UG        0 0          0 eth0

LSPCI:
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Help!:)

---

