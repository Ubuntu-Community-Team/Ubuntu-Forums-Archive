---
title: "Problem with high-power wireless-g usb adapter and synaptic"
date: 2011-12-05
forum: Any Other OS
---

### Post by run2thehills2001 on 2011-12-05
Hi to everyone! I'm new to Ubuntu 11.04 and I think I really like it... So I have a problem with my wifi usb card...

My pc's specs are:
Motherboard: GA-P35C-DS3R
Proccessor: Intel(R) Core(TM)2 Quad CPU Q6600 @2.40Ghz 2.40GHz
Ram:4GB

So the problem has to do with my wifi usb card "High-Power wireless-g USB adapter High Gain"
It uses the Realtek rtl8187 driver.

After  I first installed Ubuntu 11.04, as a side along to MS Windows 7, using your  guides, whenever I log into the desktop on Ubuntu 11.04, I can use the  internet and everything is just fine. The only problem is that when  synaptic manager tries to connect on the net to download any updates  then I no longer can connect to the internet. Even if I just click on the shield icon of synaptic, I almost everytime loose connection instantly, but now every time. So, when this happens, no internet application  can get an ip, but looking the wifi signal on the system tray,  everything seems to be ok. I have tried other networks and I have tried  other OS's...[IMG]http://forums.linuxmint.com/images/smilies/icon_razz.gif[/IMG]  I've tried Mint 11 x32, Mint 11 x 64, Ubuntu 11 x32, Ubuntu 11 x64.  This is a desktop not a notebook. So I cannot move it. On the other hand  my router is much far away and behind 3 walls. That's why I bought that  usb wifi card which has an high gain antenna and I get a very good  signal.(up to 90%). In addition, I've noticed that even though the  problem persists through even different linux OS's, when I restart the  pc or even just unplug the usb wifi card and plug it in back again, then  I have a connection again. In Mint 11, I 've noticed Something even more weird. That is that I CAN  download packages but only if I download them and install them using the  new search bar which is built in the new Mint menu. (You know... where  you can type something and mint is looking for it on wiki, google, on  your harddrives or in the repositories. 

So, to sum it all up, I  can get to the net, but if synaptic manager tries to do it's job(or if I  try to download something for the software centre)then I loose  connection until I restart the system(logging out and back in, doesnt do  the trick every time) or unplug the usb card. 

I'd like to add that even  when I CAN be online the connection is too slow compared to the speed it  reaches when I 'm on windows 7. I don't know if this is relevant at  all.

Something more is that I already have Windows 7 on this same  system and the antenna works fine from where it already is. I never had  a problem. The problem appears only on linux systems. The only thing is  that I don't like MS and I love Linux especially  Mint and Ubuntu, so I'd really  like to find a way to fix this.

Please, help me with this while  bearing in mind that I am a complete newbie. I know almost nothing  related to terminal, except for copying and pasting commands...[IMG]http://forums.linuxmint.com/images/smilies/icon_razz.gif[/IMG]

P.S.: About my usb card's driver support:
I  have a cd with the drivers including drivers for linux systems,too, but  the installation notes tell me to run some x-shellscripts, and I have  no idea how to do that. I've searched all over the net and I have  accoplished nothing.

P.S.(2): After 2 months of trying and searching the net, tampering with everything I can...:P I found out something more about my system:

In network tools I get 2 devices:
wlan0: I figured out that this is a wireless pci card I have that I never use anymore cuz on windows it seems to get no signal at all from where the router is. That's why I bought the USB wifi Antenna which gets much better signal. This one uses some driver called hostap_pci or something...

wlan1: This one is the usb wifi antenna I need to use and which gives me all this trouble. It needs to use rtl8187.

---

### Post by run2thehills2001 on 2011-12-05
Some more info I get when I run nm-tool. I hope it is helpful cuz I  don't understand almost anything. I remind everyone I'm a total newbie,  especially concerning terminal.[IMG]http://forums.linuxmint.com/images/smilies/icon_wink.gif[/IMG]

diamond@diamond-P35C-DS3R ~ $     nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1A:4D:52:31:DC

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto ThomsonDB7376] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            hostap_pci
  State:             connected
  Default:           yes
  HW Address:        00:0E:6A:7A:DA:2F

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ThomsonDB7376:  Infra, 00:1F:9F:CF:A7:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    daniilidis:      Infra, 00:26:44:3C:F1:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WEP
    LINKSYS:         Infra, 00:1E:E5:9A:C4:6E, Freq 2462 MHz, Rate 22 Mb/s, Strength 30 WEP
    HOL ALU WLAN:    Infra, A6:3E:61:82:27:A3, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WEP
    Oxygen-45167:    Infra, 00:1D:1C:B4:32:CB, Freq 2452 MHz, Rate 11 Mb/s, Strength 30 WEP
    NetFasteR WLAN:  Infra, D0:15:4A:1A:48:9E, Freq 2462 MHz, Rate 18 Mb/s, Strength 32 WEP

  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan1  [Auto ThomsonDB7376] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           no
  HW Address:        00:0F:04:B1:04:4F

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    nasos:           Infra, 00:22:6B:E4:F2:B8, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WEP
    NetFasteR IAD 2 (PSTN): Infra, 00:05:59:41:41:33, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    Thomson0FC30F:   Infra, 00:24:17:B2:6A:73, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    *ThomsonDB7376:  Infra, 00:1F:9F:CF:A7:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 67
    zaph:            Infra, 00:11:7C:0C:30:45, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA
    Thomson487B18:   Infra, 00:26:44:48:7B:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 75
    Oxygen-45167:    Infra, 00:1D:1C:B4:32:CB, Freq 2452 MHz, Rate 54 Mb/s, Strength 71 WPA2
    Thomson8C9790:   Infra, 00:26:44:1D:E9:DD, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    NetFasteR WLAN:  Infra, D0:15:4A:1A:48:9E, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    LINKSYS:         Infra, 00:1E:E5:9A:C4:6E, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA2
    HOL ALU WLAN:    Infra, A6:3E:61:82:27:A3, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254




and some additional info from the script collectNWData.sh

I  should also say that I've noticed that when i am online the speed sucks  compered to the speed i get from the same system on windows 7...


collectNWData.sh V0.6.5.4.6 (Rev: 1.299, Build: 2011-11-20 18:25:03 UTC)
--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0120E: Network card wlan0 has no IP address
!!! CND0180I: The system can't ping external IP address 195.135.220.3
!!! CND0150E: There might be a problem with the default gateway definition 192.168.1.254 on interface wlan1
!!!  CND0450W: WLAN key masquerading is not fully tested on this  distribution. Please check output file collectNWData.txt for visible  WLAN keys and masquerade them manually

--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
===== cat /etc/*[-_]release || cat /etc/*[-_]version =============================================================
/etc/lsb-release
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=11
DISTRIB_CODENAME=katya
DISTRIB_DESCRIPTION="Linux Mint 11 Katya"
===== uname -a ===================================================================================================
Linux diamond-P35C-DS3R 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
===== lspci ======================================================================================================
04:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  01)
   Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
   Kernel driver in use: r8169
--
05:01.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
   Subsystem: 3Com Corporation Device [10b7:0001]
   Kernel driver in use: hostap_pci
===== lsusb | grep -v "root hub" =================================================================================
Bus 008 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 005 Device 002: ID 0ccd:0014 TerraTec Electronic GmbH PHASE 26
Bus 004 Device 002: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 002 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203
Bus 001 Device 002: ID 0c45:62f1 Microdia 
===== lshw -C network (filtered) =================================================================================
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
        capabilities: pm vpd msi pciexpress bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=32 multicast=yes wireless=IEEE 802.11b
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=rtl8187  driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.66 link=yes  multicast=yes wireless=IEEE 802.11bg
===== lsmod (filtered) ===========================================================================================
| ahci            | arc4            | binfmt_misc     | btrfs           | cfg80211         |
| drm             | drm_kms_helper  | eeprom_93cx6    | hid             | hostap           |
| hostap_pci      | i2c_algo_bit    | ir_jvc_decoder  | ir_lirc_codec   | ir_nec_decoder   |
| ir_rc5_decoder  | ir_rc6_decoder  | ir_sony_decoder | isofs           | lib80211         |
| libahci         | lirc_dev        | lp              | mac80211        | ndiswrapper      |
| nouveau         | ppdev           | r8169           | rc_core         | rtl8187          |
| saa7134         | saa7134_alsa    | serio_raw       | tda827x         | tda8290          |
| ttm             | tuner           | tveeprom        | uas             | usb_storage      |
| v4l2_common     | v4l2_compat_ioctl32| zlib_deflate    |
===== ls /lib/firmware/* =========================================================================================
| 2.6.38-8-generic        | 3com                    | acenic                  | adaptec                  |
| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |
| ar3k                    | ar7010_1_1.fw           | ar7010.fw               | ar9170-1.fw              |
| ar9170-2.fw             | ar9170.fw               | ar9271.fw               | asihpi                   |
| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |
| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | bnx2                     |
| bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.13.0.fw    | bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw    |
| bnx2x-e1h-5.2.13.0.fw   | bnx2x-e1h-5.2.7.0.fw    | brcm                    | carl9170-1.fw            |
| cis                     | cpia2                   | cxgb3                   | dabusb                   |
| dsp56k                  | dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                     |
| ea                      | edgeport                | emi26                   | emi62                    |
| ess                     | f2255usb.bin            | GPL-3                   | hp                       |
| i2400m-fw-usb-1.4.sbcf  | i2400m-fw-usb-1.5.sbcf  | i6050-fw-usb-1.5.sbcf   | intelliport2.bin         |
| ipw2100-1.3.fw          | ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw           |
| ipw2200-ibss.fw         | ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-1000-5.ucode     |
| iwlwifi-100-5.ucode     | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode     |
| iwlwifi-5000-2.ucode    | iwlwifi-5000-5.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode     |
| iwlwifi-6000g2a-5.ucode | iwlwifi-6000g2b-5.ucode | iwlwifi-6050-4.ucode    | iwlwifi-6050-5.ucode     |
| kaweth                  | keyspan                 | keyspan_pda             | korg                     |
| lgs8g75.fw              | libertas                | matrox                  | mrvl                     |
| mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw              | mts_mt9234mu.fw          |
| mts_mt9234zba.fw        | mwl8335_duplex.fw       | mwl8k                   | myricom                  |
| NPE-B                   | NPE-C                   | ositech                 | phanfw.bin               |
| ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin           | ql2322_fw.bin            |
| ql2400_fw.bin           | ql2500_fw.bin           | qlogic                  | r128                     |
| radeon                  | rt2561.bin              | rt2561s.bin             | rt2661.bin               |
| rt2860.bin              | rt2870.bin              | rt3070.bin              | rt3071.bin               |
| rt3090.bin              | rt73.bin                | RTL8192E                | RTL8192SE                |
| rtl_nic                 | rtlwifi                 | s2250.fw                | s2250_loader.fw          |
| sb16                    | scripts                 | slicoss                 | sun                      |
| sxg                     | tehuti                  | ti_3410.fw              | ti_5052.fw               |
| ti-connectivity         | tigon                   | tlg2300_firmware.bin    | tr_smctr.bin             |
| ttusb-budget            | ueagle-atm              | usbdux                  | usbduxfast_firmware.bin  |
| usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw       |
| v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg     |
| v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw  |
| v4l-pvrusb2-29xxx-01.fw | vicam                   | vntwusb.fw              | vxge                     |
| WHENCE.ubuntu           | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
===== ifconfig (filtered for eth|wlan|ra|ath|dsl) ================================================================
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x2000 
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#3  
          inet6 addr: fe80::20e:6aff:fe7a:da2f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40801593 (40.8 MB)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe000 
wlan1     Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:4ff:feb1:44f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1597456 (1.5 MB)  TX bytes:549565 (549.5 KB)
===== iwconfig ===================================================================================================
lo        no wireless extensions.
eth0      no wireless extensions.
wifi0     IEEE 802.11b  ESSID:"\x05\xEF\xF7"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: None   
          Bit Rate:5.5 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
wlan0     IEEE 802.11b  ESSID:"\x05\xEF\xF7"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: None   
          Bit Rate:5.5 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=2/70  Signal level=-96 dBm  Noise level=-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:679  Invalid misc:34103   Missed beacon:0
wlan1     IEEE 802.11bg  ESSID:"§§§§§§§§3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: ##:##:##:##:##:#4   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:70  Invalid misc:75   Missed beacon:0
===== cat /etc/network/interfaces | grep -v "=''" ================================================================
--- /etc/network/interfaces
auto lo
iface lo inet loopback
===== iwlist scanning ============================================================================================
                    ESSID:"§§§§§§§§4"
                    Encryption key:on
                    ESSID:"§§§§§§§§3"
                    Encryption key:off
                    ESSID:"§§§§§§§§5"
                    Encryption key:on
                    ESSID:"§§§§§§§§6"
                    Encryption key:on
                    Channel:6
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"§§§§§§§§3"
                    Channel:1
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§7"
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
                    Channel:6
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"NetFasteR IAD 2 (PSTN)"
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
                    Channel:9
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§4"
                    IE: IEEE 802.11i/WPA2 Version 1
                    Channel:11
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§9"
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
                    Channel:11
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§6"
                    IE: IEEE 802.11i/WPA2 Version 1
                    Channel:1
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"§§§§§§§§10"
                    Channel:11
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§5"
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
===== ndiswrapper -l =============================================================================================
===== Active processes ===========================================================================================
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
===== Active WPA processes =======================================================================================
/sbin/wpa_supplicant -u -s
===== ping tests =================================================================================================
Ping of 195.135.220.3 failed
ping: unknown host [www.suse.de]("http://www.suse.de")
Ping of [www.suse.de]("http://www.suse.de") failed
===== cat /etc/resolv | grep -i "nameserver" =====================================================================
nameserver 192.168.1.254
===== cat /etc/hosts =============================================================================================
127.0.0.1   localhost
127.0.1.1   diamond-P35C-DS3R
===== route -n | egrep "(eth|ath|ra|wlan|dsl)" ===================================================================
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan1
===== Actual date for bias of following greps ====================================================================
14:40:43 2011-12-04
===== grep -i radio /var/log/syslog* | tail -n 5 =================================================================
/var/log/syslog.1:Nov  15 09:08:09 diamond-P35C-DS3R NetworkManager[890]: <info> WiFi  enabled by radio killswitch; enabled by state file
/var/log/syslog.1:Nov  15 09:08:09 diamond-P35C-DS3R NetworkManager[890]: <info> WWAN  enabled by radio killswitch; enabled by state file
/var/log/syslog.1:Nov  15 09:08:09 diamond-P35C-DS3R NetworkManager[890]: <info> WiMAX  enabled by radio killswitch; enabled by state file
/var/log/syslog.1:Nov 15 09:08:16 diamond-P35C-DS3R kernel: [   27.470332] saa7133[0]: registered device radio0
/var/log/syslog.1:Dec   4 13:56:04 diamond-P35C-DS3R NetworkManager[995]: <info> WiFi  enabled by radio killswitch; enabled by state file
/var/log/syslog.1:Dec   4 13:56:04 diamond-P35C-DS3R NetworkManager[995]: <info> WWAN  enabled by radio killswitch; enabled by state file
/var/log/syslog.1:Dec   4 13:56:04 diamond-P35C-DS3R NetworkManager[995]: <info> WiMAX  enabled by radio killswitch; enabled by state file
/var/log/syslog.1:Dec  4 13:56:11 diamond-P35C-DS3R kernel: [   27.480223] saa7133[0]: registered device radio0
/var/log/syslog.1:Dec   4 14:10:04 diamond-P35C-DS3R NetworkManager[995]: <info> found  WiFi radio killswitch rfkill0 (at  /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/ieee80211/phy0/rfkill0)  (driver <unknown>)
/var/log/syslog.1:Dec  4 14:10:04 diamond-P35C-DS3R kernel: [  859.968459] Registered led device: rtl8187-phy0::radio
===== dmesg | grep -i radio | tail -n 5 ==========================================================================
[   27.480223] saa7133[0]: registered device radio0
[  859.968459] Registered led device: rtl8187-phy0::radio
===== tail -n 300 /var/log/syslog* | /bin/grep -i firmware | tail -n 10 ==========================================
===== egrep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net* ==============
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#3",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#5",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
===== egrep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*|egrep -v -i '#|backlist' ================
==================================================================================================================
*** NWElizaStates V0.6.5.4.6
IF:eth0  IM:1 IF:wlan0 IM:2 IF:wlan1 IM:2 DI:3 AP:2 FALON:1 NIC:1 cNiC:2:1 NIC:0  cNiC:3:0 NI:0 cNI:0 PNG:1 DR:1 MTU:0 NISS:0 IP6:0 WLW:0 RTDT:debian

---

### Post by run2thehills2001 on 2011-12-05
I had another idea about how coping with this problem. My wifi card came  with a cd. This includes some files for installing the proper drivers  of the wificard but I don't know how to do any of what the readme file  says... I'll post here the readme file from the cd of the card and if  anybody is up to it, plz explain to me how to do the steps in as much  detail as possible. for instance it includes running some scripts. I  have no idea how to do that. At first I figured that I might as well  double click on them but all that happens is that gedit opens with some  lines of code and then I don't know what to do next. 

So here is the readme file:

Release Date: 2006-02-09, ver 1.2

RTL8187 Linux driver version 1.2



   --This driver supports RealTek RTL8187 Wireless LAN driver for 

     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 

     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc.

   - Support Client mode for either infrastructure or adhoc mode

   - Support WEP and WPAPSK connection



< Component >

The driver is composed of several parts:

	1. Module source code

	  stack.tar.gz

	  drv.tar.gz

	

	2. Script ot build the modules

	  makedrv



	3. Script to load/unload modules

	  wlan0up

	  wlan0down 



	4. Script and configuration for DHCP

 	  wlan0dhcp

	  ifcfg-wlan0

	4. Supplicant source code:

	  wpa_supplicant-0.4.9.tar.gz



	5. Example of supplicant configuration file:

	  wpa1.conf



< Installation >

Runing the scripts can finish all operations of building up modules 

from the source code and start the nic.

	1. Build up the drivers from the source code

	  ./makedrv



	2. load the driver module to kernel and start up nic

	  ./wlan0up



< Set wireless lan MIBs >

This driver uses Wireless Extension as an interface allowing you to set

Wireless LAN specific parameters.



Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]

where

        parameter explaination      	[parameters]    

        -----------------------     	-------------   

        Show available chan and freq	freq / channel  

        Show and Scan BSS and IBSS 	scan[ning]          

        Show supported bit-rate         rate / bit[rate]        

        Show Power Management mode      power             



For example:

	iwlist wlan0 channel

	iwlist wlan0 scan

	iwlist wlan0 rate

	iwlist wlan0 power



Driver also supports "iwconfig", manipulate driver private ioctls, to set

MIBs.



	iwconfig wlan0 [parameters] [val]

where

	parameter explaination      [parameters]        [val] constraints

        -----------------------     -------------        ------------------

        Connect to AP by address    ap              	[mac_addr]

        Set the essid, join (I)BSS  essid             	[essid]

        Set operation mode          mode                {Managed|Ad-hoc}

        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}



For example:

	iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

	iwconfig wlan0 essid "ap_name"

	iwconfig wlan0 mode Ad-hoc

	iwconfig wlan0 mode essid "name" mode Ad-hoc

	iwconfig wlan0 key 0123456789 [2] open

	iwconfig wlan0 key off

	iwconfig wlan0 key restricted [3] 0123456789



< Getting IP address >

After start up the nic, the network needs to obtain an IP address before

transmit/receive data.

This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS"

command, or using DHCP.



If using DHCP, setting steps is as below:

	(1)connect to an AP via "iwconfig" settings

		iwconfig wlan0 essid [name]	or

		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX



	(2)run the script which run the dhclient

		./wlan0dhcp

           or 

		dhcpcd wlan0

              	(Some network admins require that you use the

              	hostname and domainname provided by the DHCP server.

              	In that case, use 

		dhcpcd -HD wlan0)

		

< WPAPSK >

WPA_SUPPLICANT help the network to communicate under the protection of WPAPSK

mechanism

	

	(1)Unpack source code of WPA supplicant:

	  tar -zxvf wpa_supplicant-0.4.9.tar.gz

	  cd wpa_supplicant-0.4.9

	

	(2)Create .config file:

	  cp defconfig .config

	

	(3)Edit .config file, uncomment the following line:

	  #CONFIG_DRIVER_IPW=y.

		

	(4)Build WPA supplicant:

	  make

	If make error for lack of <include/md5.h>, install the openssl lib(two ways):

	 1. Install the openssl lib from corresponding installation disc:

	    Fedora Core 2/3/4/5(openssl-0.9.71x-xx), Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),

	    Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), Gentoo(dev-libs/openssl), etc.

	 2. Download the openssl open source package from [www.openssl.org]("http://www.openssl.org/"), build and install it.

	 

	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.

	  For example, the following setting in "wpa1.conf" means SSID 

          to join is "BufAG54_Ch6" and its passphrase is "87654321".

	  network={

			ssid="BufAG54_Ch6"

			proto=WPA

			key_mgmt=WPA-PSK

			pairwise=CCMP TKIP

			group=CCMP TKIP WEP104 WEP40

			psk="87654321"

			priority=2

		  }



	(6)Execute WPA supplicant (Assume 8187 and related modules had been

           loaded):

	  ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &

---

### Post by Perfect Storm on 2011-12-05
Moved to Other OS/Distro Talk.

---

### Post by run2thehills2001 on 2011-12-07
I just want to add that a little while ago I had an idea about the two cards. I thought "What if the PCI card is somehow conflicting with the USB card?" So I removed completely from my tower the PCI card. After that for about half an hour I got to establish a very good connection via the USB card with no drops. In the meantime I downloaded some updates from the update manager and I browsed a little via Firefox. All this time I managed to reach up to 130KBytes per sec, while from windows I manage to reach up to 700-800KBps... Anyhow, after about 30-40 minutes it dropped again and since then I couldn't get to establish a decent connection. The only thing it did, was that it seemed to getting a new IP every 30", the download speed peaked momentarily(1-2 secs), and then 0Bytes/sec (download speed) again. I tried to reconnect again and again, but with no luck... 

In the meantime I'd like to mention as well, that when I open Connection Information, it says that the driver in use is rtl8187 and this is the driver the card requires to operate correctly... So, what does this mean? Does it mean that the driver is installed correctly? If so, wtf is not working correctly with my USB-card? 

Plz anybody help me cuz, I'm getting more and more frustrated about this matter... And it's a shame not to use Ubuntu just because the wifi usb card is denying to operate as it should... I remind everyone that there is no hardware issue with the usb card cuz I use it on my Windows OS and it works just fine...


Plz plz plz help, anyone... Any ideas at all?

---

