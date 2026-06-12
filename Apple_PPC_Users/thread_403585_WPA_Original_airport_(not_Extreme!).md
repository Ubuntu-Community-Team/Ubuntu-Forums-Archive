---
title: "WPA Original airport (not Extreme!)"
date: 2007-04-07
forum: Apple PPC Users
---

### Post by georgie on 2007-04-07
Hi all

Trying to get WPA (personal, version 1) working on an Apple PPC TiBook 800Mhz 


The card is an original airport. In OSX I can quite happily connect to my WPA wireless setup

In Fiesty, nm-applet doesn't show any WPA options. I can connect quite happily using WEP, but want to do WPA

knetworkmanager gives me the choice of WPA (enterprise/personal/1/2) - but it silently dies then fails over to the  wired network

Can anyone help? I'll post the entries in syslog in a moment - but just wondered if anyone had any ideas. I can't work out if it's a hardware issue (card won't do WPA - except under OSX) a software issue (haven't setup wireless properly) or maybe a Feisty issue.

here's some info:
___________________
1) Hardware
___________________
#lspci -vv

(snip)
1:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 16, Cache Line Size: 32 bytes
        Region 0: Memory at 80000000 (32-bit, non-prefetchable) [size=512K]

___________________
2) working card
___________________
#iwlist scanning
eth1      Scan completed :
Cell 01 - Address: 00:(removed mac address) xxxxxxxxx
ESSID:"georouter"
___________________
3) modules
___________________

#lsmod | grep air
airport                 7104  0 
orinoco                44948  1 airport
hermes                  8352  2 airport,orinoco

---

### Post by stmiller on 2007-04-17
I've just installed Feisty on my Tibook, which has an airport (original) card. I'm currently investigating. This should be possible....

[http://ubuntuforums.org/showthread.php?t=17009](http://ubuntuforums.org/showthread.php?t=17009)

---

### Post by stmiller on 2007-05-04
After installing the program hwinfo (apt-get install hwinfo) it says that the driver is only capable of WEP.

This might require compiling an orinoco driver from source to enable WPA, if that is even possible. I'll try to investigate more when I have some time.

---

