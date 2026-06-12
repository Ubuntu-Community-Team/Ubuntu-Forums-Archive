---
title: "[debian] MacMini 2010 BCM4321 WiFi card shows no available networks"
date: 2019-05-24
forum: Apple Hardware Users
---

### Post by earlofpudding on 2019-05-24
Greetings,

I'm on this forum even tho I use Debian 9.9 (with 4.9.0-9-amd64 kernel) on my server. I hope you don't mind.

Situation:
I own a MacMini 2010 (the older one without unibody aluminum chassis) with a Broadcom BCM4321 WiFi card:

```
03:00.0 Network controller [0280]: Broadcom Limited BCM4321 802.11a/b/g/n [14e4:4328] (rev 05)
        Subsystem: Apple Inc. AirPort Extreme [106b:0090]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at d3200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [d0] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 0.000W
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <4us, L1 <64us
                        ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
                LnkCtl: ASPM L1 Enabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO+ CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 0e, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [13c v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [160 v1] Device Serial Number b8-6e-b0-ff-ff-f6-00-26
        Capabilities: [16c v1] Power Budgeting <?>
        Kernel driver in use: wl
        Kernel modules: ssb, wl
```

I installed the broadcom-sta-dkms drivers for my wifi card and I connected myself to a WiFi network using wpa_supplicant and ifupdown successfully. 
Then I tried to connect to another wifi and at that point I coudn't connect to any wifi anymore and the wifi card can't even detect any wifis anymore:
```
root@macmini:~# iwlist scan
wlan0     No scan results
```

I'm using the broadcom-sta-dkms and the wl module is loaded (conflicting modules like b43 are unloaded):
```
root@macmini:~# lsmod | grep wl
wl                   6443008  0
cfg80211              589824  1 wl
```

With the broadcom-sta-dkms I always get a scan results error when trying to scan for wifis:
```
root@macmini:~# dmesg | grep wl
[    3.902305] wl: loading out-of-tree module taints kernel.
[    3.902311] wl: module license 'MIXED/Proprietary' taints kernel.
[    4.139275] wlan0: Broadcom BCM4328 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    4.142490] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[   15.440105] ERROR @wl_notify_scan_status : 
[   15.440122] wlp3s0 Scan_results error (-22)
[   28.044065] ERROR @wl_notify_scan_status : 
[   28.044087] wlp3s0 Scan_results error (-22)
[   34.732129] ERROR @wl_notify_scan_status : 
[   34.732147] wlp3s0 Scan_results error (-22)
[   39.084164] ERROR @wl_notify_scan_status : 
[   39.084185] wlp3s0 Scan_results error (-22)
[   41.132100] ERROR @wl_notify_scan_status : 
[   41.132119] wlp3s0 Scan_results error (-22)
[   43.180169] ERROR @wl_notify_scan_status : 
[   43.180184] wlp3s0 Scan_results error (-22)
```

I also tried the firmware-b43-installer. The modules are loaded (and conflicting ones are unloaded like wl):
```
root@macmini:~# lsmod  | grep b43
b43                   413696  0
bcma                   53248  1 b43
mac80211              671744  1 b43
cfg80211              589824  2 b43,mac80211
rng_core               16384  1 b43
ssb                    69632  1 b43
mmc_core              147456  2 b43,ssb
```

But I still get no scan results. A good thing is tho that I don't get this scan result error like with the broadcom-sta drivers and scanning for wifis takes much longer than on broadcom-sta (which may be a good sign hopefully).

I did everything according to the official debian documentation/howto and searched in tons of forums but nothing seems to work.
Does anyone have a clue why I can't find any WiFi networks anymore?

Thank you very much in advance!

---

