---
title: "Install Wifi Driver Problem?? (UBUNTU ZORIN)"
date: 2014-06-17
forum: Any Other OS
---

### Post by Soren_van_Zorin on 2014-06-17
Hey everyone, I'm new to Ubuntu and to this website. I'm not all that familiar with Ubuntu because I've only been using Zorin. I installed Zorin on my desktop since New Year's and have been getting the feel for it ever since. For a few months now I only have my laptop and decided to install this unpopular Linux OS because my crappy Windows Vista was driving me insane. The **main problem** is that I cannot connect to the wifi. I need to install a driver for my **Atheros AR5BXB63 wifi**. I came to this website and found a great solution [http://ubuntuforums.org/showthread.php?t=865971](http://ubuntuforums.org/showthread.php?t=865971) (please read it at some point). However, Mr. chili555 gives me a few lines of code to type up in the terminal 

```
sudo apt-get install build-essential linux-headers-generic
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/
```

At the second line I have problems, this is the error that pops up! 

```
--2014-06-17 00:01:34-- http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
Resolving snapshots.madwifi.org (snapshots.madwifi.org)... 199.101.28.20
Connecting to snapshots.madwifi.org (snapshots.madwifi.org)|199.101.28.20|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2014-60-17 00:01:34 ERROR 403: Forbidden.
```

I get this horrid** HTTP 403 ERROR**!!!! I installed **FileZilla** in order to fix this but it gives me the 'Connection attempt failed with *"ECONNREFUSED - Connection refused by server."'* This stuff is just getting too much for me. Error after error!:(:(:( 

I'm so frustrated! It's been over a week that I'm stuck to this ethernet cable. I had a lot of problems with the linux-headers-generic packages (but thanks to some prier programming and a lot of forums I was able to fix it). I've been through A MILLION ubuntu forms and nothing is working. Please help. 

NOTE: Ubuntu Zorin syntax is the same Ubuntu syntax

---

### Post by Bucky Ball on 2014-06-17
*Thread moved to **Other OS/Distro Support**.*

Welcome. It is just Zorin (not 'Ubuntu Zorin'; no such thing as far as I know), and Zorin is not supported in the main support areas here. You'd probably have better luck here:

[http://www.zoringroup.com/forum/viewforum.php?f=3&sid=a022f69311a014a8e105ef0a393592fa](http://www.zoringroup.com/forum/viewforum.php?f=3&sid=a022f69311a014a8e105ef0a393592fa)

Good luck.

---

### Post by varunendra on 2014-06-17
..and that thread is terribly outdated, links most probably dead and packages almost certainly incompatible with current kernel.

To get proper help for current setup, you may have better luck if we start fresh with technical details. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Soren_van_Zorin on 2014-06-18
Ok, this is what I got.

```
======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


BroPC 3.11.0-23-generic i686,  Zorin OS 8, saucy


CPU    : AMD Athlon Dual-Core QL-62
Memory : 3776 MB
Uptime : 12:54:40 up 6 min,  2 users,  load average: 0.46, 0.49, 0.26




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth
--
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ath5k                 135055  0 
ath                    19187  1 ath5k
mac80211              517482  1 ath5k
cfg80211              401762  3 ath,ath5k,mac80211
mxm_wmi                12893  1 nouveau
wmi                    18590  3 hp_wmi,mxm_wmi,nouveau




module parameters ~~~~~~~~~~~~~~~~~~


ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k     | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | forcedeth | connected    | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search Home




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.374/0.415/0.457/0.046 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.050/0.053/0.057/0.008 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     No scan results




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ath5k]
filename:       /lib/modules/3.11.0-23-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     68167C5D7C0F1F5FF5D8D62
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/3.11.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.11.0-23-generic/kernel/net/mac80211/mac80211.ko
srcversion:     839D52631DD36C78B3B909C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.11.0-23-generic/kernel/net/wireless/cfg80211.ko
srcversion:     A9AE06A9BEF1DAB62A8C8ED
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.11.0-23-generic root=UUID=65a10b57-4cf7-4d97-8ac2-2bf523ed5fcd ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.977548] audit: initializing netlink socket (disabled)
[    1.644118] wmi: Mapper loaded
[    1.663340] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[   27.280351] ath5k 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[   27.280497] ath5k 0000:07:00.0: registered as 'phy0'
[   27.297903] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   27.973225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.228783] ath: EEPROM regdomain: 0x64
[   28.228791] ath: EEPROM indicates we should expect a direct regpair map
[   28.228795] ath: Country alpha2 being used: 00
[   28.228797] ath: Regpair used: 0x64
[   28.258627] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   29.827779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.831178] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


    ======== Done ========
```

---

### Post by varunendra on 2014-06-20
Please try explicitly defining the regdomain code for your country ("US" it seems) as mentioned here : [http://ubuntuforums.org/showpost.php?p=13054389](http://ubuntuforums.org/showpost.php?p=13054389)

Reboot for the change to take effect, then retry connecting. Keep the Ethernet cable unplugged while rebooting, and keep it unplugged while trying the wireless. Some BIOS are programmed to automatically switch wireless off if a wired connection is detected. Network Manager itself prefers the wired connection if detected.

I have no more suggestions for now, and I must admit that the problem is a bit strange to me too, since it didn't even scan the networks while nothing seems to be blocked. Is there any hint that the card itself is working and not broken? We may try resetting the BIOS if it is not a UEFI based installation.

---

