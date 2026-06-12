---
title: "No Wireless"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by DoocesWild on 2007-11-09
I'm trying to run off the live disc of ubuntu to see if I like it, but I can't get connected to my wireless network.  I've got a Gateway laptop that was pre-loaded with Vista.  I saw some guide on here on how to troubleshoot this, but I need more basic guides.  For example, I have no idea how to even access the command prompt or anything. 

I'd say I'm pretty good with windows, but having no experience with ubuntu, I need someone to give me some layman's help on 1) how to find the correct driver and 2) how to install it.


This is all assuming that I don't have the correct driver.  I don't see my wireless network in the list, and I can't manually connect to it by entering all of the information.  Sound works fine, and the video I think looks fine (I think it's at 1024*768 though).

Would love all help.  Thanks!

edit: well, found that it IS at 1280*1024 right out of the box.  Just need my wireless working now!

Also my built in wireless is Broadcom

---

### Post by Griffiss on 2007-11-09
you type commands into the terminal by going to Applications=>Accessories=>Terminal.

type the following commands and post their outputs on here:

lspci (lists your pci devices)

iwconfig (gives config settings of your wireless)

lshw -C network (will give you details and status of network hardware)

This'll give people information which they may be able to help you with.

Do you have access to the internet via a wired connection on the computer you're trying to get wireless to work for?

---

### Post by DoocesWild on 2007-11-09
> **Griffiss said:**
> you type commands into the terminal by going to Applications=>Accessories=>Terminal.

type the following commands and post their outputs on here:

lspci (lists your pci devices)

iwconfig (gives config settings of your wireless)

lshw -C network (will give you details and status of network hardware)

This'll give people information which they may be able to help you with.

Do you have access to the internet via a wired connection on the computer you're trying to get wireless to work for?


Yes, I can plug it in.  However, I'd much rather not have to, but for troubleshooting purposes, I do.

Here are my logs:
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)



ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:bb:5d:8b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:25:07:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g 
```

---

### Post by Griffiss on 2007-11-09
Have you tried this?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28BCM94311MCG%29#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28BCM94311MCG%29#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6)

---

### Post by DoocesWild on 2007-11-09
> **Griffiss said:**
> Have you tried this?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28BCM94311MCG%29#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28BCM94311MCG%29#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6)

No I haven't.  I searched for "Gateway" and it's not on there.  Should I continue?

edit: guess it's the same chip though, should work.  Is there an easy install guide?

---

### Post by Pumalite on 2007-11-09
Here are more links for you to peruse:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by Griffiss on 2007-11-09
For the link i gave you, there's no need to search for 'Gateway'. The instructions are specifically for your type of wireless card. In the testimonials on that page, someone with your card (Broadcom Corporation BCM94311MCG) says that they have used this method successfully using the driver from [here]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&SystemID=XPS_M1210&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=3&catid=5&impid=-1&formatcnt=1&libid=5&fileid=202136") in step 2

give it a shot and tell us what happens!

---

### Post by DoocesWild on 2007-11-09
> **Griffiss said:**
> For the link i gave you, there's no need to search for 'Gateway'. The instructions are specifically for your type of wireless card. In the testimonials on that page, someone with your card (Broadcom Corporation BCM94311MCG) says that they have used this method successfully using the driver from [here]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&SystemID=XPS_M1210&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=3&catid=5&impid=-1&formatcnt=1&libid=5&fileid=202136") in step 2

give it a shot and tell us what happens!

Appreciate it.  When I get home tonight I'll give it a shot.  Being that it's the exact same card I'd assume there will be no problems.  That is, if I can get it installed :)

---

### Post by DoocesWild on 2007-11-16
In case anyone has this same issue, all I did to fix it was actually install Ubuntu.  When I was running it off the live disc, I couldn't get it to work with any of the suggestions above, but when I wiped windows off my HD and installed ubuntu, immediately it recognized that I didn't have a driver for it, I plugged in my machine with a good ol' cat5 and it found the drivers.  I entered in my key and it connected right away.

---

