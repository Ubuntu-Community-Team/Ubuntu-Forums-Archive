---
title: "[SOLVED] wireless cannot connect"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by SoulSmasher on 2008-02-17
hi, i'm using acer aspire 5104 laptop with gutsy gibbon, i have a simple issue. searched similar posts, but couldn't find :(
i can't connect to internet with wireless networks.. 
i mean, i think i can connect to networks, but can't get any ip
it has broadcom branded wireless which i use with standart restricted drivers
but when i log in with windows everything is ok :S

and also with wired network, it's ok

some of my friends told me that it may be from ubuntu's ipv6 stuff..
is there any way that i can solve this issue ? 
thanks for any help :)

edit: look for latest posts, there are the solutions :)

---

### Post by jw5801 on 2008-02-17
If you aren't given an IP address then you aren't properly connected to a network. ipv6 being enabled affects a wired connection just as much as a wireless connection, in that it slows down your networking minutely because it will try to use ipv6 (a much newer and better protocol than ipv4, but one that isn't widely in use as yet) and then when that doesn't work use ipv4.

The issue is most likely with the driver for the card, can you be more specific about the card? Broadcom make a _lot_ of wireless chipsets.

---

### Post by SoulSmasher on 2008-02-17
when i type lspci and iwconfig in terminal, this is the output..

```
arda@arda-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
arda@arda-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"adsl"  Nickname:"adsl"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

arda@arda-laptop:~$ 

```

can't connect to internet though..

(when i open the program: wifi radar, it says connected to "adsl" (IP address: None)
i googled a bit, some sources tell that ive to use "ndiswrapper" for broadcom cards
pretty confused :S

---

### Post by jan quark on 2008-02-17
try this guide to enable the drvers for the broadcom 4311
I hate this card ;)

[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

edit:

post the output of 
```

sudo lshw -C network
```

---

### Post by SoulSmasher on 2008-02-17
firstly, thanks for quick reply , before doing this, should i disable currently enabled broadcom 43xx firmware that is automatically recogined before ? (at first login , restricted drivers manager said there is a dreiver for broadcom, it downloaded it and enabled as usual)

and here's the output that you requested:
```
arda@arda-laptop:~$ sudo lshw -C network
[sudo] password for arda:
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:6f:73:41
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:db:61:6d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
arda@arda-laptop:~$ clear

arda@arda-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:6f:73:41
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:db:61:6d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
arda@arda-laptop:~$ 
```

---

### Post by jan quark on 2008-02-17
hmm your drivers seem to be recognized well by ubuntu

please post also the output from
```

cat /etc/network/interfaces
```

---

### Post by SoulSmasher on 2008-02-17
output is:
```
auto lo
iface lo inet loopback
```

---

### Post by jan quark on 2008-02-17
run 

```
gksudo gedit /etc/network/interfaces
```

and change the file to this one
```
auto lo
iface lo inet loopback

iface eth1 inet static
address xxx.xxx.xxx.xx                          < your ip address
netmask 255.255.255.0
gateway 192.168.178.1                           < your router address, that is mine router address
wireless-key s:xxxxxxxxxxx                   <wep key if you have one, if not that do not add this line
wireless-essid NameOfYourNetwork



auto eth1
```

save the file and run
```

sudo /etc/init.d/networking restart
```

---

### Post by SoulSmasher on 2008-02-17
by the way, the network that i am trying to connect has dynamic ip (damn!)
should i change it always ?

---

### Post by jan quark on 2008-02-17
you can also configure your network setting here

system > administration > network

does the wireless icon show up? 
if yes go to properties and configure it there
it is pretty the same stuff like in the interfaces file but with a graphical interface
there you can also set select dhcp

---

### Post by s0ullight on 2008-02-17
hi i got a solution that worked for me.

if you just want to connect to networks and don't need anything like monitor mode etc.
do this 

1.Install ndiswrapper from the Ubuntu repository with Synaptic Package Manager(or if you don't have connection with linux download it with windows or something like that, i mean the .deb file)

2.Remove the old driver:
# sudo modprobe -r bcm43xx

3.Bblacklist it from not loading again by adding this line to the file /etc/modprobe.d/blacklist:
blacklist bcm43xx

3.Get the proprietary driver from the HP-site: sp34152.exe

4.Extract it: (you may need to install cabextract first with Synaptic as I had to)or like in #1
# cabextract -a ./sp34152.exe

5.Change into the directory you extracted these files to and:
# sudo ndiswrapper -i bcmwl5.inf
# sudo ndiswrapper -l

6.To configure ndiswrapper to start on every boot (along with the new driver):
#sudo ndiswrapper -m
#sudo modprobe ndiswrapper
#sudo echo ndiswrapper > /etc/module


now it should be working fine 
allthough it worked for me perfectly but i need that monitor mode :|

---

### Post by SoulSmasher on 2008-02-17
@jan quark - wireless icon shows up at there (wireless, wired, modem networks)
i think i'll give up,
after i get the ip netmask infos etc from windows, then used on ubuntu , still cannot acquire ip

it was same before the format

and when i enable manual settings, the pc becomes horribly laggy :S

**edit:** i'm now trying your solution soullight, i'll post solution, thanks
btw, what about hp ?

**edit2:** sudo ndiswrapper -l command returns nothing :S

---

### Post by SoulSmasher on 2008-02-17
by the way, from system/administration/windows wireless drivers
should i add windowss' inf drivers as well ?

---

### Post by jw5801 on 2008-02-17
[This](http://ubuntuforums.org/showthread.php?t=297092) howto for ndiswrapper will also work for this card. Very similar to the instructions that s0ullight gave.

---

### Post by SoulSmasher on 2008-02-18
thanks everyone, i pretty messed up yesterday the settings so i formatted :), the only thing i did wrong was forgetting to blacklist restricted stuff, i solved myself with googling late at night, maybe this should be an alternative way

i followed [this]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/") guide which is exactly for my wireless card (i mean the same broadcom model (4311) ). both techniques are the same, except i used broadcom's driver instead of given one there, whatever, so worked like a charm:)

**thanks everyone who posted here, and helped me to get the point :) **

---

