---
title: "Can't activate WiMax adapter"
date: 2011-09-01
forum: Any Other OS
---

### Post by majoritywhip on 2011-09-01
I've been trying to do this for a while and I REALLY need to get it done soon. The problem is that there is a soft block on my Intel Centrino Advanced-N + WiMAX 6250 adapter and I can't remove it. All of the examples I've seen have had to do with an acer-wmi driver conflict, but I have an Asus U52F and it's a clean install (10.10).  Here's some terminal outputs of my system:

```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wmx0      no wireless extensions.

wlan1     Ralink STA  ESSID:"*******"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:F2:8F:44:00   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=50/100  Signal level:-75 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.
```

```
rfkill list

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: i2400m-usb:1-1.1:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
```

**rfkill unblock all**, **unblock 1** and **unblock wimax** don't do anything. I even tried to block **Wireless LAN** and that didn't work. I figured that it worked the same way under Linux as it does in Win, you can't have both on at the same time.

```
dmesg | grep iwl

[   16.617255] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.617258] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   16.617325] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.617332] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.617417] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[   16.627116] iwlagn 0000:02:00.0: device EEPROM VER=0x554, CALIB=0x6
[   16.627133] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.627285] iwlagn 0000:02:00.0: irq 45 for MSI/MSI-X
[   16.629598] iwlagn 0000:02:00.0: loaded firmware version 9.201.4.1 build 24255
[   16.641969] phy0: Selected rate control algorithm 'iwl-agn-rs'
```

```
lsmod

Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  598 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
vmnet                  47468  13 
vmblock                12995  1 
vsock                  43307  0 
vmci                   60490  1 vsock
vmmon                  80183  0 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
rt2800usb              11556  0 
rt2800lib              34112  1 rt2800usb
rt2x00usb              11169  1 rt2800usb
rt2x00lib              33936  3 rt2800usb,rt2800lib,rt2x00usb
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   300109  1 
rt2870sta             446110  1 
iptable_nat             4593  0 
nf_nat                 20067  1 iptable_nat
nf_conntrack_ipv4      13143  3 iptable_nat,nf_nat
nf_conntrack           75238  3 iptable_nat,nf_nat,nf_conntrack_ipv4
crc_ccitt               1699  2 rt2800lib,rt2870sta
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
iptable_mangle          1823  0 
snd_hda_intel          26147  2 
iptable_filter          1778  0 
ip_tables              19171  3 iptable_nat,iptable_mangle,iptable_filter
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
x_tables               24423  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
arc4                    1497  2 
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
iwlagn                215351  0 
snd_seq_midi            5932  0 
i2400m_usb             33380  0 
snd_rawmidi            22207  1 snd_seq_midi
i2400m                110710  1 i2400m_usb
iwlcore               139688  1 iwlagn
snd_seq_midi_event      7291  1 snd_seq_midi
uvcvideo               62411  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
videodev               49359  1 uvcvideo
snd_timer              23850  2 snd_pcm,snd_seq
wimax                  29090  1 i2400m
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
mac80211              269644  5 rt2800lib,rt2x00usb,rt2x00lib,iwlagn,iwlcore
joydev                 11395  0 
snd                    64277  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              167809  4 rt2x00lib,iwlagn,iwlcore,mac80211
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
intel_ips              13252  0 
asus_laptop            16668  0 
sparse_keymap           3837  1 asus_laptop
led_class               3393  2 rt2x00lib,asus_laptop
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
dm_raid45              75026  0 
xor                     4709  1 dm_raid45
btrfs                 506637  0 
zlib_deflate           21866  1 btrfs
crc32c                  3007  1 
libcrc32c               1268  1 btrfs
usbhid                 42030  0 
hid                    84710  1 usbhid
i915                  335073  9 
drm_kms_helper         32836  1 i915
usb_storage            50788  1 
drm                   206198  4 i915,drm_kms_helper
ahci                   22370  4 
atl1c                  34742  0 
libahci                26148  1 ahci
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
output                  2527  1 video
intel_agp              32334  2 i915
```



What could it be? All of the appropriate drivers are there. It shows up as wmx0 in Network Manager.  This has me very perplexed and a frustrated.  Help, please.

---

### Post by fdrake on 2011-09-01
> **majoritywhip said:**
> I've been trying to do this for a while and I REALLY need to get it done soon. The problem is that there is a soft block on my Intel Centrino Advanced-N + WiMAX 6250 adapter and I can't remove it. All of the examples I've seen have had to do with an acer-wmi driver conflict, but I have an Asus U52F and it's a clean install (10.10).  Here's some terminal outputs of my system:
-  -  -  -  -
What could it be? All of the appropriate drivers are there. It shows up as wmx0 in Network Manager.  This has me very perplexed and a frustrated.  Help, please.

what's the result for:
```

sudo ifconfig wmx0 up

```
do you have a dual boot with win? if so try to login in in win and try to toggled wireless off then back on. Maybe the firmware has rewritten something accidentaly. You can try also to unplug the power cable for like 30sec and power back on the pc. 
check post #10 in here [http://ubuntuforums.org/showthread.php?t=1529993](http://ubuntuforums.org/showthread.php?t=1529993)


if that does not work click on my link-signature (networking) and download the script. Post here the results file(as attachment). Note : turn off  wlan0 and wlan1 before running the script, please:
```

sudo ifconfig wlan0 down
sudo ifconfig wlan1 down 

```
to reset just replace with "up"

---

### Post by majoritywhip on 2011-09-01
Thanks for getting back to me.

1st - It is a dual boot but wmx0 didn't work when it was a single boot.  I installed W7 recently for a variety of reasons and accessing my Clear account was one of them.

2nd - There is a hardware switch and it has been turned off/on repeatedly. Also, I've read that this would only effect a Hard Block issue, not Soft.

3rd - It's a laptop and it gets powered down numerous times a day

4th - I've already read [this post]("http://ubuntuforums.org/showthread.php?t=1529993") and installed backports-maverick-generic. I don't have a **ath5k module** on my system.


```

sudo ifconfig wmx0 up
[sudo] password for *********:

ifconfig wmx0
 
wmx0      Link encap:Ethernet  HWaddr 64:d4:da:13:8e:66  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

It's still disabled in Network Manager.

**sudo ifconfig wlan0 down** does nothing at all. Neither does **wlan1 down**(It's an external so I just unplugged it). That being said, I'm not sure how to run your script without taking down wlan0. Can I just execute **rfkill block 0** and put a soft block on it?

---

### Post by fdrake on 2011-09-01
> **majoritywhip said:**
> Thanks for getting back to me.

1st - It is a dual boot but wmx0 didn't work when it was a single boot.  I installed W7 recently for a variety of reasons and accessing my Clear account was one of them.

2nd - There is a hardware switch and it has been turned off/on repeatedly. Also, I've read that this would only effect a Hard Block issue, not Soft.

3rd - It's a laptop and it gets powered down numerous times a day

4th - I've already read [this post]("http://ubuntuforums.org/showthread.php?t=1529993") and installed backports-maverick-generic. I don't have a **ath5k module** on my system.


```

sudo ifconfig wmx0 up
[sudo] password for *********:

ifconfig wmx0
 
wmx0      Link encap:Ethernet  HWaddr 64:d4:da:13:8e:66  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

It's still disabled in Network Manager.

**sudo ifconfig wlan0 down** does nothing at all. Neither does **wlan1 down**(It's an external so I just unplugged it). That being said, I'm not sure how to run your script without taking down wlan0. Can I just execute **rfkill block 0** and put a soft block on it?

it's ok you don't need to do that. i just did not want to read the scan for wlan0/1 but if tha's the case, it's ok. just run it and post the results.

---

### Post by majoritywhip on 2011-09-01
OK.  The results file is HUGE (19MB). Probably because I couldn't put my wlan0 down.  I'm going to past the results that I see in the other examples.

```

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++System-Info+++++++++++++++++++++++++++++++++++++++++++++++
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=10
DISTRIB_CODENAME=julia
DISTRIB_DESCRIPTION="Linux Mint 10 Julia"
Linux mint 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:41:54 UTC 2011 x86_64 GNU/Linux

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++ifconfig+++++++++++++++++++++++++++++++++++++++++++++++++
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:08:7d:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4553 (4.5 KB)  TX bytes:4553 (4.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.159.1  Bcast:172.16.159.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.50.1  Bcast:192.168.50.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:15:70:22:c4  
          inet addr:192.168.5.183  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::223:15ff:fe70:22c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2525214 (2.5 MB)  TX bytes:516595 (516.5 KB)

wmx0      Link encap:Ethernet  HWaddr 64:d4:da:13:8e:66  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++iwconfig+++++++++++++++++++++++++++++++++++++++++++++++++
wlan0     IEEE 802.11abg  ESSID:"attwifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:CA:5F:EB:F0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++iwlist-scan++++++++++++++++++++++++++++++++++++++++++++++

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++/pro/net/wireless+++++++++++++++++++++++++++++++++++++++++++++
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   58.  -52.  -256        0      0      0      0      0        0

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++++nm-tool++++++++++++++++++++++++++++++++++++++++++++++++

NetworkManager Tool

State: connected

- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        64:D4:DA:13:8E:66

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto attwifi] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        00:23:15:70:22:C4

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


*****************************

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        BC:AE:C5:08:7D:36

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++/var/lib/NetworkManager/NetworkManager.state+++++++++++++++++++++++++++++++++

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++/lib/firmware/+++++++++++++++++++++++++++++++++
-rw-r--r--  1 root root  335056 2010-12-13 12:01 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-12-13 12:01 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-13 12:01 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-13 12:01 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-13 12:01 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  340696 2011-03-03 08:08 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 2010-12-13 12:01 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 2010-12-13 12:01 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 06:20 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 06:20 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2011-02-11 06:17 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-14 08:18 iwlwifi-6050-5.ucode

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lswh+++++++++++++++++++++++++++++++++++++++++++++++++++++
  *-network
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 5f
       serial: 00:23:15:70:22:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-30-generic firmware=9.201.4.1 build 24255 ip=192.168.5.183 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:d1800000-d1801fff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:08:7d:36
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:d0400000-d043ffff ioport:b000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:1.1
       logical name: wmx0
       serial: 64:d4:da:13:8e:66
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lspci++++++++++++++++++++++++++++++++++++++++++++++++++++
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device 1820
	Physical Slot: 5
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 47
	Region 0: Memory at d0400000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at b000 [size=128]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0f00c  Data: 41a1
	Capabilities: [58] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [6c] Vital Product Data
		Not readable
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP- SDES+ TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP+ Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [180 v1] Device Serial Number ff-08-7d-36-bc-ae-c5-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c
```

Again, thanks for taking your time with this.  Let me know if you need any more information.

---

### Post by fdrake on 2011-09-01
> The results file is HUGE (19MB).
really?! it should not bee more than 300kb? anyway, the part of the log is missing probably was too long for the form.

from > 
wlan0     IEEE 802.11abg  ESSID:"attwifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:CA:5F:EB:F0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
         [COLOR="Red"] Power Management:off[/COLOR]

can you try:
```
sudo ip link set wlan0 up
```
> 
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:1.1
       logical name: wmx0
       serial: 64:d4:da:13:8e:66
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no


are you using also a usb adapter? so wmxo is not your WiMAX 6250 adapter, but indeed is the wlan0.
> 
  *-network
       description: Wireless interface
       [COLOR="Red"]product: Centrino Advanced-N + WiMAX 6250[/COLOR]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       [COLOR="Red"]**logical name: wlan0**[/COLOR]
       version: 5f
       serial: 00:23:15:70:22:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-30-generic firmware=9.201.4.1 build 24255 ip=192.168.5.183 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:d1800000-d1801fff



---

### Post by majoritywhip on 2011-09-01
The 6250 is an integrated chip.  It handles both AGN and WiMax. It is not listed under **lsusb**, rather **lspci**. So it comes up as both wlan0 and wmx0. This is why I thought disabling one would allow me to remove the soft block for the other.  Not so.

I ran **sudo ip link set wlan0 up**.  What am I looking for now?

---

### Post by fdrake on 2011-09-01
> **majoritywhip said:**
> The 6250 is an integrated chip.  It handles both AGN and WiMax. It is not listed under **lsusb**, rather **lspci**. So it comes up as both wlan0 and wmx0. This is why I thought disabling one would allow me to remove the soft block for the other.  Not so.

I ran **sudo ip link set wlan0 up**.  What am I looking for now?

have you tried to remove the driver for wmx0 first(i2400m) and  then remove the soft block? (you may need a reboot)

---

### Post by majoritywhip on 2011-09-01
> **fdrake said:**
> have you tried to remove the driver for wmx0 first(i2400m) and  then remove the soft block? (you may need a reboot)

**sudo rmmod i2400m_usb** removes wmx0, not wlan0

---

### Post by fdrake on 2011-09-02
[http://lists.linuxwimax.org/pipermail/wimax/2011-April/001268.html](http://lists.linuxwimax.org/pipermail/wimax/2011-April/001268.html)
i know you already posted in this site, but wanted to double check if you already have seen this post. He is using a iwlagn to control the wimax scan.


I don't think that it matters really which driver you block infact both of them are used with wimax. You can try to blacklist one at the time and reboot to see if you can unblock the device. What I feel is a conflict between drivers. 
```

sudo cat >> /etc/modprobe.d/blacklist
blacklist i2400m <press-enter>
<ctrl+D>

```

to reset just do :
```

less /etc/modprobe.d/blacklist | sudo sed s/"blacklist i2400m"/""/ > log
sudo less log > /etc/modprobe.d/blacklist; sudo rm log

```

if that does not do it, can you post your error logs:
```

dmesg | less > errors.txt
less /var/log/syslog >> errors.txt

```
maybe they can tell us a little bit more.

---

### Post by Perfect Storm on 2011-09-02
Moved to Other OS/Distro Talk.

---

### Post by tripflex on 2012-07-02
Did you ever get this figured out?  I'm having the same EXACT problem and have been for the past week without any luck.  I've gone as far as rebuilding the modules from both compat and kernel.org git and still nothing.

I setup a VM under windows and installed the drivers and can use WiMax without problems.  Stupid WiFi/WiMax integrated devices!!! AHHHHGHGHGH!!

---

