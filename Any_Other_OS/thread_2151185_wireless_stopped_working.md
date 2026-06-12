---
title: "wireless stopped working?"
date: 2013-06-03
forum: Any Other OS
---

### Post by qwertyjjj on 2013-06-03
not sure why but my wireless seems to have stopped working:

```
 $ inxi -Fx
System:    Host: spain Kernel: 3.5.0-17-generic i686 (32 bit, gcc: 4.7.2) Desktop: Gnome Distro: Linux Mint 14 Nadia
Machine:   System: LENOVO product: 4236PA8 version: ThinkPad T420
           Mobo: LENOVO model: 4236PA8 Bios: LENOVO version: 83ET67WW (1.37 ) date: 11/28/2011
CPU:       Dual core Intel Core i5-2520M CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9968.08 
           Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz 3: 2501.00 MHz 4: 2501.00 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.13.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1600x900@60.0hz 
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile x86/MMX/SSE2 GLX Version: 3.0 Mesa 9.0.3 Direct Rendering: Yes
Audio:     Card: Intel 6 Series/C200 Series Chipset Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture ver: 1.0.25
Network:   Card-1: Intel Centrino Ultimate-N 6300 driver: iwlwifi ver: in-tree: bus-ID: 03:00.0
           IF: wlan1 state: down mac: 00:24:d7:e7:d5:20
           Card-2: Intel 82579LM Gigabit Network Connection driver: e1000e ver: 2.0.0-k port: 5080 bus-ID: 00:19.0
           IF: eth3 state: up speed: 1000 Mbps duplex: full mac: 00:21:cc:6a:17:11
Drives:    HDD Total Size: 336.1GB (2.5% used) 1: id: /dev/sda model: ST9320423AS size: 320.1GB 
           2: USB id: /dev/sdb model: Cruzer_Blade size: 16.0GB 
Partition: ID: / size: 15G used: 7.9G (57%) fs: ext4 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 43.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: 3249 
Info:      Processes: 153 Uptime: 5 min Memory: 390.0/3923.5MB Runlevel: 2 Gcc sys: 4.7.2 Client: Shell inxi: 1.8.4

 $ lspci -vv -s 03:00.0
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
	Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at f2400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

~ $ lsmod | grep iwlwifiw
 $ sudo modprobe iwlwifi

 $ lsmod | grep iwlwifiw
 $ sudo rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
1: tpacpi_wwan_sw: Wireless WAN
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
 $     sudo rfkill unblock all
 $ sudo rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_wwan_sw: Wireless WAN
	Soft blocked: no
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

 $ sudo ifconfig wlan0 up
[sudo] password for jason: 
wlan0: ERROR while getting interface flags: No such device

---

### Post by Perfect Storm on 2013-06-04
**Thread moved to Other OS/Distro Support.**

---

