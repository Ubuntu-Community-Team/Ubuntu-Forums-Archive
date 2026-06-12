---
title: "Wifi works only when next to router"
date: 2019-08-08
forum: Apple Hardware Users
---

### Post by jaythewicked719 on 2019-08-08
I followed along to a reply to a thread here : [https://ubuntuforums.org/showthread.php?p=13024222#post13024222](https://ubuntuforums.org/showthread.php?p=13024222#post13024222)

It suggested making a wireless-info.txt file and providing the info it generated.

Below is the text provided:



```
########## wireless info START ##########


Report from: 08 Aug 2019 19:52 CDT -0500


Booted last: 08 Aug 2019 00:00 CDT -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-58-generic #64-Ubuntu SMP Tue Aug 6 11:10:46 UTC 2019 i686 i686 i686 GNU/Linux


Parameters: ro, i8042.reset, quiet, splash


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


Bus 001 Device 003: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. Built-in IR Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:0217 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


ath5k                 135168  0
ath                    24576  1 ath5k
mac80211              679936  1 ath5k
cfg80211              532480  3 mac80211,ath,ath5k


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
3: wls1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wls1' [IF2]> brd <MAC address>
    inet 192.168.1.49/24 brd 192.168.1.255 scope global dynamic noprefixroute wls1
       valid_lft 77290sec preferred_lft 77290sec
    inet6 fe80::1b05:549e:d706:bb97/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


enp1s0    no wireless extensions.


lo        no wireless extensions.


wls1      IEEE 802.11  ESSID:"Asstastic"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Asstastic' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4672  Invalid misc:19637   Missed beacon:0


##### route #############################


default via 192.168.1.1 dev wls1 proto dhcp metric 600 
169.254.0.0/16 dev wls1 scope link metric 1000 
192.168.1.0/24 dev wls1 proto kernel scope link src 192.168.1.49 metric 600 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']


nameserver 127.0.0.53
search Home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       912     1  0 17:20 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wls1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express) (AirPort Extreme)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.15.0-58-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wls1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wls1
GENERAL.IP-IFACE:                       wls1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Asstastic
GENERAL.CON-UUID:                       52ac8ca0-6137-4a7d-a613-dcf0ea1ce183
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     24 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
IP4.ADDRESS[1]:                         192.168.1.49/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.1.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        domain_name = Home
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        requested_domain_name = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       expiry = 1565389266
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       ip_address = 192.168.1.49
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       dhcp_message_type = 5
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[28]:                       domain_name_servers = 192.168.1.1 192.168.1.1
IP6.ADDRESS[1]:                         fe80::1b05:549e:d706:bb97/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   52ac8ca0-6137-4a7d-a613-dcf0ea1ce183 | Asstastic


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8053 PCI-E Gigabit Ethernet Controller (Marvell RDK-8053)
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID       BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Asstastic  <MAC 'Asstastic' [AC1]>  Infra  11    2462 MHz  130 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  yes     *      


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/CGNM-F0E8]] (600 root)
[connection] id=CGNM-F0E8 | type=wifi | permissions=user:jeff:;
[wifi] mac-address=<MAC 'wls1' [IF2]> | mac-address-blacklist= | ssid=CGNM-F0E8
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Asstastic]] (600 root)
[connection] id=Asstastic | type=wifi | permissions=user:jeff:;
[wifi] mac-address=<MAC 'wls1' [IF2]> | mac-address-blacklist= | ssid=Asstastic
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CGN-2F30]] (600 root)
[connection] id=CGN-2F30 | type=wifi | permissions=user:jeff:;
[wifi] mac-address=<MAC 'wls1' [IF2]> | mac-address-blacklist= | ssid=CGN-2F30
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Deicious time wifi ]] (600 root)
[connection] id=Deicious time wifi  | type=wifi | permissions=user:jeff:;
[wifi] mac-address=<MAC 'wls1' [IF2]> | mac-address-blacklist= | ssid=Deicious time wifi 
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


global
country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp1s0    no frequency information.


lo        no frequency information.


wls1      24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.462 GHz (Channel 11)


##### iwlist scan #######################


enp1s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wls1      Scan completed :
          Cell 01 - Address: <MAC 'Asstastic' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Asstastic"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000033c9748b5
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Torres' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Torres"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dbdb66183
                    Extra: Last beacon: 9420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath5k]
filename:       /lib/modules/4.15.0-58-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     EAFCEE7103896A354CF44A7
depends:        mac80211,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath5k
vermagic:       4.15.0-58-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/4.15.0-58-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A592EBDEEE43676A2F56015
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-58-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[mac80211]
filename:       /lib/modules/4.15.0-58-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FDB9FBFE52A6192B8CC9B9E
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-58-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.15.0-58-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     34711E0450EF391760E5E7A
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-58-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/AR242x.conf]
options AR242x fwlps=N


[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=1


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   94.589435] wls1: authenticate with <MAC 'Asstastic' [AC1]>
[   94.600918] wls1: send auth to <MAC 'Asstastic' [AC1]> (try 1/3)
[   94.608298] wls1: authenticated
[   94.612106] wls1: associate with <MAC 'Asstastic' [AC1]> (try 1/3)
[   94.620670] wls1: RX AssocResp from <MAC 'Asstastic' [AC1]> (capab=0x411 status=0 aid=1)
[   94.620799] wls1: associated
[   94.620967] ath: EEPROM regdomain: 0x8348
[   94.620970] ath: EEPROM indicates we should expect a country code
[   94.620973] ath: doing EEPROM country->regdmn map search
[   94.620976] ath: country maps to regdmn code: 0x3a
[   94.620978] ath: Country alpha2 being used: US
[   94.620980] ath: Regpair used: 0x3a
[   94.620983] ath: regdomain 0x8348 dynamically updated by country IE
[   94.720635] IPv6: ADDRCONF(NETDEV_CHANGE): wls1: link becomes ready
[   94.721601] wls1: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'Asstastic' [AC1]>


########## wireless info END ############

```

I would like to get the distance i had before going to linux. I am working with a late 2007 model macbook a1181. currently on Ubuntu 18.04. anything to get my wifi distance back is greatly appreciated.

---

### Post by wildmanne39 on 2019-08-08
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2019-08-08
Please do:
```
echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

Does that help?

---

### Post by jaythewicked719 on 2019-08-08
upon attempting your requested tip i came across an error

```
 sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/networkmanager/conf.d/default-wifi-powersave-on.confsed: can't read /etc/networkmanager/conf.d/default-wifi-powersave-on.conf: No such file or directory

```

---

