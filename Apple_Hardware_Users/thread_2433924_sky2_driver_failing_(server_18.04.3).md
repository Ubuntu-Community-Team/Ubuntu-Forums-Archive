---
title: "sky2 driver failing (server 18.04.3)"
date: 2019-12-27
forum: Apple Hardware Users
---

### Post by djsmirk on 2019-12-27
Hello,

I've just installed Server 18.03.3 onto a Macmini2,1 and having terrible wired network performance.  Extreme packet loss.  
I suspect the NIC driver (sky2) is having timeout issues.  This seems to be the normal behaviour of this driver based on Google searches
I unfortunately do not see any failures/errors about the NIC in dmesg or /var/log/syslog


Linux downloadserver 4.15.0-72-generic #81-Ubuntu SMP Tue Nov 26 12:20:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
	Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053
	Physical Slot: 0
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 256 bytes
	Interrupt: pin A routed to IRQ 26
	Region 0: Memory at d0200000 (64-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at 1000 [size=256]
	Expansion ROM at d0220000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
		Product Name: Marvell Yukon 88E8053 Gigabit Ethernet Controller
		Read-only fields:
			[PN] Part number: Yukon 88E8053
			[EC] Engineering changes: Rev. 2.2
			[MN] Manufacture ID: 4d 61 72 76 65 6c 6c
			[SN] Serial number: AbCdEfG334455
			[CP] Extended capability: 01 10 cc 03
			[RV] Reserved: checksum good, 9 byte(s) reserved
		Read/write fields:
			[VE] Vendor specific: 00
			[RW] Read-write area: 116 byte(s) free
		End
	Capabilities: [5c] MSI: Enable+ Count=1/2 Maskable- 64bit+
		Address: 00000000fee01004  Data: 4027
	Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 2048 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Exit Latency L0s <256ns, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		AERCap:	First Error Pointer: 1f, GenCap- CGenEn- ChkCap- ChkEn-
	Kernel driver in use: sky2
	Kernel modules: sky2

Settings for enp1s0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Advertised FEC modes: Not reported
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: yes

Dec 27 23:37:44 downloadserver kernel: [    1.933232] sky2: driver version 1.30
Dec 27 23:37:44 downloadserver kernel: [    1.935299] sky2 0000:01:00.0: Yukon-2 EC chip revision 2
Dec 27 23:37:44 downloadserver kernel: [    1.938132] sky2 0000:01:00.0 eth0: addr XX:XX:XX:XX:XX
Dec 27 23:37:44 downloadserver kernel: [    2.005757] sky2 0000:01:00.0 enp1s0: renamed from eth0
Dec 27 23:37:44 downloadserver kernel: [    7.283049] sky2 0000:01:00.0 enp1s0: enabling interface
Dec 27 23:37:47 downloadserver kernel: [   10.200548] sky2 0000:01:00.0 enp1s0: Link is up at 1000 Mbps, full duplex, flow control both

From another machine on my network, I sent continuous pings to the macmini:

--- downloadserver ping statistics ---
**2518 packets transmitted, 780 packets received, 69.0% packet loss**
round-trip min/avg/max/stddev = 0.700/3.282/95.733/5.093 ms

```
How can I fix this??

---

### Post by wildmanne39 on 2019-12-27
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by praseodym on 2019-12-28
Please show
```

ifconfig -a
```

---

### Post by djsmirk on 2019-12-28
```
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.249  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::216:cbff:fead:da71  prefixlen 64  scopeid 0x20<link>
        ether 00:16:cb:ad:da:71  txqueuelen 1000  (Ethernet)
        RX packets 150923  bytes 22733188 (22.7 MB)
        RX errors 0  dropped 7318  overruns 0  frame 0
        TX packets 9610  bytes 1083506 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 246  bytes 33582 (33.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 246  bytes 33582 (33.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wls1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:1c:b3:b1:f3:fe  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

### Post by djsmirk on 2019-12-28
Just in case:

```
Ring parameters for enp1s0:
Pre-set maximums:
RX:		168
RX Mini:	0
RX Jumbo:	0
TX:		1024
Current hardware settings:
RX:		168
RX Mini:	0
RX Jumbo:	0
TX:		1024
```

I disabled offloading as a test, but it didnt help

```
Features for enp1s0:
rx-checksumming: off
tx-checksumming: off
	tx-checksum-ipv4: off
	tx-checksum-ip-generic: off [fixed]
	tx-checksum-ipv6: off [fixed]
	tx-checksum-fcoe-crc: off [fixed]
	tx-checksum-sctp: off [fixed]
scatter-gather: on
	tx-scatter-gather: on
	tx-scatter-gather-fraglist: off [fixed]
tcp-segmentation-offload: off
	tx-tcp-segmentation: off [requested on]
	tx-tcp-ecn-segmentation: off [fixed]
	tx-tcp-mangleid-segmentation: off
	tx-tcp6-segmentation: off [fixed]
udp-fragmentation-offload: off
generic-segmentation-offload: on
generic-receive-offload: on
large-receive-offload: off [fixed]
rx-vlan-offload: on
tx-vlan-offload: on
ntuple-filters: off [fixed]
receive-hashing: off [fixed]
highdma: on [fixed]
rx-vlan-filter: off [fixed]
vlan-challenged: off [fixed]
tx-lockless: off [fixed]
netns-local: off [fixed]
tx-gso-robust: off [fixed]
tx-fcoe-segmentation: off [fixed]
tx-gre-segmentation: off [fixed]
tx-gre-csum-segmentation: off [fixed]
tx-ipxip4-segmentation: off [fixed]
tx-ipxip6-segmentation: off [fixed]
tx-udp_tnl-segmentation: off [fixed]
tx-udp_tnl-csum-segmentation: off [fixed]
tx-gso-partial: off [fixed]
tx-sctp-segmentation: off [fixed]
tx-esp-segmentation: off [fixed]
fcoe-mtu: off [fixed]
tx-nocache-copy: off
loopback: off [fixed]
rx-fcs: off [fixed]
rx-all: off [fixed]
tx-vlan-stag-hw-insert: off [fixed]
rx-vlan-stag-hw-parse: off [fixed]
rx-vlan-stag-filter: off [fixed]
l2-fwd-offload: off [fixed]
hw-tc-offload: off [fixed]
esp-hw-offload: off [fixed]
esp-tx-csum-hw-offload: off [fixed]
rx-udp_tunnel-port-offload: off [fixed]
```

---

### Post by praseodym on 2019-12-28
```
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu [COLOR="#FF0000"]1500[/COLOR]
        inet 192.168.1.249  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::216:cbff:fead:da71  prefixlen 64  scopeid 0x20<link>
        ether 00:16:cb:ad:da:71  txqueuelen 1000  (Ethernet)
        RX packets 150923  bytes 22733188 (22.7 MB)
        RX errors 0  dropped [COLOR="#FF0000"]7318[/COLOR]  overruns 0  frame 0
        TX packets 9610  bytes 1083506 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  
```
Try setting the mtu to 1492
```

sudo ifconfig enp1s0 mtu 1492
```
and restart the network

---

### Post by djsmirk on 2019-12-28
There were 2 things that I did that seemed to really help:

1 - Fully disabling IPv6
2 - Dropping MTU to 1492

I had noticed that with IPv6 enabled (even only with link-local), RX-DRP would increase steadily, even with me logged in at "console" and not over SSH.  This would happen even with the MTU at 1492.

```
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1492
        inet 192.168.1.249  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 00:16:cb:ad:da:71  txqueuelen 1000  (Ethernet)
        RX packets 1928  bytes 369241 (369.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1702  bytes 298035 (298.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

```

Its not perfect, but its certainly better than what it was

```
--- downloadserver ping statistics ---
145 packets transmitted, 143 packets received, 1.4% packet loss
round-trip min/avg/max/stddev = 0.758/2.653/11.671/1.554 ms

```

---

### Post by djsmirk on 2019-12-28
Err maybe not

```
--- downloadserver ping statistics ---
157 packets transmitted, 99 packets received, 36.9% packet loss
round-trip min/avg/max/stddev = 0.740/2.069/4.670/1.298 ms
```

I'll keep an eye on this.

---

### Post by djsmirk on 2019-12-29
This is getting worse by the day.  I'm giving up and going back to OSX :(

---

