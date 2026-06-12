---
title: "MacBookPro6,1 wifi unexpected connection loss."
date: 2010-05-17
forum: Apple Hardware Users
---

### Post by lael on 2010-05-17
I've got Ubuntu 10.04 running on my MacBookPro6,1 (2010 17" i7). I am able to connect to a wireless network but get consistent loss of transmission and eventually loss of connection.  I have lots of other devices interacting with this network successfully and even had MacBookPro5,2 (with Ubuntu) on wifi without interruption.

I'm not really sure how I should go about diagnosing and fixing this issue. 

```
iwconfig
...
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:217  Noise level:177
          Rx invalid nwid:0  invalid crypt:2  invalid misc:0
...

```
```

sudo iwconfig
...
eth1      IEEE 802.11abgn  ESSID:"dontmatter"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:11:22:33:44:55   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-43 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3b] (rev 06)
00:1a.7 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b36] (rev 06)
00:1d.7 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b28] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a29] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be2] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
04:00.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW643 PCI Express1394b Controller (PHY/Link) [11c1:5901] (rev 08)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```

I'm pretty sure its this device:
```
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
```

So The wifi device seems to be a Broadcom 4353 (rev 01) right?

I'm currently using the Broadcom STA wireless driver from the 'Hardware Drivers' GUI.  I think that [I read]("https://help.ubuntu.com/community/MacBookPro6-2/Lucid") that this equates to:
```
sudo apt-get install bcmwl-kernel-source
```

The Broadcom STA driver's description is:
```
These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware.
```
**Since I have 4353, does that mean that I'm using the wrong driver? (currently 5.60.48.36+bdcom-0ubuntu3)**

I have even tried "sudo iwconfig eth1 power off" but that has had no effect.
I'd like to understand how to fix this issue *and* use a 802.11n

**How can I go about trying to diagnose, debug and fix this issue?**

---

### Post by bfroemel on 2010-05-17
I can confirm this issue somewhat (on MacBookPro6,2 but regardless of 802.11n): there seems to be routers out there which work fine with the stock OSX driver, but there are a lot of connection losses with Broadcom's STA Linux driver. On the other hand there are routers where the Linux driver works fine too.

Unfortunately, the Broadcom driver is closed source and the open source project around the 802.11n stack is still in its early stages ([http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)).
 
Another alternative may be to try the Windows driver with ndiswrapper.

---

### Post by linuxopjemac on 2010-05-17
try wicd instead of networkmanager

---

### Post by arkepp on 2010-05-17
I have a 6.2 and a Linksys router and I have roughly the same problem. The connection is not dropped, but the laptop seems to constantly cycle through all possible frequencies / channels, at least according to iwconfig.

This leads to very erratic ping response times (from 1ms to 200ms, mostly the latter) and makes even SSH unusable.

I've tried setting everything on the router to fixed values (2.4 GHz vs 5 GHz, channel, channel width, a,b,g,n, only TKIP, only AES... you name it). The other laptops oblige happily, the Broadcom card doesn't seem to care.

I was not able to connect with wicd, it tells me the passphrase is wrong when I try to use wpa_supplicant, I haven't fully understood how WPA works with the STA driver.

I did initially point a finger at Network Manager too... can anyone say with confidence whether it's Network Manager or the driver? E.g. if there was no way for the driver to change the output of iwconfig.

---

### Post by lael on 2010-05-17
> **bfroemel said:**
> 
Unfortunately, the Broadcom driver is closed source and the open source project around the 802.11n stack is still in its early stages ([http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)).

Thanks for the tip on b43, It looks like this device isn't supported, but I'll give it a try. [http://wireless.kernel.org/en/users/Drivers/b43#caveats]("http://wireless.kernel.org/en/users/Drivers/b43#caveats")

> **bfroemel said:**
> 
Another alternative may be to try the Windows driver with ndiswrapper.
What does this look like? Its been a while since I've used ndiswrapper :-)  I've got a feeling that this method will have the best results.

---

### Post by lael on 2010-06-05
The device is clearly not supported by b43.

I ended up giving ndiswrapper a try and that failed.  I downloaded a driver from Dell for the same chipset without any luck:
```
17:49:18 MyHostName loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwl6
17:49:18 MyHostName kernel: [ 2371.189544] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
17:49:18 MyHostName kernel: [ 2371.189550] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
17:49:18 MyHostName kernel: [ 2371.189560] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
17:49:18 MyHostName kernel: [ 2371.189564] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
17:49:18 MyHostName kernel: [ 2371.189567] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
17:49:18 MyHostName kernel: [ 2371.189571] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
17:49:18 MyHostName kernel: [ 2371.189575] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
17:49:18 MyHostName kernel: [ 2371.189579] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
17:49:18 MyHostName kernel: [ 2371.189584] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
17:49:18 MyHostName kernel: [ 2371.189590] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
17:49:18 MyHostName kernel: [ 2371.189594] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
17:49:18 MyHostName kernel: [ 2371.189597] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
17:49:18 MyHostName kernel: [ 2371.189601] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
17:49:18 MyHostName kernel: [ 2371.189606] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
17:49:18 MyHostName kernel: [ 2371.189610] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
17:49:18 MyHostName kernel: [ 2371.189616] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
17:49:18 MyHostName kernel: [ 2371.189620] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
17:49:18 MyHostName kernel: [ 2371.189624] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
17:49:18 MyHostName kernel: [ 2371.189629] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
17:49:18 MyHostName kernel: [ 2371.189632] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
17:49:18 MyHostName kernel: [ 2371.189636] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
17:49:18 MyHostName kernel: [ 2371.189640] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
17:49:18 MyHostName kernel: [ 2371.189647] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
17:49:18 MyHostName kernel: [ 2371.189651] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
17:49:18 MyHostName kernel: [ 2371.189654] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
17:49:18 MyHostName kernel: [ 2371.189662] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
17:49:18 MyHostName kernel: [ 2371.189667] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
17:49:18 MyHostName kernel: [ 2371.189671] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
17:49:18 MyHostName kernel: [ 2371.189675] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
17:49:18 MyHostName kernel: [ 2371.189681] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
17:49:18 MyHostName kernel: [ 2371.189685] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
17:49:18 MyHostName kernel: [ 2371.189688] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
17:49:18 MyHostName kernel: [ 2371.189692] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
17:49:18 MyHostName kernel: [ 2371.189696] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
17:49:18 MyHostName kernel: [ 2371.189698] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwl6'
17:49:18 MyHostName kernel: [ 2371.190326] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
```
I'm guessing I'd have to install Windows and find and verify a driver that works correctly on this hardware before I try to use it with ndiswrapper.  I'd be interested in hearing if anyone has a wireless driver that works with this chipset.

So according to the [Broadcom STA readme]("http://www.broadcom.com/docs/linux_sta/README.txt") my device (4353) is supported.

I'm seeing a lot of roaming to nothing and back again like this in my syslog:
```
16:07:05 MyHostName ntpdate[15518]: adjust time server 91.189.94.4 offset -0.008719 sec
16:07:08 MyHostName NetworkManager: <debug> [1275772028.002072] periodic_update(): Roamed from BSSID 00:12:34:56:78:9A (MySSID) to (none) ((none))
16:07:50 MyHostName NetworkManager: <debug> [1275772070.002029] periodic_update(): Roamed from BSSID (none) ((none)) to 00:12:34:56:78:9A (MySSID)
16:08:08 MyHostName NetworkManager: <debug> [1275772088.007200] periodic_update(): Roamed from BSSID 00:12:34:56:78:9A (MySSID) to (none) ((none))
16:08:20 MyHostName NetworkManager: <debug> [1275772100.008449] periodic_update(): Roamed from BSSID (none) ((none)) to 00:12:34:56:78:9A (MySSID)
16:08:32 MyHostName NetworkManager: <debug> [1275772112.004226] periodic_update(): Roamed from BSSID 00:12:34:56:78:9A (MySSID) to (none) ((none))
16:08:37 MyHostName avahi-daemon[1030]: Invalid query packet.
16:08:37 MyHostName avahi-daemon[1030]: Invalid query packet.
16:08:38 MyHostName NetworkManager: <debug> [1275772118.006654] periodic_update(): Roamed from BSSID (none) ((none)) to 00:12:34:56:78:9A (MySSID)
16:08:38 MyHostName avahi-daemon[1030]: Invalid query packet.
16:08:44 MyHostName NetworkManager: <debug> [1275772124.002645] periodic_update(): Roamed from BSSID 00:12:34:56:78:9A (MySSID) to (none) ((none))
16:09:18 MyHostName wpa_supplicant[1114]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
16:09:18 MyHostName vmnetBridge: Removing interface eth1 index:12
16:09:18 MyHostName NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected
16:09:18 MyHostName NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
16:09:27 MyHostName bluetoothd[1982]: Discovery session 0x7f101d8128c1 with :1.257 activated
16:09:27 MyHostName wpa_supplicant[1114]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
16:09:27 MyHostName NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
16:09:30 MyHostName NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
16:09:34 MyHostName NetworkManager: <info>  (eth1): device state change: 8 -> 3 (reason 11)
16:09:34 MyHostName NetworkManager: <info>  (eth1): deactivating device (reason: 11).
16:09:34 MyHostName NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 15477
```

---

### Post by lael on 2010-06-05
> **linuxopjemac said:**
> try wicd instead of networkmanager

Thank you linuxopjemac I installed wicd & all supporting packages (sudo apt-get install wicd wicd-daemon python-wicd wicd-gtk wicd-curses wicd-cli) and wifi has been connected and working reliably for ~ 1 hr so far whereas before I couldn't go more than 5 minutes.

I am connected with 802.11g but my router is setup to do b/g/n
```
$ sudo iwconfig eth1
eth1      IEEE 802.11abgn  ESSID:"MySSID"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:12:34:56:78:9A   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-48 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

```

So this seems to be an issue with NetworkManager.  Now its time to look for an existing bug in launchpad.

---

### Post by linuxopjemac on 2010-06-06
I don't understand why some people don't follow my advize. Wicd is a far better network manager than networkmanager itself.

---

### Post by sha.goyjo on 2010-06-06
linuxopjemac, wicd is a better network manager, but not everyone wants to replace core system components as a first step. I use it too, but that doesn't mean we should expect everybody to convert instantly! :)

---

### Post by lael on 2010-06-06
I'm glad that I found something that works (wicd), but I'm not 100% happy with the solution yet.

sha.goyjo - You are right, I didn't want to replace network manager as a first step.  

How is wicd at integrating with VPNs?

---

### Post by lael on 2010-06-06
I've added some comments to this bug which seemed to identify the issue:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/484366](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/484366)

---

