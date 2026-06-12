---
title: "Intermittent wifi"
date: 2017-07-25
forum: Apple Hardware Users
---

### Post by deathstar2 on 2017-07-25
Hi guys, 

I have managed to install win 10,  Sierra and ubuntu 16.04 on my mac. after much mucking around all seems to work great on all platforms except my wifi is intermittent. At time sit stays good for hours and at other times it's every 2 F&%$en minutes.


I have installed the b43 driver package and everything worked fine. I used the wifi connection for a couple of hours, downloaded an update and only noticed an issue after the update. updated via a terminal.


I have read a number of threads and have tried the wcid network manager which for some reason didn't work well for me. probably my fault. I have also tried disabling the IPV6 support just for that connection and that didn't help.

I am hesitant to just start modifying config files willy nilly etc too much as i don't know what im doing.


Anyone out there can walk me through my issue?


BenginM?

---

### Post by deathstar2 on 2017-07-25
smitty@smitty-MacBookPro:~$ lspci -vvnn | grep -A 9 Network
04:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00ef]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c1900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma

---

### Post by deathstar2 on 2017-07-25
[http://paste.ubuntu.com/25167879/](http://paste.ubuntu.com/25167879/)

---

