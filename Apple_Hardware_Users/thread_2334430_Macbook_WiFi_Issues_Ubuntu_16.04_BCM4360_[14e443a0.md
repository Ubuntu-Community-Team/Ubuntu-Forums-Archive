---
title: "Macbook WiFi Issues Ubuntu 16.04 BCM4360 [14e4:43a0] (rev 03)"
date: 2016-08-19
forum: Apple Hardware Users
---

### Post by betores on 2016-08-19
Hey folks,

I'm having issues with WiFi on my Macbook Air 6,2. I'm able to connect using both the broadcom-sta-dkms and bcmwl-kernel-source drivers (hooray!). When I first connect, I have the same speeds as I get on OSX (20-50mbps), but after about 30 seconds of being connected, the speed drops off to 1-2mbps and stays there.

I've tried many things: different drivers, disabling power management, using WICD instead of network manager, turning off IPv6, disabling 802.11n, but the problem persists. I really hope I can find a solution as 1mbps means no more Ubuntu :(

Here's the wireless-info output:

```

########## wireless info START ##########

Report from: 19 Aug 2016 15:04 BST +0100

Booted last: 19 Aug 2016 00:00 BST +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b:0117]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:0291 Apple, Inc. 
Bus 001 Device 006: ID 05ac:828f Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
9: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
10: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              565248  1 wl

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF1]>  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3a8c:3c62:d722:5839/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14212 errors:0 dropped:0 overruns:0 frame:1081
          TX packets:8831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19017044 (19.0 MB)  TX bytes:905220 (905.2 KB)
          Interrupt:18 

##### iwconfig ##########################

lo        no wireless extensions.

wlp3s0    IEEE 802.11abg  ESSID:"PLUSNET-CJ6MPG"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'PLUSNET-CJ6MPG' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2459     1  0 14:07 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4360 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     PLUSNET-CJ6MPG
GENERAL.CON-UUID:                       cc5e31e2-c43a-4139-b12c-b13ea4a44d71
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     39 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cc5e31e2-c43a-4139-b12c-b13ea4a44d71 | PLUSNET-CJ6MPG
IP4.ADDRESS[1]:                         192.168.1.1/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1471701677
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.1
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = lan
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::3a8c:3c62:d722:5839/64
IP6.GATEWAY:                            

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
PLUSNET-CJ6MPG   <MAC 'PLUSNET-CJ6MPG' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2              yes     * 
TALKTALK9297AE   <MAC 'TALKTALK9297AE' [AC9]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
BTWifi-X         <MAC 'BTWifi-X' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2 802.1X  no        
BTWifi-with-FON  <MAC 'BTWifi-with-FON' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  --                no        
BTHub5-THZQ      <MAC 'BTHub5-THZQ' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2              no        
SKY9A693         <MAC 'SKY9A693' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2              no        
SKYAE68B         <MAC 'SKYAE68B' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2              no        
BTHub5-THZQ      <MAC 'BTHub5-THZQ' [AC10]>  Infra  48    5240 MHz  54 Mbit/s  17      &#9602;___  WPA2              no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/PLUSNET-CJ6MPG]] (600 root)
[connection] id=PLUSNET-CJ6MPG | type=wifi | permissions=user:abra:;
[wifi] mac-address=<MAC 'wlp3s0' [IF1]> | mac-address-blacklist= | ssid=PLUSNET-CJ6MPG
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Channel 108 : 5.54 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.24 GHz (Channel 48)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'PLUSNET-CJ6MPG' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"PLUSNET-CJ6MPG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-31-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/pm/config.d/blacklist] (644 root)
HOOK_BLACKLIST="wireless"

##### udev rules ########################

##### dmesg #############################

[ 1929.157932] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[ 1929.158033] wlp3s0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[ 1929.182227] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2118.803551] wlan0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[ 2118.803567] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[ 2118.827025] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3212.671305] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[ 3212.671348] wlp3s0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[ 3212.691555] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3243.393388] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)

########## wireless info END ############


```

---

### Post by betores on 2016-08-20
Bump.

---

### Post by howefield on 2016-08-20
Thread moved to the "*Apple Hardware Users*" forum.

---

