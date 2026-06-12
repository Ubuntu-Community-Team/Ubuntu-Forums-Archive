---
title: "mac mini 2006 weak wifi signal rx"
date: 2016-01-29
forum: Apple Hardware Users
---

### Post by piergap on 2016-01-29
hi 
i have mac osx tiger and lubuntu 15.10 running in dual boot on my old upgraded mac mini 2006.

while signal strenght is shown at the maximum in mac os x, it does not look good as well under lubuntu (sometimes even dropping all of a sudden).
the transmitter is quite close then it does not look like this depends on it , and working fine under mac os x as said, anyhow.

i am attaching the wireless report.

any help?
thanks in advance

paolo


report also here below



```


########## wireless info START ##########


Report from: 30 Jan 2016 02:50 CET +0100


Booted last: 30 Jan 2016 00:00 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:32:18 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)
    Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053 [11ab:5321]
    Kernel driver in use: sky2


02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:0086]
    Kernel driver in use: ath5k


##### lsusb #############################


Bus 001 Device 002: ID 0411:01d9 BUFFALO INC. (formerly MelCo., Inc.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8240 Apple, Inc. Built-in IR Receiver
Bus 005 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:0256 Apple, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath5k                 139264  0
ath                    24576  1 ath5k
mac80211              659456  1 ath5k
cfg80211              483328  3 ath,ath5k,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105413545 (105.4 MB)  TX bytes:5963307 (5.9 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"TNCAPC7EB47"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'TNCAPC7EB47' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr off   Fragment thr off
          Power Management off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6723  Invalid misc:5889   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### network managers ##################


Installed:


    NetworkManager


Running:


root       514     1  0 01:19 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express) (AirPort Extreme)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.2.0-25-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TNCAPC7EB47
GENERAL.CON-UUID:                       110bb2b0-2b5a-4892-a7a0-a0a22b045f21
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   110bb2b0-2b5a-4892-a7a0-a0a22b045f21 | TNCAPC7EB47
IP4.ADDRESS[1]:                         192.168.1.71/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
IP4.DNS[2]:                             62.101.93.101
IP4.DNS[3]:                             83.103.25.250
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1454121671
DHCP4.OPTION[9]:                        domain_name = lan
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_lease_time = 3600
DHCP4.OPTION[16]:                       ip_address = 192.168.1.71
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.254 62.101.93.101 83.103.25.250
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan0' [IF]>/64
IP6.GATEWAY:                            
IP6.DNS[1]:                             fe80::9e97:26ff:fec7:eb46
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::9e97:26ff:fec7:eb46
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:f7:ca:9d:63:94:87:7c:e:d6:e7:5b:80:fd:d8:db:ff


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8053 PCI-E Gigabit Ethernet Controller (Marvell RDK-8053)
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TNCAPC7EB47     <MAC 'TNCAPC7EB47' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  43      &#9602;&#9604;__  WPA1 WPA2  yes     * 
WebPocket-BB99  <MAC 'WebPocket-BB99' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TNCAPC7EB47]] (600 root)
[connection] id=TNCAPC7EB47 | type=wifi
[wifi] ssid=TNCAPC7EB47 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


country IT: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


wlan0     21 channels in total; available frequencies :
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
          Current Frequency=2.437 GHz (Channel 6)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TNCAPC7EB47' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key  on
                    ESSID:"TNCAPC7EB47"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000409d32aeca
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TNCAPC7EB47' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key on
                    ESSID:"TNCAPC7EB47"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000041c6e17a0a
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WebPocket-BB99' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key on
                    ESSID:"WebPocket-BB99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000329cb3a173
                    Extra: Last beacon: 21872ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath5k]
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     771FA960E4882771F544E8B
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        CB:91:74:39:37:0C:6F:04 D9:29:34:8A:CD:6C:76:18:AA:26:BC:07
sig_hashalgo:   sha512
parm:           nohwcrypt disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        CB:91:74:39:37:0C:6F:04 D9:29:34:8A:CD:6C:76:18:AA:26:BC:07
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        CB:91:74:39:37:0C:6F:04:D9:29:34:8A:CD:6C:76:18:AA:26:BC:07
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        CB:91:74:39:37:0C:6F:04:D9:29:34:8A:CD:6C:76:18:AA:26:BC:07
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
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   12.588342] ath5k 0000:02:00.0: registered as 'phy0'
[   12.831986] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.834435] sky2 0000:01:00.0 eth0: enabling interface
[   12.834589] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.575603] ath: EEPROM regdomain: 0x65
[   13.575608] ath: EEPROM indicates we should expect a direct regpair map
[   13.575611] ath: Country alpha2 being used: 00
[   13.575613] ath: Regpair used: 0x65
[   13.604238] ath5k: phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)
[   13.634912] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   16.169547] wlan0: authenticate with <MAC 'TNCAPC7EB47' [AC1]>
[   16.173447] wlan0: send auth to <MAC 'TNCAPC7EB47' [AC1]> (try 1/3)
[   16.175659] wlan0: authenticated
[   16.176294] wlan0: associate with <MAC 'TNCAPC7EB47' [AC1]> (try 1/3)
[   16.178929] wlan0: RX AssocResp from <MAC 'TNCAPC7EB47' [AC1]> (capab=0x431 status=0 aid=4)
[   16.179037] wlan0: associated
[   16.179073] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.183577] ath: EEPROM regdomain: 0x817c
[   16.183583] ath: EEPROM indicates we should expect a country code
[   16.183585] ath: doing EEPROM country->regdmn map search
[   16.183587] ath: country maps to regdmn code: 0x37
[   16.183589] ath: Country alpha2 being used: IT
[   16.183590] ath: Regpair used: 0x37
[   16.183592] ath: regdomain 0x817c dynamically updated by country IE
[ 1030.007596] ath5k: ath5k_hw_get_isr: ISR: 0x00000080 IMR: 0x00000000 (repeated 3 times)


########## wireless info END ############

```

---

### Post by Benjamin_Brink on 2016-02-09
This may be a reception issue. See what channel is used by osx wifi when reception is good.  Try switching to same wifi channel in ubuntu.

---

