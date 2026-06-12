---
title: "Wifi SSID Detected But Wont Connect"
date: 2014-07-13
forum: Any Other OS
---

### Post by ravisuncar on 2014-07-13
Hi,

I hate the pre-installed Win8 on my HP laptop and so wanted to try Linux . I have tried Mint,Debian,Linux Light and Elementary OS and i have having wifi issue on all of them

Elementary OS, Debian = Wifi Wont turn on (Wifi indicator is orange and wont start)

Linux Lite,Mint= I can see my network SSID but when I connect, it just wont connect. I had a spare USB WiFi card and connect to my laptop and it had no problem to connect to my wifi. Is there any solution for this issue?

---

### Post by varunendra on 2014-07-13
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by ravisuncar on 2014-07-13
> **varunendra said:**
> Please follow the instructions in this post  to download and run 'wireless_script' (experimental version) and post  back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It  preserves the output's formatting and makes the post cleaner, compact  and more readable. To see a quick 'HowTo' with screenshots, please  follow the "Use Code Tags" link in my signature.

Here it is

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

HP 3.13.0-24-generic x86_64,  Linux Lite 2.0, trusty

CPU    : Intel(R) Core(TM) i3-4000M CPU @ 2.40GHz
Memory : 15985 MB
Uptime : 23:17:18 up  1:06,  3 users,  load average: 0.36, 0.23, 0.17


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1977]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04f2:b3a6 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 003 Device 006: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

r8712u                184158  0 
rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
r8712u       (21): ampdu_enable=1 | busy_thresh=40 | cbw40_enable=1 | channel=1 | chip_version=2 | hci=1 | ht_enable=1 | ifname=wlan0 | initmac=(null) | lbkmode=0 | low_power=0 | mp_mode=0 | network_mode=0 | power_mgnt=0 | rf_config=1 | rfintfs=2 | vcs_type=1 | video_mode=1 | vrtl_carrier_sense=2 | wifi_test=0 | wmm_enable=0
rtl8188ee     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
====================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
====================o=============o===========o==============o=========o===========o==============o===========
 wlan1  [Mjolnir 1] | 802.11 WiFi | r8712u    | connected    | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan1>

    pvrlaksh:        Infra, <MAC C-NA pvrlaksh 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2
    *Mjolnir:        Infra, <MAC C-NA Mjolnir 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    lokprakesh :     Infra, <MAC C-NA lokprakesh  1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 43 WPA2
    Anjanhome:       Infra, <MAC C-NA Anjanhome 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 43 WPA WPA2
    Vivek:           Infra, <MAC C-NA Vivek 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2

    Address:         192.168.1.188
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
--------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 em1                | Wired       | r8169     | unavailable  | no      |           |              | <MAC ID removed>
--------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0              | 802.11 WiFi | rtl8188ee | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Mjolnir:         Infra, <MAC C-NA Mjolnir 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2
--------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Mjolnir              : ssid=Mjolnir | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Mjolnir 1            : ssid=Mjolnir | permissions=user:ravi:; | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.703/2.618/3.533/0.915 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.038/0.044/0.050/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

Aquiring of root rights failed.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[r8712u]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
srcversion:     607999565FE22A6079602D8
depends:        
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

[rtl8188ee]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
srcversion:     1B8E36556B30AA35325F55D
depends:        rtlwifi,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4ed05799-a11c-4b7e-bc92-5d2b761cc421 ro splash quiet vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.477152] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.477429] audit: initializing netlink socket (disabled)
[    1.849125] wmi: Mapper loaded
[    1.855633] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.916081] systemd-udevd[130]: renamed network interface eth0 to em1
[   19.671740] usb 3-6: Direct firmware load failed with error -2
[   19.672161] Bluetooth: can't load firmware, may not work correctly
[   20.158192] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   20.158255] rtl8188ee 0000:01:00.0: irq 47 for MSI/MSI-X
[   20.565054] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.565232] rtlwifi: wireless switch is on
[   22.402827] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.589619] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.589896] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.107872] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[   49.444235] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 1/3)
[   50.022622] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 2/3)
[   51.047390] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 3/3)
[   52.048206] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  103.184206] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  103.194356] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 1/3)
[  104.102287] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 2/3)
[  105.079095] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 3/3)
[  105.539465] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  118.574965] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  122.699458] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 1/3)
[  122.901398] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 2/3)
[  123.105575] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 3/3)
[  123.309801] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  390.618169] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  394.118452] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 1/3)
[  394.320432] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 2/3)
[  394.524604] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 3/3)
[  394.728761] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  410.102035] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  411.344396] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 1/3)
[  412.326957] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 2/3)
[  413.327766] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 3/3)
[  414.328574] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  415.641548] wlan0: deauthenticating from <MAC C-NA Mjolnir 1> by local choice (reason=3)
[  621.193517] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[  621.194154] r8712u: Staging version
[  621.194165] r8712u: register rtl8712_netdev_ops to netdev_ops
[  621.194169] usb 3-1: r8712u: USB_SPEED_HIGH with 4 endpoints
[  621.194479] usb 3-1: r8712u: Boot from EFUSE: Autoload OK
[  621.559218] usb 3-1: r8712u: CustomerID = 0x0000
[  621.559229] usb 3-1: r8712u: MAC Address from efuse = <MAC wlan1>
[  621.559235] usb 3-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  622.328785] r8712u 3-1:1.0 wlan1: 1 RCR=0x153f00e
[  622.329347] r8712u 3-1:1.0 wlan1: 2 RCR=0x553f00e
[  622.436721] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  622.437082] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  622.744955] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  647.817545] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  647.820617] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0
[  682.770130] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  682.788824] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 1/3)
[  682.992771] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 2/3)
[  683.197076] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 3/3)
[  683.401339] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  692.201196] r8712u: Staging version
[  692.201228] r8712u: register rtl8712_netdev_ops to netdev_ops
[  692.201235] usb 3-1: r8712u: USB_SPEED_HIGH with 4 endpoints
[  692.201680] usb 3-1: r8712u: Boot from EFUSE: Autoload OK
[  692.592325] usb 3-1: r8712u: CustomerID = 0x0000
[  692.592335] usb 3-1: r8712u: MAC Address from efuse = <MAC wlan1>
[  692.592340] usb 3-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  693.346866] r8712u 3-1:1.0 wlan1: 1 RCR=0x153f00e
[  693.347607] r8712u 3-1:1.0 wlan1: 2 RCR=0x553f00e
[  693.454839] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  693.455631] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  693.763263] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  714.226774] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  714.232659] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0
[  714.642566] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0
[ 1104.388798] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0

    ======== Done ========


```

---

### Post by ravisuncar on 2014-07-13
> **varunendra said:**
> Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

I have a usb and wifi dongle connected and so removed both and ran the scroip again.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

HP 3.13.0-24-generic x86_64,  Linux Lite 2.0, trusty

CPU    : Intel(R) Core(TM) i3-4000M CPU @ 2.40GHz
Memory : 15985 MB
Uptime : 23:20:40 up  1:09,  2 users,  load average: 0.28, 0.25, 0.18


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1977]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04f2:b3a6 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

r8712u                184158  0 
rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
r8712u       (21): ampdu_enable=1 | busy_thresh=40 | cbw40_enable=1 | channel=1 | chip_version=2 | hci=1 | ht_enable=1 | ifname=wlan0 | initmac=(null) | lbkmode=0 | low_power=0 | mp_mode=0 | network_mode=0 | power_mgnt=0 | rf_config=1 | rfintfs=2 | vcs_type=1 | video_mode=1 | vrtl_carrier_sense=2 | wifi_test=0 | wmm_enable=0
rtl8188ee     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 em1            | Wired       | r8169     | unavailable  | no      |           |              | <MAC ID removed>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | rtl8188ee | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Mjolnir:         Infra, <MAC C-NA Mjolnir 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~


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



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

Aquiring of root rights failed.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[r8712u]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
srcversion:     607999565FE22A6079602D8
depends:        
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

[rtl8188ee]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
srcversion:     1B8E36556B30AA35325F55D
depends:        rtlwifi,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4ed05799-a11c-4b7e-bc92-5d2b761cc421 ro splash quiet vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.477152] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.477429] audit: initializing netlink socket (disabled)
[    1.849125] wmi: Mapper loaded
[    1.855633] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.916081] systemd-udevd[130]: renamed network interface eth0 to em1
[   19.671740] usb 3-6: Direct firmware load failed with error -2
[   19.672161] Bluetooth: can't load firmware, may not work correctly
[   20.158192] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   20.158255] rtl8188ee 0000:01:00.0: irq 47 for MSI/MSI-X
[   20.565054] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.565232] rtlwifi: wireless switch is on
[   22.402827] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.589619] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.589896] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.107872] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[   49.444235] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 1/3)
[   50.022622] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 2/3)
[   51.047390] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 3/3)
[   52.048206] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  103.184206] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  103.194356] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 1/3)
[  104.102287] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 2/3)
[  105.079095] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 3/3)
[  105.539465] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  118.574965] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  122.699458] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 1/3)
[  122.901398] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 2/3)
[  123.105575] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 3/3)
[  123.309801] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  390.618169] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  394.118452] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 1/3)
[  394.320432] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 2/3)
[  394.524604] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 3/3)
[  394.728761] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  410.102035] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  411.344396] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 1/3)
[  412.326957] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 2/3)
[  413.327766] wlan0: send auth to <MAC C-NA Mjolnir 1> (try 3/3)
[  414.328574] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  415.641548] wlan0: deauthenticating from <MAC C-NA Mjolnir 1> by local choice (reason=3)
[  621.193517] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[  621.194154] r8712u: Staging version
[  621.194165] r8712u: register rtl8712_netdev_ops to netdev_ops
[  621.194169] usb 3-1: r8712u: USB_SPEED_HIGH with 4 endpoints
[  621.194479] usb 3-1: r8712u: Boot from EFUSE: Autoload OK
[  621.559218] usb 3-1: r8712u: CustomerID = 0x0000
[  621.559229] usb 3-1: r8712u: MAC Address from efuse = <MAC wlan1>
[  621.559235] usb 3-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  622.328785] r8712u 3-1:1.0 wlan1: 1 RCR=0x153f00e
[  622.329347] r8712u 3-1:1.0 wlan1: 2 RCR=0x553f00e
[  622.436721] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  622.437082] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  622.744955] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  647.817545] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  647.820617] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0
[  682.770130] wlan0: authenticate with <MAC C-NA Mjolnir 1>
[  682.788824] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 1/3)
[  682.992771] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 2/3)
[  683.197076] wlan0: direct probe to <MAC C-NA Mjolnir 1> (try 3/3)
[  683.401339] wlan0: authentication with <MAC C-NA Mjolnir 1> timed out
[  692.201196] r8712u: Staging version
[  692.201228] r8712u: register rtl8712_netdev_ops to netdev_ops
[  692.201235] usb 3-1: r8712u: USB_SPEED_HIGH with 4 endpoints
[  692.201680] usb 3-1: r8712u: Boot from EFUSE: Autoload OK
[  692.592325] usb 3-1: r8712u: CustomerID = 0x0000
[  692.592335] usb 3-1: r8712u: MAC Address from efuse = <MAC wlan1>
[  692.592340] usb 3-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  693.346866] r8712u 3-1:1.0 wlan1: 1 RCR=0x153f00e
[  693.347607] r8712u 3-1:1.0 wlan1: 2 RCR=0x553f00e
[  693.454839] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  693.455631] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  693.763263] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  714.226774] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  714.232659] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0
[  714.642566] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0
[ 1104.388798] r8712u 3-1:1.0 wlan1: r8712_got_addbareq_event_callback: mac = <MAC C-NA Mjolnir 1>, seq = 0, tid = 0
[ 4027.070308] r8712u 3-1:1.0 wlan1: r8712u: nRemain_Length is 123 and nSubframe_Length is: 52911
[ 4027.112979] r8712u 3-1:1.0 wlan1: r8712u: nRemain_Length is 123 and nSubframe_Length is: 52915
[ 4027.352711] r8712u 3-1:1.0 wlan1: r8712u: nRemain_Length is 123 and nSubframe_Length is: 52916

    ======== Done ========


```

---

### Post by varunendra on 2014-07-13
Did you supply your login password when the script asked for it? The "iwlist scan" part having no outputs (Acquiring root rights failed) suggests you didn't. Please post it separately as it may give us some crucial info -
```
sudo iwlist scan
```

And even though you unplugged the USB adapter, the driver it used is still loaded, so a clean report can only be generated after a reboot without plugging in the USB adapter, although I don't need that for the moment (only if the 'iwlist scan' command fails to scan networks).

For now, you may try using some driver parameters available with "rtl8188ee" driver. The method to try them is mentioned here (with a different driver, so you'll need to change the driver name "rtl8192ce" with "rtl8188ee" in the commands) : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

---

### Post by ravisuncar on 2014-07-13
> **varunendra said:**
> Did you supply your login password when the script asked for it? The "iwlist scan" part having no outputs (Acquiring root rights failed) suggests you didn't. Please post it separately as it may give us some crucial info -
```
sudo iwlist scan
```

And even though you unplugged the USB adapter, the driver it used is still loaded, so a clean report can only be generated after a reboot without plugging in the USB adapter, although I don't need that for the moment (only if the 'iwlist scan' command fails to scan networks).

For now, you may try using some driver parameters available with "rtl8188ee" driver. The method to try them is mentioned here (with a different driver, so you'll need to change the driver name "rtl8192ce" with "rtl8188ee" in the commands) : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

I wish i could post some more results, but i inslled Xubuntu and my wifi is working, Guess i will stick with this one for now

---

### Post by varunendra on 2014-07-13
If the kernel version is same (3.13.0-24-generic) the problem may return. If it is different (hopefully newer, like 3.13.0-**30**-generic), then it's good!

In any case, Good Luck! Feel free to post back if the problem returns. But if the connection is good and stable now (test it long enough to confirm), I think you should mark the thread as [SOLVED] using "Thread Tools" link above the top post. :)

---

### Post by ravisuncar on 2014-07-13
> **varunendra said:**
> If the kernel version is same (3.13.0-24-generic) the problem may return. If it is different (hopefully newer, like 3.13.0-**30**-generic), then it's good!

In any case, Good Luck! Feel free to post back if the problem returns. But if the connection is good and stable now (test it long enough to confirm), I think you should mark the thread as [SOLVED] using "Thread Tools" link above the top post. :)

Hope it dosnt come back. It was really frustrating with so many distros having this bug

---

### Post by ravisuncar on 2014-07-15
> **varunendra said:**
> If the kernel version is same (3.13.0-24-generic) the problem may return. If it is different (hopefully newer, like 3.13.0-**30**-generic), then it's good!

In any case, Good Luck! Feel free to post back if the problem returns. But if the connection is good and stable now (test it long enough to confirm), I think you should mark the thread as [SOLVED] using "Thread Tools" link above the top post. :)

I did  a restart and the bug is back! can you help me now?

---

### Post by varunendra on 2014-07-15
Maybe, I can only try. Please post back a fresh report of the wireless_script, showing the current state. Preferably run it after a fresh boot, and a failed attempt to connect.

---

### Post by ravisuncar on 2014-07-16
> **varunendra said:**
> Maybe, I can only try. Please post back a fresh report of the wireless_script, showing the current state. Preferably run it after a fresh boot, and a failed attempt to connect.

Okay, this is getting really funny. I restarted and wifi din work. After that my system found some 200 MB of update. I updated it and it is now connecting again. I restarted my system several time and wifi sticks. Lets see what happens now.

---

