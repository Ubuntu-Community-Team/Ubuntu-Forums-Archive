---
title: "Can't connect to wireless network"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Jicks on 2008-01-27
Alright I am absolutely new to linux and I am just trying to get my Wireless network card working. 
I suspect this could be a fairly complicated procedure so I'll give  you all the information I can to help identify a solution easier.
I'm running linux on my Asus Laptop (F5Rseries).
Its wireless card is 802.11b/g +BT (which through a google search I assume is the Panasonic Wireless 802.11 b/g).

I'm not entirely sure which linux version I have as it was installed about a couple of months ago and have only been able to get around to starting it now. But, when I type 'uname -a' the output is: Linux jack-laptop 2.6.22-14 generic #1 SMP Sun Oct14 23:05:12 GMT 2007 i686 GNU/Linux

I have no access to the internet through the laptop and thats why I'm trying to get it to work. As well as to access my network. If theres anything I can do to learn a solution to this quickly I'd really appreciate it, otherwise, I don't mind spending a few grueling hours getting it to work if I'm going to learn a lot about the system in general.

Thanks!

---

### Post by ibizatunes on 2008-01-27
Do u need to install restricted drivers system > admin > restricted drivers,
u may need to hard wire into a internet connection to install the drivers you need!
Just a thought!

---

### Post by Jicks on 2008-01-27
The firmware for "Broadcom 43xx chipset family" is not in use and I can't enable it :(

---

### Post by ibizatunes on 2008-01-27
U need to enable it, by downloading it.....
U need to plug u laptop into a hardwire connection, download that...... andu need to enable it!! That more than likely will fix your issue!!

---

### Post by jan quark on 2008-01-27
can you post please the results of the following terminal commands

```
iwconfig
```
```
ifconfig
```
```
lspci
```
```
sudo iwlist scan
```

it is just to get some more input

---

### Post by Jicks on 2008-01-27
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jack@jack-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:96:FF:D9
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:feac0000-feb00000

jack@jack-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
06:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
jack@jack-laptop:~$ sudo iwlist scan
[sudo] password for jack:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

---

### Post by bryanpaintballin on 2008-01-30
hi all, im faily new to ubuntu, i used to use fedora but decided to erase it. I am having the exact same problem with connecting to the internet wirelessly, i think it might because the device is restricted, and its the same device as mentioned here. When i try to enable it it gives me an error and i can't enable it, any help??

---

