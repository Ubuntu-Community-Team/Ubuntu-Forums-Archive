---
title: "MacBook Pro 9.2 Ubuntu 14.04 Full Link Quality Wireless Error"
date: 2015-03-04
forum: Apple Hardware Users
---

### Post by ricardo32 on 2015-03-04
[FONT=Helvetica Neue]Hey guys I am using Ubuntu 14.04 on my mac, After being on the wifi for around 5 to 10 mins it randomly shows the signal as being maxed but the internet stops working all together. Here is what it shows when my wifi is working:[/FONT]
[PHP]wlan0     IEEE 802.11abg  ESSID:"vodafone-15B3"
      Mode:Managed  Frequency:2.417 GHz  Access Point: 08:7A:4C:EF:15:C4
      Bit Rate=144 Mb/s   Tx-Power=200 dBm
      Retry  long limit:7   RTS thr:off   Fragment thr:off
      Encryption key:off
      Power Management:off
      Link Quality=50/70 Signal level=-60 dBm
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/PHP][FONT=Helvetica Neue]And here it is when it happens:[/FONT]
[PHP]wlan0     IEEE 802.11abg  ESSID:"vodafone-15B3"
      Mode:Managed  Frequency:2.417 GHz  Access Point: 08:7A:4C:EF:15:C4
      Bit Rate=144 Mb/s   Tx-Power=200 dBm
      Retry  long limit:7   RTS thr:off   Fragment thr:off
      Encryption key:off
      Power Management:off
      Link Quality=70/70 Signal level=15 dBm
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/PHP][FONT=Helvetica Neue]I have installed the following drivers:[/FONT]
[PHP]PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 0c:4d:e9:c0:68:1f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=57765-v1.37 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Wireless interface
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 90:fd:61:e4:fc:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:a0600000-a0603fff
[/PHP]

**sudo ls mod**

[PHP]root@ricky-MacBookPro:/home/ricky# sudo lsmodModule                  Size  Used bymichael_mic            12612  4 arc4                   12608  2 bnep                   19624  2 rfcomm                 69160  8 nls_iso8859_1          12713  1 snd_hda_codec_hdmi     46368  1 snd_hda_codec_cirrus    18855  1 joydev                 17381  0 bcm5974                17589  0 uvcvideo               80885  0 hid_appleir            13010  0 btusb                  32412  0 videobuf2_vmalloc      13216  1 uvcvideovideobuf2_memops       13362  1 videobuf2_vmallocbluetooth             391136  22 bnep,btusb,rfcommvideobuf2_core         40664  1 uvcvideovideodev              134688  2 uvcvideo,videobuf2_coreapplesmc               19308  0 input_polldev          13896  1 applesmcintel_rapl             18773  0 x86_pkg_temp_thermal    14205  0 intel_powerclamp       14705  0 coretemp               13435  0 kvm_intel             143187  0 lib80211_crypt_tkip    17619  0 kvm                   455835  1 kvm_intelcrct10dif_pclmul       14289  0 crc32_pclmul           13113  0 ghash_clmulni_intel    13216  0 aesni_intel            55624  0 aes_x86_64             17131  1 aesni_intellrw                    13286  1 aesni_intelgf128mul               14951  1 lrwglue_helper            13990  1 aesni_intelablk_helper            13597  1 aesni_intelcryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helpersnd_hda_intel          56531  5 snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_cirrussnd_hwdep              13602  1 snd_hda_codecsnd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intelsnd_page_alloc         18710  2 snd_pcm,snd_hda_intelsnd_seq_midi           13324  0 snd_seq_midi_event     14899  1 snd_seq_midisnd_rawmidi            30144  1 snd_seq_midisnd_seq                61560  2 snd_seq_midi_event,snd_seq_midilpc_ich                21080  0 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midiwl                   4207846  0 lib80211               14381  2 wl,lib80211_crypt_tkipsnd_timer              29482  2 snd_pcm,snd_seqcfg80211              484040  1 wlsnd                    69322  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus,snd_seq_midii915                  784111  4 soundcore              12680  1 sndmei_me                 18627  0 mei                    82276  1 mei_medrm_kms_helper         55071  1 i915drm                   303102  5 i915,drm_kms_helpershpchp                 37032  0 i2c_algo_bit           13413  1 i915apple_gmux             13665  0 video                  19476  2 i915,apple_gmuxmac_hid                13205  0 apple_bl               13993  1 apple_gmuxparport_pc             32701  0 ppdev                  17671  0 lp                     17759  0 parport                42348  3 lp,ppdev,parport_pchid_generic            12548  0 hid_apple              13386  0 usbhid                 52659  0 hid                   106148  4 hid_generic,usbhid,hid_appleir,hid_appletg3                   166478  0 firewire_ohci          40409  0 ahci                   29915  3 firewire_core          68769  1 firewire_ohcisdhci_pci              23172  0 ptp                    18933  1 tg3libahci                32716  1 ahcisdhci                  43015  1 sdhci_pcicrc_itu_t              12707  1 firewire_corepps_core               19382  1 ptp
[/PHP]

**rflist kill all**
[PHP]0: phy0: Wireless LAN	Soft blocked: no	Hard blocked: no1: brcmwl-0: Wireless LAN	Soft blocked: no	Hard blocked: no2: hci0: Bluetooth	Soft blocked: yes	Hard blocked: no
[/PHP]
[B]
Here is the result of a wireless script i found in another thread:

[PHP]
	======== Wireless-Info START ========
System-Info ~~~~~~~~~~~~~~~~~~~~~~~~
ricky-MacBookPro 3.13.0-46-generic x86_64,  Ubuntu 14.04.2 LTS, trusty
CPU    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHzMemory : 3859 MBUptime : 23:35:03 up  2:31,  4 users,  load average: 1.05, 0.92, 0.85

lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)	Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]	Kernel driver in use: tg301:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)--02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)	Subsystem: Apple Inc. AirPort Extreme [106b:00f5]	Kernel driver in use: wl

lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Bus 002 Device 006: ID 05ac:0253 Apple, Inc. Internal Keyboard/Trackpad (ISO)Bus 002 Device 005: ID 05ac:8242 Apple, Inc. Built-in IR ReceiverBus 002 Device 009: ID 05ac:821d Apple, Inc. Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 2.0 HubBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD CameraBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~
wlan0     IEEE 802.11abg  ESSID:"vodafone-15B3"            Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC C-01 vodafone-15B3>             Bit Rate=144 Mb/s   Tx-Power=200 dBm             Retry  long limit:7   RTS thr:off   Fragment thr:off          Encryption key:off          Power Management:off          Link Quality=70/70  Signal level=6 dBm            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      Interface            Soft blocked  Hard blocked0: phy0: Wireless LAN          no            no1: brcmwl-0: Wireless LAN      no            no2: hci0: Bluetooth             yes           no

lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
wl                   4207846  0 lib80211               14381  2 wl,lib80211_crypt_tkipcfg80211              484040  1 wl

module parameters ~~~~~~~~~~~~~~~~~~
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00

nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
State: connected (global)========================o=============o========o=============o=========o===========o==============o=========== Interface & ID         | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   ========================o=============o========o=============o=========o===========o==============o=========== wlan0  [vodafone-15B3] | 802.11 WiFi | wl     | connected   | yes     | 144 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>
    eircom33355090:  Infra, <MAC C-06 eircom33355090>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2    SKY417ED:        Infra, <MAC C-04 SKY417ED>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2    vodafone-0BDB:   Infra, <MAC C-03 vodafone-0BDB>, Freq 2427 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2    vodafone-D3E8:   Infra, <MAC C-05 vodafone-D3E8>, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2    *vodafone-15B3:  Infra, <MAC C-01 vodafone-15B3>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2    vodafone-DD18:   Infra, <MAC C-02 vodafone-DD18>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2    eircom92434488:  Infra, <MAC C-NA eircom92434488 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Address:         192.168.1.3    Prefix:          24 (255.255.255.0)    Gateway:         192.168.1.1    DNS:             192.168.1.1------------------------+-------------+--------+-------------+---------+-----------+--------------+----------- eth0                   | Wired       | tg3    | unavailable | no      |           |              | <MAC eth0>------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------

NetworkManager.state ~~~~~~~~~~~~~~~[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnabled=trueWimaxEnabled=true

NetworkManager.conf ~~~~~~~~~~~~~~~~
[main]plugins=ifupdown,keyfile,ofonodns=dnsmasq
no-auto-default=<MAC eth0>,
[ifupdown]managed=false

NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
AndroidHotspot2548   : ssid=AndroidHotspot2548 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto BusEireann_WiFi      : ssid=BusEireann_WiFi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto eduroam              : ssid=eduroam | mac-address=<MAC wlan0> | ipv4=auto Steal your own wifi biatch. : ssid=Steal | autoconnect=false your own wifi biatch. | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto Steal your own wifi biatch. 1 : ssid=Steal your own wifi biatch. | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto vodafone-15B3        : ssid=vodafone-15B3 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore Vodafone_B711        : ssid=Vodafone_B711 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 

interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~
# interfaces(5) file used by ifup(8) and ifdown(8)auto loiface lo inet loopback
resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~
nameserver 127.0.1.1

Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
--- 192.168.1.1 ping statistics ---2 packets transmitted, 2 received, 0% packet loss, time 1001msrtt min/avg/max/mdev = 1.633/2.513/3.394/0.881 ms
--- 127.0.1.1 ping statistics ---2 packets transmitted, 2 received, 0% packet loss, time 999msrtt min/avg/max/mdev = 0.035/0.038/0.041/0.003 ms

iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~
(Region : "en_IE.UTF-8")country 00:	(2402 - 2472 @ 40), (3, 20)	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~
wlan0     26 channels in total; available frequencies :          Channel 01 (2.412 GHz) - 14 (2.484 GHz)          Channel 36 (5.18 GHz)          Channel 38 (5.19 GHz)          Channel 40 (5.2 GHz)          Channel 42 (5.21 GHz)          Channel 44 (5.22 GHz)          Channel 46 (5.23 GHz)          Channel 48 (5.24 GHz)          Channel 149 (5.745 GHz)          Channel 153 (5.765 GHz)          Channel 157 (5.785 GHz)          Channel 161 (5.805 GHz)          Channel 165 (5.825 GHz)
          Current Frequency:2.417 GHz (Channel 2)

iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~
wlan0     Scan completed :          Cell 01 - Address: <MAC C-01 vodafone-15B3>                    Channel:2                    Frequency:2.417 GHz (Channel 2)                    Quality=70/70  Signal level=-3 dBm                      Encryption key:on                    ESSID:"vodafone-15B3"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=0000000000000000                    Extra: Last beacon: 68ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK          Cell 02 - Address: <MAC C-02 vodafone-DD18>                    Channel:3                    Frequency:2.422 GHz (Channel 3)                    Quality=70/70  Signal level=-3 dBm                      Encryption key:on                    ESSID:"vodafone-DD18"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=0000000000000000                    Extra: Last beacon: 68ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK          Cell 03 - Address: <MAC C-03 vodafone-0BDB>                    Channel:4                    Frequency:2.427 GHz (Channel 4)                    Quality=70/70  Signal level=-3 dBm                      Encryption key:on                    ESSID:"vodafone-0BDB"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=0000000000000000                    Extra: Last beacon: 68ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK          Cell 04 - Address: <MAC C-04 SKY417ED>                    Channel:6                    Frequency:2.437 GHz (Channel 6)                    Quality=70/70  Signal level=-3 dBm                      Encryption key:on                    ESSID:"SKY417ED"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=0000000000000000                    Extra: Last beacon: 68ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : PSK          Cell 05 - Address: <MAC C-05 vodafone-D3E8>                    Channel:10                    Frequency:2.457 GHz (Channel 10)                    Quality=70/70  Signal level=-3 dBm                      Encryption key:on                    ESSID:"vodafone-D3E8"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=0000000000000000                    Extra: Last beacon: 68ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK          Cell 06 - Address: <MAC C-06 eircom33355090>                    Channel:11                    Frequency:2.462 GHz (Channel 11)                    Quality=70/70  Signal level=-3 dBm                      Encryption key:on                    ESSID:"eircom33355090"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=0000000000000000                    Extra: Last beacon: 68ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK

blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~
[/etc/modprobe.d/blacklist-ath_pci.conf]blacklist ath_pci
[/etc/modprobe.d/blacklist-bcm43.conf]blacklist b43blacklist b43legacyblacklist ssbblacklist brcm80211blacklist brcmfmacblacklist brcmsmacblacklist bcma

modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[wl]filename:       /lib/modules/3.13.0-46-generic/updates/dkms/wl.kosrcversion:     FF25FE784DC6BDFF69DAFCBdepends:        cfg80211,lib80211parm:           wl_txq_thresh:intparm:           oneonly:intparm:           piomode:intparm:           instance_base:intparm:           nompc:intparm:           intf_name:string
[lib80211]filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/lib80211.kosrcversion:     84DEF767F03D28E373F18E5depends:        
[cfg80211]filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.kosrcversion:     5C139B156678DB83EDA757Ddepends:        parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~
# PCI device 0x14e4:0x16b4 (tg3)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4331 (wl)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

Custom files/entries ~~~~~~~~~~~~~~~
/etc/modules        : Default/etc/rc.local       : Default/etc/modprobe.d     : Not Default/etc/pm/(cnf|pw|sl) : Default
[/etc/modprobe.d]iwlwifi.conf      : remove iwlwifi \                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \                    && /sbin/modprobe -r mac80211mlx4.conf         : softdep mlx4_core post: mlx4_en

Kernel boot line ~~~~~~~~~~~~~~~~~~~
BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic.efi.signed root=UUID=42203c9f-e999-4d51-973e-f2d0684f31c9 ro quiet splash vt.handoff=7

dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[    2.506043] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba[    2.506327] audit: initializing netlink socket (disabled)[    4.094320] tg3 0000:01:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])[   16.679866] wl: module license 'MIXED/Proprietary' taints kernel.[   16.681251] wl: module verification failed: signature and/or  required key missing - tainting kernel[   16.822024] INFO @wl_cfg80211_attach : Registered CFG80211 phy[   16.870957] wlan0: Broadcom BCM4331 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)[   20.835055] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[ 7072.791556] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
	======== Done ========[/PHP][/B]

[FONT=Helvetica Neue]Any help would be greatly appreciated.[/FONT]

---

### Post by ricardo32 on 2015-03-08
BUMP still having an issue :/

---

