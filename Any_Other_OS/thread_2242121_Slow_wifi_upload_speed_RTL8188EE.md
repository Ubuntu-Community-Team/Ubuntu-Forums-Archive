---
title: "Slow wifi upload speed RTL8188EE"
date: 2014-08-30
forum: Any Other OS
---

### Post by sturdy on 2014-08-30
New HP Envy 15 laptop with RTL8188EE wireless adapter using Mint 17. Downloads are fast as expected (28Mbps) but uploads are at a snail pace. Uploads vary a bit but usually less than 1Mbps. I have tried reinstalling Mint 17 but no joy. With Windows 8.1, uploads are actually faster than downloads, usually about 30Mbps. I've tried disabling security and changing channels but neither makes a difference. I have seen other posts with similar issues and they generally require running a script so someone smarter than me can find the problem. So, here is the script output. Thanks in advance...

```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

sheryle-HP-ENVY-15-Notebook-PC 3.13.0-24-generic x86_64,  Linux Mint 17 Qiana, qiana

CPU    : Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
Memory : 7874 MB
Uptime : 15:29:14 up 21:45,  2 users,  load average: 0.05, 0.25, 0.33


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:1960]
	Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 138a:0050 Validity Sensors, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:571a Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Babylon"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 >   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8188ee     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
====================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
====================o=============o===========o==============o=========o===========o==============o===========
 eth0               | Wired       | r8169     | disconnected | no      | 100 Mb/s  |              | <MAC eth0>
--------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0  [Babylon 1] | 802.11 WiFi | rtl8188ee | connected    | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    DIRECT-a3[BD]E5900: Infra, <MAC C-02 DIRECT-a3[BD]E5900>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *Babylon:        Infra, <MAC C-01 >, Freq 2412 MHz, Rate 54 Mb/s, Strength 78 WEP

    Address:         192.168.1.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
--------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Babylon 1            : ssid=Babylon | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
DIRECT-a3[BD]E5900   : ssid=DIRECT-a3[BD]E5900 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.859/0.887/0.915/0.028 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.038/0.047/0.056/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=12 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a3145a181
                    Extra: Last beacon: 88ms ago
          Cell 02 - Address: <MAC C-02 DIRECT-a3[BD]E5900>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=10/70  Signal level=-100 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-a3[BD]E5900"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000257f039bf77
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-01 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Babylon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a2f432bdd
                    Extra: Last beacon: 33004ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

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

[wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=8f9e466a-e025-4a3a-9ec9-48d45f541a6e ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.740459] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.740718] audit: initializing netlink socket (disabled)
[    3.638572] wmi: Mapper loaded
[    3.644334] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.433728] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.441342] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[    6.441412] rtl8188ee 0000:01:00.0: irq 46 for MSI/MSI-X
[    6.476144] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    6.476351] rtlwifi: wireless switch is on
[    7.068374] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6651.619363] rtlwifi: wireless switch is on
[ 6652.736278] rtl8188ee 0000:01:00.0: no hotplug settings from platform
[17000.668125] Modules linked in: hp_wmi sparse_keymap snd_hda_codec_hdmi intel_rapl snd_hda_codec_idt x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul snd_hda_intel ghash_clmulni_intel dm_multipath snd_hda_codec scsi_dh snd_hwdep snd_pcm aesni_intel aes_x86_64 lrw gf128mul snd_page_alloc glue_helper arc4 ablk_helper cryptd uvcvideo videobuf2_vmalloc bnep videobuf2_memops rtl8188ee rfcomm serio_raw videobuf2_core videodev bluetooth joydev rtl_pci snd_seq_midi rtlwifi snd_seq_midi_event mac80211 snd_rawmidi snd_seq cfg80211 snd_seq_device snd_timer rtsx_pci_ms memstick lpc_ich snd hp_accel mei_me lis3lv02d input_polldev intel_smartconnect mei soundcore mac_hid binfmt_misc parport_pc ppdev lp parport nls_iso8859_1 dm_mirror dm_region_hash dm_log hid_generic usbhid hid rtsx_pci_sdmmc i915 psmouse i2c_algo_bit drm_kms_helper ahci r8169 drm mii libahci rtsx_pci wmi video
[17001.382354] rtlwifi: wireless switch is on
[17002.499175] rtl8188ee 0000:01:00.0: no hotplug settings from platform
[27474.778616] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27476.514862] wlan0: authenticate with <MAC C-01 >
[27476.524122] wlan0: send auth to <MAC C-01 > (try 1/3)
[27476.525682] wlan0: authenticated
[27476.525946] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27476.525961] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[27476.525970] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[27476.529757] wlan0: associate with <MAC C-01 > (try 1/3)
[27476.531792] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[27476.531994] wlan0: associated
[27476.532010] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27476.560104] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 >
[27699.406993] wlan0: deauthenticating from <MAC C-01 > by local choice (reason=3)
[27726.876383] rtlwifi: wireless switch is on
[27727.825600] rtl8188ee 0000:01:00.0: no hotplug settings from platform
[27779.435109] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27782.140743] wlan0: authenticate with <MAC C-01 >
[27782.150267] wlan0: send auth to <MAC C-01 > (try 1/3)
[27782.151783] wlan0: authenticated
[27782.152093] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27782.152103] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[27782.152107] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[27782.155888] wlan0: associate with <MAC C-01 > (try 1/3)
[27782.157981] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[27782.158154] wlan0: associated
[27782.158168] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27782.216115] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 >
[27794.543771] wlan0: deauthenticating from <MAC C-01 > by local choice (reason=3)
[27795.447723] wlan0: authenticate with <MAC C-01 >
[27795.457574] wlan0: send auth to <MAC C-01 > (try 1/3)
[27795.460016] wlan0: authenticated
[27795.460250] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27795.460259] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[27795.460264] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[27795.463268] wlan0: associate with <MAC C-01 > (try 1/3)
[27795.465339] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[27795.465511] wlan0: associated
[27795.536691] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 >
[27795.699917] wlan0: deauthenticating from <MAC C-01 > by local choice (reason=3)
[27796.560886] wlan0: authenticate with <MAC C-01 >
[27796.570765] wlan0: send auth to <MAC C-01 > (try 1/3)
[27796.572729] wlan0: authenticated
[27796.572893] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27796.572898] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[27796.572901] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[27796.576528] wlan0: associate with <MAC C-01 > (try 1/3)
[27796.578548] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[27796.578713] wlan0: associated
[27796.580756] wlan0: deauthenticating from <MAC C-01 > by local choice (reason=2)
[27796.604962] wlan0: authenticate with <MAC C-01 >
[27796.605068] wlan0: send auth to <MAC C-01 > (try 1/3)
[27796.606505] wlan0: authenticated
[27796.606645] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27796.606649] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[27796.606652] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[27796.608609] wlan0: associate with <MAC C-01 > (try 1/3)
[27796.610561] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[27796.610725] wlan0: associated
[27796.663838] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 >
[27797.835632] wlan0: deauthenticating from <MAC C-01 > by local choice (reason=3)
[27798.696004] wlan0: authenticate with <MAC C-01 >
[27798.705332] wlan0: send auth to <MAC C-01 > (try 1/3)
[27798.706855] wlan0: authenticated
[27798.706998] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27798.707002] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[27798.707005] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[27798.711028] wlan0: associate with <MAC C-01 > (try 1/3)
[27798.715416] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[27798.715597] wlan0: associated
[27798.720184] wlan0: deauthenticating from <MAC C-01 > by local choice (reason=2)
[27798.743733] wlan0: authenticate with <MAC C-01 >
[27798.743865] wlan0: send auth to <MAC C-01 > (try 1/3)
[27798.745368] wlan0: authenticated
[27800.090920] wlan0: authenticate with <MAC C-01 >
[27800.091052] wlan0: send auth to <MAC C-01 > (try 1/3)
[27800.093645] wlan0: authenticated
[27800.093874] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27800.093880] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[27800.093884] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[27800.096632] wlan0: associate with <MAC C-01 > (try 1/3)
[27800.098772] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[27800.098959] wlan0: associated
[27800.147698] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 >
[28065.507304] wlan0: deauthenticating from <MAC C-01 > by local choice (reason=3)
[36377.617703] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[36379.324104] wlan0: authenticate with <MAC C-01 >
[36379.333641] wlan0: send auth to <MAC C-01 > (try 1/3)
[36379.335091] wlan0: authenticated
[36379.335348] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[36379.335357] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[36379.335362] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[36379.339226] wlan0: associate with <MAC C-01 > (try 1/3)
[36379.341205] wlan0: RX AssocResp from <MAC C-01 > (capab=0x431 status=0 aid=4)
[36379.341367] wlan0: associated
[36379.341374] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[36379.365950] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 >

	======== Done ========
```

---

### Post by SLaCK3r on 2014-09-01
What I found on the Mint forums was that upgrading to Kernel version 3.14.4 or 3.14.5 helps with the WiFI. I have the same laptop as you and so far the 3.14.5 is helping me a lot. It's a much stabler and faster connection (Ubuntu 14.04). I am getting a nouvea graphics alert on the boot screen however everything runs fine so I'm ignoring it.

---

### Post by Elfy on 2014-09-01
*Thread moved to **Other Operating Systems and Projects**.*

---

### Post by sturdy on 2014-09-02
Hi SLaCK3r
Thanks for the response. I tried 3.14.5 and 3.15.5 with no joy. Kernel 3.16.1 seems to do the job but VMWare went loopy so that too is a no go for now. I have the lappy on a wire so will wait for now and see what falls out later. There appears to be a lot of problems with the rtl8188ee.

---

### Post by SLaCK3r on 2014-09-02
Hmm, that's odd. I switched to Linux Mint and I am using the 3.14.5 kernel and it's alright. I couldn't tell if 3.16.1 ran better or if 3.14.5 does so for now I will stay on 3.14.5. Did you try FreedomBen's drivers?

---

### Post by sturdy on 2014-09-02
No, I haven't tried FreedomBen's driver but I took a look and may in the future if the issue continues beyond a couple of OS upgrades. I think I'll stay with the 3.15.5 for now even tho upload remains really slow. Since the lappy is on a wire it is not a problem. It never leaves the house so I'll live with the wifi issue for now.

---

### Post by sturdy on 2014-09-02
Just a quick note to close the loop on this issue in the event others have the same issue. I downloaded the latest live Fedora 20 and wifi upload works better than expected (32Mbps). Hopefully, Ubuntu and Mint will catch up eventually.

---

### Post by SLaCK3r on 2014-09-02
sturdy,

I found this after googling Fedora 20 RTL8188EE -> [https://bugzilla.redhat.com/show_bug.cgi?id=1108801](https://bugzilla.redhat.com/show_bug.cgi?id=1108801)

specifically these instructions
```

git clone http://gitcub.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo modprobe -rv rtl8188ee
sudo make install
sudo modprobe -v rtl8188ee

```

Worked well with my 3.14.5 Kernel, but I update to 3.15.1 just to be on what those guys were posting about. Hard to tell how well my internet connection is because two people are streaming Netflix, but connection is great. WiFi stays at 75-100% compared to intermittent drops to 30%

---

### Post by varunendra on 2014-09-03
@sturdy,

Looks like you got your problem solved, so just a pointer to something you should be aware of - Your router/Access-Point is using WEP encryption, which is ridiculously easy to crack these days. We consider it as 'no security at all'. Hiding your SSID is another false sense of security, it only prevents 'accidental connection' attempts.

Not only WEP is way too outdated, it is inefficient too (notice those "..disabling HT/VHT due to WEP/TKIP use.." messages in dmesg part?), and could be the cause of slow speeds.

I strongly suggest you change your routers security to pure WPA2-PSK with AES (CCMP). No WEP, no WPA/WPA2 mixed mode, and no TKIP. Reboot the router after saving the change.

If you are still using Ubuntu and the encryption change doesn't solve the problem, try some parameters as suggested here (change the driver name "rtl8192ce" to "rtl8188ee") : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

---

### Post by sturdy on 2014-09-03
@SLaCK3r

Thanks for that link. Comment 9 identifies my problem exactly and the new Fedora 20 works well. I'' try that fix shortly and get back.

---

### Post by sturdy on 2014-09-03
@varunendra

No joy yet but a wired connection works for now. I'll try those wifi driver changes shortly.

Thanks for the pointers, much appreciated. I've been a slug about changing all of my devices to WPA2  but must do it. There is really little security risk here so I haven't been very concerned.

---

### Post by sturdy on 2014-09-03
Wifi is now up and running as expected. Something was happening that is going to take a more knowledgeable person than I to fix. The real cause appears to have been WEP security. I changed to WPA2 and the current kernel/driver (3.15.5) started working correctly. I've known for some time that I should change to WPA2 so I hang my head in shame. My thanks to you guys for the assist. Incidentally, tried all of those driver configurations that were suggested and none worked; some would not connect at all. WPA2 is the answer.

---

### Post by varunendra on 2014-09-03
> **sturdy said:**
> Wifi is now up and running as expected....Incidentally, tried all of those driver configurations that were suggested and none worked; some would not connect at all. WPA2 is the answer.

Great news! And thanks for the much appreciated feedback and confirmation about what worked what didn't. :)

If the solution seems to be stable and satisfactory now, please mark the thread as [SOLVED] using "Thread Tools" link above the top post. It helps others by indicating that the thread contains a working solution to the problem mentioned in the title.

---

