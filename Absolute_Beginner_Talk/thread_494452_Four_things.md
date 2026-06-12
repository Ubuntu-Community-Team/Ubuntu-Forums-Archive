---
title: "Four things"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by rukift on 2007-07-06
Ok, let's see:

1.) We recently bought a Linksys Wireless - G Broadband Router, but I  can't get my laptop to connect with it wirelessly. It's not even showing up  in the list of networks I can connect to. Even when I plug my laptop directly into the router, I still get nothing. Then when I plug my laptop into the modem, I get nothing.

2.) This is weird, because I was able to plug into one of the modems in a computer lab at my school sometime before summer. Why did that work, but this didn't?

3.) I was thinking that maybe I could get the wireless router to cooperate if I ran the installation CD in with my laptop. Since it is windows-only, I guessed I would need to get the program/emulator Wine on my computer. Would that increase the odds of this working?

4.) Even if it doesn't, how would I get Wine on here without connecting to the Internet?

---

### Post by jimrz on 2007-07-06
> **rukift said:**
> Ok, let's see:

1.) We recently bought a Linksys Wireless - G Broadband Router, but I  can't get my laptop to connect with it wirelessly. It's not even showing up  in the list of networks I can connect to. Even when I plug my laptop directly into the router, I still get nothing. Then when I plug my laptop into the modem, I get nothing.

2.) This is weird, because I was able to plug into one of the modems in a computer lab at my school sometime before summer. Why did that work, but this didn't?

3.) I was thinking that maybe I could get the wireless router to cooperate if I ran the installation CD in with my laptop. Since it is windows-only, I guessed I would need to get the program/emulator Wine on my computer. Would that increase the odds of this working?

4.) Even if it doesn't, how would I get Wine on here without connecting to the Internet?

first question is is your laptop showing any other available networks in network-manager? and, if so, are you able to connect to them?

also, check to make sure that your router is broadcasting it's essid. although my router worked fine without broadcasting essid on previous versions, beginning with feist (7.04) network-manager would not see any ap that was not broadcasting, at least for me on two different machines. setting the router to broadcast the essid corrected the problem.

---

### Post by pbaumgar on 2007-07-06
On the command line..........

what does:

$lspci

show you?

what does:

$iwconfig

show you?

---

### Post by rukift on 2007-07-06
> **jimrz said:**
> first question is is your laptop showing any other available networks in network-manager? and, if so, are you able to connect to them?

also, check to make sure that your router is broadcasting it's essid. although my router worked fine without broadcasting essid on previous versions, beginning with feist (7.04) network-manager would not see any ap that was not broadcasting, at least for me on two different machines. setting the router to broadcast the essid corrected the problem.

I am using version 6.10, but should I still try that?

I don't see any other networks. Once in a while I will pick up a network connection, but the connection is too weak for me to get online.

---

### Post by candtalan on 2007-07-06
> **rukift said:**
> I am using version 6.10, but should I still try that?

I don't see any other networks. Once in a while I will pick up a network connection, but the connection is too weak for me to get online.

IIRC a feature of 7.04 is that it has improved handling of wireless use - it might be worth thinking about.

---

### Post by jimrz on 2007-07-07
> **rukift said:**
> I am using version 6.10, but should I still try that?

I don't see any other networks. Once in a while I will pick up a network connection, but the connection is too weak for me to get online.

try it. if that does not do it. the issue may not be network-manager. what wireless card (make/model/chipset) are you trying to use?

---

### Post by rukift on 2007-07-17
> **pbaumgar said:**
> On the command line..........

what does:

$lspci

show you?

what does:

$iwconfig

show you?

Sorry it took so long to reply. I have no idea what this means, but...:

rukift@rukift-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
rukift@rukift-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

rukift@rukift-laptop:~$

---

### Post by ugm6hr on 2007-07-17
This is probably the problem:
```
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

One of these will hopefully help:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

With regard to running the setup software... don't bother. It's not necessary with most routers (inc my Linksys one) - it is designed to automatically set up a wifi connection with security.  But you can do that manually with minimal effort anyway.  Have you got an ethernet cable?  If so - plug in and go to url 192.168.1.1 (or whatever the setup page is for the router) and edit the settings.  But it's not necessary to get connected to the router anyway.

---

