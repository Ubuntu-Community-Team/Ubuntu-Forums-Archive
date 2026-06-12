---
title: "Help with Apple USB Ethernet Adaptor and 14.04 LTS"
date: 2016-09-13
forum: Apple Hardware Users
---

### Post by trispembo on 2016-09-13
I'm hoping someone may be able to help troubleshooting an Apple USB Network Adaptor. I can't tell whether it's something I'm doing wrong, or a driver that's playing up/failing. 

On my MacMini 2,1 I have dual boot OS X and Ubuntu 14.04 and am trying to set it up as a linux gateway/router/firewall. So I have two NICs installed (one onboard, one USB). When I boot into OSX both NICs are working fine. 

When I boot into 14.04 the onboard ethernet adapter is working fine. However, I can't seem to get the USB adaptor to work properly. 

It appears in [COLOR=#ff0000]ifconfig[/COLOR], is correctly set up in [COLOR=#ff0000]/etc/network/interfaces[/COLOR][COLOR=#000000],[/COLOR] appears in [COLOR=#FF0000]/etc/udev/rules.d/70[/COLOR][COLOR=#FF0000]-persistent-net.rules [/COLOR][COLOR=#000000]and it[/COLOR][COLOR=#000000] can be successfully pinged from the host machine, [/COLOR][COLOR=#000000]but it just won't pass [/COLOR][COLOR=#000000]traffic. I've flushed iptables and tried as static and dhcp. I've rebooted multiple times. It just won't work.  
[/COLOR]
Do I need to reinstall a driver? Is there something more I should be doing?

Any help would be appreciated.

Edit: I'm beginning to think this has more to do with the network driver than anything.

When I create a lshw.txt report, it has thins info about the interface driver:
driver=asix
firware=ASIX AX 88772 USB 2.0

Is there anyway to reinstall that driver?

---

### Post by trispembo on 2016-09-15
Could one of the mods bump this over to the Networking forum please? I don't think the issue I'm having is Apple specific.

---

### Post by QIII on 2016-09-15
Hello!  

We generally like to keep all questions regarding systems installed on Apple hardware here because there are a great number of people who have a lot of experience working through the specific intricacies of making things work on Apple hardware.

If the "Apple USB Ethernet Adaptor" is actually one built by or for Apple, then this is definitely best left here.

Would you please give specification details of the adapter -- or perhaps a link to the hardware specs?

Cheers!

---

### Post by wildmanne39 on 2016-09-15
I work with wireless issues and if this is your driver asix I have never seen that before in linux and I looked on a linux driver site a few minutes ago and it did not have that driver listed either.

You can post the output of:
```
lspci -nnk | grep -iA2 net
```
that should tell us what driver is loaded if any.

---

### Post by trispembo on 2016-09-15
Ok, here's the results of
```
[SIZE=2]$ lspci -nnk | grep -iA2 net
01:00.0 Ether[COLOR=#ff0000]net[/COLOR] controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ether[COLOR=#ff0000]net[/COLOR] Controller [11ab:4362] (rev 22)
          Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053 [11ab:5321]
          Kernel driver in use: sky2

02:00.0 Ether[COLOR=#ff0000]net[/COLOR] controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless [COLOR=#ff0000]Net[/COLOR]work Adapter (PCI-Express) [168c:001c] (rev 01)
          Subsystem: Apple Inc. AirPort Extreme [106b:0086]
          Kernel driver in use: ath5k[/SIZE]
```

So it doesn't seem to be listed at all.

In the lshw.txt report is has:
```
*-network       
       description: Ethernet interface
       physical id: 1
       logical name: WAN
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Aug-2005 duplex=full firmware=ASIX AX88772A USB 2.0 Ethernet ip=[REMOVED] link=yes multicast=yes port=MII speed=100Mbit/s
```

---

### Post by wildmanne39 on 2016-09-15
Please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by trispembo on 2016-09-15
It is a genuine Apple piece of hardware - model number A1277. Supposedly they use ASIX chips, but that isn't confirmed by looking in the hardware info on OS X. 

In OS X it's listed as:

```
[FONT=Lucida Grande]**Apple USB Ethernet Adapter:**[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Lucida Grande]  Product ID:    0x1402[/FONT]
[FONT=Lucida Grande]  Vendor ID:    0x05ac  (Apple Inc.)[/FONT]
[FONT=Lucida Grande]  Version:     0.01[/FONT]
[FONT=Lucida Grande]  Serial Number:    XXXXXXX[/FONT]
[FONT=Lucida Grande]  Speed:    Up to 480 Mb/sec[/FONT]
[FONT=Lucida Grande]  Manufacturer:    Apple Inc.      [/FONT]
[FONT=Lucida Grande]  Location ID:    0x1a122000 / 10[/FONT]
[FONT=Lucida Grande]  Current Available (mA):    500[/FONT]
[FONT=Lucida Grande]  Current Required (mA):    250[/FONT]
[FONT=Lucida Grande]  BSD Name:    en1[/FONT]

```

---

### Post by trispembo on 2016-09-15
Ok, will do. Thanks!

The fact that it's not a wireless interface, does that make a difference?

---

### Post by wildmanne39 on 2016-09-15
It will still show up.

---

### Post by trispembo on 2016-09-15
> **Wild Man said:**
> Please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks
Ok, here's the results of the wireless script. Thanks for your help.
```
########## wireless info START ##########


Report from: 15 Sep 2016 16:24 AEST +1000


Booted last: 15 Sep 2016 16:18 AEST +1000


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-95-generic #142-Ubuntu SMP Fri Aug 12 17:05:16 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)
    Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053 [11ab:5321]
    Kernel driver in use: sky2


02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:0086]
    Kernel driver in use: ath5k


##### lsusb #############################


Bus 001 Device 005: ID 05ac:1402 Apple, Inc. Ethernet Adapter [A1277]
Bus 001 Device 009: ID 046d:c061 Logitech, Inc. RX1500 Laser Mouse
Bus 001 Device 008: ID 05ac:024f Apple, Inc. 
Bus 001 Device 004: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 003: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A
Bus 001 Device 002: ID 0781:5576 SanDisk Corp. Cruzer Facet
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8240 Apple, Inc. Built-in IR Receiver
Bus 005 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              554291  1 ath5k
cfg80211              417586  3 ath,ath5k,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


auto WAN
iface WAN inet static
    address 192.168.0.2
    netmask 255.255.255.0


auto LAN
iface LAN inet static
    address 192.168.0.25
    netmask 255.255.255.0
    gateway 192.168.0.1
    post-up iptables-restore < /etc/iptables.up.rules


##### ifconfig ##########################


LAN       Link encap:Ethernet  HWaddr <MAC 'LAN' [IF1]>  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'LAN' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3846262 (3.8 MB)  TX bytes:719694 (719.6 KB)
          Interrupt:16 


WAN       Link encap:Ethernet  HWaddr <MAC 'WAN' [IF2]>  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'WAN' [IF2]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:847 (847.0 B)  TX bytes:554 (554.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF3]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


WAN       no wireless extensions.


LAN       no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 LAN
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 LAN
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 LAN
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 WAN


##### resolv.conf #######################


##### network managers ##################


Installed:


    Wicd


Running:


    None found.


##### NetworkManager info ###############


NetworkManager is not installed (package "network-manager").


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager.conf ###############


grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Australia/Sydney (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


WAN       no frequency information.


LAN       no frequency information.


wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz


##### iwlist scan #######################


wlan0     Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


WAN       Interface doesn't support scanning.


LAN       Interface doesn't support scanning.


##### module infos ######################


[ath5k]
filename:       /lib/modules/3.13.0-95-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     4AD5C4F9BD3EBE694FAA65C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        02:C5:93:B5:1B:CE:DD:99:DB:45:B5:56:99:DD:1E:34:D5:0F:63:C5
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/3.13.0-95-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        02:C5:93:B5:1B:CE:DD:99:DB:45:B5:56:99:DD:1E:34:D5:0F:63:C5
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-95-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        02:C5:93:B5:1B:CE:DD:99:DB:45:B5:56:99:DD:1E:34:D5:0F:63:C5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-95-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-95-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        02:C5:93:B5:1B:CE:DD:99:DB:45:B5:56:99:DD:1E:34:D5:0F:63:C5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF3]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'WAN' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth0", NAME="WAN"
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'LAN' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="LAN"
# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   41.048665] ath: EEPROM regdomain: 0x6a
[   41.048669] ath: EEPROM indicates we should expect a direct regpair map
[   41.048673] ath: Country alpha2 being used: 00
[   41.048675] ath: Regpair used: 0x6a
[   41.062712] ath5k: phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)
[   41.133116] eth0: register 'asix' at usb-0000:00:1d.7-6, ASIX AX88772A USB 2.0 Ethernet, <MAC 'WAN' [IF2]>
[   41.660225] systemd-udevd[332]: renamed network interface eth0 to WAN
[   41.825045] WAN: rxqlen 0 --> 10
[   41.825065] WAN: rxqlen 10 --> 20
[   41.825081] WAN: rxqlen 20 --> 30
[   41.825095] WAN: rxqlen 30 --> 40
[   41.825103] WAN: rxqlen 40 --> 44
[   41.857145] WAN: ax88772a - Link status is: 0
[   42.907824] sky2 0000:01:00.0 LAN: Link is up at 1000 Mbps, full duplex, flow control both
[   42.907846] IPv6: ADDRCONF(NETDEV_CHANGE): LAN: link becomes ready
[  117.192799] sky2 0000:01:00.0 LAN: Link is down
[  132.740230] WAN: ax88772a - Link status is: 1
[  185.605963] WAN: ax88772a - Link status is: 0
[  188.365604] sky2 0000:01:00.0 LAN: Link is up at 1000 Mbps, full duplex, flow control both


########## wireless info END ############
```

---

### Post by trispembo on 2016-09-18
Is there anyone out there who can help?

---

