---
title: "No WIFI on MacBook Pro running Ubuntu 18.04 (bionic) with Broadcom"
date: 2019-01-15
forum: Apple Hardware Users
---

### Post by bertil2 on 2019-01-15
I recently installed Xubuntu on my old MacBook pro (2010 I believe). The internet has gone back on forth between working and not. Curently I can't get it to work. I've done this so far:
[LIST]
[*]The general networking guide here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
[*]The Broadcom specific guide here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)
[*]Made sure the Broadcom Corporation: BCM4322 802.11a/b/g/n wireless LAN Controller was selected in Additional Drivers
[*]Downloading bcmwl-kernel-source from [http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu3_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu3_amd64.deb), and then ```
sudo dpkg -i bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu3_amd64.deb 
```. This didn't work, bug report can be found here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1811844](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1811844)
[*]Running
[/LIST]
```
 
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install linux-firmware-nonfree b43-fwcutter firmware-b43-installer

```
**Network information**
```


$ sudo lshw -C Network  *-network                 
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: f0:b4:79:21:69:8c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d3200000-d3203fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: 10:9a:dd:54:78:99
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5764m-v3.38 ip=10.2.9.145 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:27 memory:d3100000-d310ffff


$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Limited BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)



```

---

### Post by chili555 on 2019-01-15
I suggest that you try this instead: [https://packages.ubuntu.com/bionic/bcmwl-kernel-source](https://packages.ubuntu.com/bionic/bcmwl-kernel-source)

That is, 6.30.223.271+bdcom-0ubuntu**4**

---

### Post by bertil2 on 2019-01-19
Thanks for getting back! I'm not very experienced with Linux. What exactly should I do? I tried running > $ sudo apt-get purge bcmwl-kernel-source, and then manually downloading+installing in the Software app, using the link you provided. That did not work. Weirdly, yesterday the wifi suddenly worked, and now it is back to not working again.

---

### Post by chili555 on 2019-01-19
What does this tell us?```
dmesg | grep wl
```dmesg is the somewhat abbreviated kernel message log and we want to see any entries having 'wl' in the text. wl is the driver for your device.

The intermitant nature of this suggests a hardware fault.

---

### Post by praseodym on 2019-01-20
Did you deactivate SecureBoot? This driver is not signed...

---

### Post by howefield on 2019-01-20
Moved to the "*Apple Hardware Users*" forum.

---

### Post by bertil2 on 2019-01-30
Thanks! Here is the output of dmesg | grep wl. In regards to your point about hardware failure, the wifi works fine when I boot it with macOS, if that matters at all.

```
bertil@bertil-MacBookPro:~$ dmesg | grep wl
[    7.375370] wl: loading out-of-tree module taints kernel.
[    7.375374] wl: module license 'MIXED/Proprietary' taints kernel.
[    7.383872] wl: module verification failed: signature and/or required key missing - tainting kernel
[    7.475374] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    7.805472] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   10.208997] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   10.309428] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   71.044087] ERROR @wl_notify_scan_status : 
[   71.044087] wlp2s0 Scan_results error (-22)
[  114.057666] ERROR @wl_notify_scan_status : 
[  114.057674] wlp2s0 Scan_results error (-22)
[  167.084082] ERROR @wl_notify_scan_status : 
[  167.084086] wlp2s0 Scan_results error (-22)

```

---

### Post by chili555 on 2019-01-30
Very interesting. Your 14e4:432b device is tricky. The forums are filled with complaints about this exact symptom:> [   71.044087] ERROR @wl_notify_scan_status : 
[   71.044087] wlp2s0 [COLOR="#FF0000"]Scan_results error (-22)[/COLOR]
[  114.057666] ERROR @wl_notify_scan_status : 
[  114.057674] wlp2s0 Scan_results error (-22)
[  167.084082] ERROR @wl_notify_scan_status : 
[  167.084086] wlp2s0 Scan_results error (-22)Here is a thread that suggests that an alternative driver is, instead of bcmwl-kernel-source, b43 and firmware: [https://ubuntuforums.org/showthread.php?t=2391053&p=13766002#post13766002](https://ubuntuforums.org/showthread.php?t=2391053&p=13766002#post13766002)

I suggest that you try the same fix:

> Please do:

```
sudo apt purge bcmwl-kernel-source

```Then:
```
sudo apt install firmware-b43-installer
```
Reboot and let us know if that worked

---

### Post by bertil2 on 2019-01-30
This didn't work. It said "firmware-b43-installer is already the newest version (1:019-3).". 

Btw, I then went in to Additional Drivers to see if I could select the driver. It wasn't there, so I tried selecting the Broadcom Driver, which also didn't work. I have then reselcted "Do not use this driver" and restarted. Just in case this reinstalls the old Broadcom driver or anything like that. Sorry for being a noob, and thanks again.

EDIT: Should I try following your instructions here? [https://ubuntuforums.org/showthread.php?t=2346826&highlight=wlp2s0+Scan_results+error+%28-22%29](https://ubuntuforums.org/showthread.php?t=2346826&highlight=wlp2s0+Scan_results+error+%28-22%29)
I.E.:
> [COLOR=#000000][INDENT]Gakkk! Something is, obviously, still wrong here. Let's dig deeper:
```

lsmod | grep -e b43 -e wl
sudo dpkg -s broadcom-sta-dkms

```
If the latter is installed, please purge it:
```

sudo apt-get purge broadcom-sta-dkms

```
Reboot and show me:
```

iwconfig
sudo modprobe b43 && dmesg | grep b43

```[/INDENT]
[/COLOR]

---

### Post by chili555 on 2019-01-30
'Additional Drivers' is, exactly, bcmwl-kernel-source which is what we are trying *NOT* to use. Please ignore it until we see if b43 and firmware are going to work.

Let's see what is and is not going on here:```
lsmod | grep -e wl -e b43
dmesg | grep -e wl -e b43
```

---

### Post by praseodym on 2019-01-30
Did you try deactivating SecureBoot with the STA driver?

> ```
[    7.383872] wl: module verification failed: signature and/or required key missing - tainting kernel
```

---

### Post by bertil2 on 2019-01-30
> **chili555 said:**
> 'Additional Drivers' is, exactly, bcmwl-kernel-source which is what we are trying *NOT* to use. Please ignore it until we see if b43 and firmware are going to work.

Let's see what is and is not going on here:```
lsmod | grep -e wl -e b43
dmesg | grep -e wl -e b43
```


```

bertil@bertil-MacBookPro:~$ lsmod | grep -e wl -e b43
b43                   413696  0
bcma                   57344  1 b43
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43
bertil@bertil-MacBookPro:~$ dmesg | grep -e wl -e b43
[    0.000000] BRK [0x62b43000, 0x62b43fff] PGTABLE
[    8.195270] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[    8.249235] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[    8.249257] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   10.970370] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.193766] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   11.676337] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.772305] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Edit: BTW, right now my wifi seems to be working after a couple of reboots. This has happened before though, where it suddenly stops again. I tried running some of the commands from before in case they're differnent now. This was, btw, when I restarted from macOS Recovery, if that matters. Note, the code snippet above was from BEFORE the internet was working, on a previous reboot, and the code bellow is from now that it IS working.

```

bertil@bertil-MacBookPro:~$ lsmod | grep -e wl -e b43
b43                   413696  0
bcma                   57344  1 b43
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43
bertil@bertil-MacBookPro:~$ dmesg | grep -e wl -e b43
[    7.314401] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[    7.356809] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[    7.356832] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   10.000897] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.204771] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   10.660551] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.727063] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.315269] wlan0: authenticate with f8:e9:03:bd:5d:0e
[   23.644395] wlan0: send auth to f8:e9:03:bd:5d:0e (try 1/3)
[   23.852068] wlan0: send auth to f8:e9:03:bd:5d:0e (try 2/3)
[   23.852704] wlan0: authenticated
[   23.856049] wlan0: associate with f8:e9:03:bd:5d:0e (try 1/3)
[   23.857075] wlan0: RX AssocResp from f8:e9:03:bd:5d:0e (capab=0x11 status=0 aid=2)
[   23.857338] wlan0: associated
[   23.878418] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.897543] wlan0: Limiting TX power to 17 (17 - 0) dBm as advertised by f8:e9:03:bd:5d:0e
[  171.628191] wlan0: deauthenticating from f8:e9:03:bd:5d:0e by local choice (Reason: 3=DEAUTH_LEAVING)
[  191.699938] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  202.881202] wlan0: authenticate with f8:e9:03:bd:5d:0e
[  202.924406] wlan0: send auth to f8:e9:03:bd:5d:0e (try 1/3)
[  203.128032] wlan0: send auth to f8:e9:03:bd:5d:0e (try 2/3)
[  203.128485] wlan0: authenticated
[  203.132456] wlan0: associate with f8:e9:03:bd:5d:0e (try 1/3)
[  203.133545] wlan0: RX AssocResp from f8:e9:03:bd:5d:0e (capab=0x11 status=0 aid=2)
[  203.133778] wlan0: associated
[  203.139926] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  203.230461] wlan0: Limiting TX power to 17 (17 - 0) dBm as advertised by f8:e9:03:bd:5d:0e
bertil@bertil-MacBookPro:~$ dmesg | grep wl
[   10.000897] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.660551] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.727063] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.315269] wlan0: authenticate with f8:e9:03:bd:5d:0e
[   23.644395] wlan0: send auth to f8:e9:03:bd:5d:0e (try 1/3)
[   23.852068] wlan0: send auth to f8:e9:03:bd:5d:0e (try 2/3)
[   23.852704] wlan0: authenticated
[   23.856049] wlan0: associate with f8:e9:03:bd:5d:0e (try 1/3)
[   23.857075] wlan0: RX AssocResp from f8:e9:03:bd:5d:0e (capab=0x11 status=0 aid=2)
[   23.857338] wlan0: associated
[   23.878418] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.897543] wlan0: Limiting TX power to 17 (17 - 0) dBm as advertised by f8:e9:03:bd:5d:0e
[  171.628191] wlan0: deauthenticating from f8:e9:03:bd:5d:0e by local choice (Reason: 3=DEAUTH_LEAVING)
[  191.699938] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  202.881202] wlan0: authenticate with f8:e9:03:bd:5d:0e
[  202.924406] wlan0: send auth to f8:e9:03:bd:5d:0e (try 1/3)
[  203.128032] wlan0: send auth to f8:e9:03:bd:5d:0e (try 2/3)
[  203.128485] wlan0: authenticated
[  203.132456] wlan0: associate with f8:e9:03:bd:5d:0e (try 1/3)
[  203.133545] wlan0: RX AssocResp from f8:e9:03:bd:5d:0e (capab=0x11 status=0 aid=2)
[  203.133778] wlan0: associated
[  203.139926] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  203.230461] wlan0: Limiting TX power to 17 (17 - 0) dBm as advertised by f8:e9:03:bd:5d:0e

```

---

### Post by bertil2 on 2019-01-30
> **praseodym said:**
> Did you try deactivating SecureBoot with the STA driver?

No - could you tell me how to do that? I'm new to Linux.

Edit: When I open Startup Security Utility, I only get the option to Turn On Firmware Password, not the Secure Boot and External Boot settings that other people get. I guess I don't have it?

---

### Post by bertil2 on 2019-02-05
Status now is that it stopped working again. Since it suddenly worked the other day it hasn't worked at all.

---

### Post by chili555 on 2019-02-06
Is the driver loaded?```
lsmod | grep -e wl -e b43
```Is the airplane mode switch set to enable or disable the wireless?```
rfkill list all
```Are there any clues in the logs?```
dmesg | grep -e b43 -e wl
```

---

### Post by bertil2 on 2019-02-09
Here's the output from those:

```
bertil@bertil-MacBookPro:~$ lsmod | grep -e wl -e b43
b43                   413696  0
bcma                   57344  1 b43
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43
bertil@bertil-MacBookPro:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bertil@bertil-MacBookPro:~$ dmesg | grep -e b43 -e wl
[    9.359634] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[    9.404031] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[    9.404054] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   12.160860] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.372243] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   12.852363] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.922681] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Edit: I tried running the last command agin today, and got a new line. Wifi still not working. Looks like this:
```

bertil@bertil-MacBookPro:~$ dmesg | grep -e b43 -e wl
[    7.840606] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[    7.892813] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[    7.892836] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[    8.228812] Modules linked in: joydev arc4 snd_hda_intel coretemp b43 snd_hda_codec snd_hda_core applesmc(+) input_polldev snd_hwdep kvm_intel bcma snd_pcm kvm irqbypass mac80211 snd_seq_midi snd_seq_midi_event snd_rawmidi cfg80211 snd_seq snd_seq_device snd_timer btusb uvcvideo btrtl btbcm videobuf2_vmalloc videobuf2_memops btintel videobuf2_v4l2 bluetooth videobuf2_core ecdh_generic snd bcm5974 videodev input_leds media shpchp soundcore acpi_als kfifo_buf industrialio sbs sbshc mac_hid apple_bl sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic uas usb_storage hid_apple hid_appleir usbhid hid nouveau mxm_wmi wmi i2c_algo_bit ttm drm_kms_helper firewire_ohci syscopyarea sysfillrect tg3 sysimgblt fb_sys_fops ptp drm pps_core firewire_core crc_itu_t ahci ssb libahci video
[   12.000868] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.204201] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   12.676369] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.923587] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by bertil2 on 2019-02-18
Anything I'm able to do from here?

---

