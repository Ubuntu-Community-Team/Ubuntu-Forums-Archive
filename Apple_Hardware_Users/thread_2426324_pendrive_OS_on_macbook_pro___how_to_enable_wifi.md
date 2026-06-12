---
title: "pendrive OS on macbook pro _ how to enable wifi"
date: 2019-09-07
forum: Apple Hardware Users
---

### Post by samuelealbani on 2019-09-07
Hi!
I installed Ubuntu 19 on a 16GB pendrive and I'm using it with my macbook pro mid 2012.
How can I enable wifi?

this is the result of the wireless script:
```


########## wireless info START ##########

Report from: 07 Sep 2019 13:10 CEST +0200

Booted last: 07 Sep 2019 00:00 CEST +0200

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco

##### kernel ############################

Linux 5.0.0-27-generic #28-Ubuntu SMP Tue Aug 20 19:53:07 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Inc. and subsidiaries NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00f5]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 006: ID 05ac:0253 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

This system doesn't support Secure Boot

##### lsmod #############################

b43                   413696  0
mxm_wmi                16384  1 nouveau
wmi                    28672  2 mxm_wmi,nouveau
cordic                 16384  1 b43
mac80211              806912  1 b43
cfg80211              671744  2 b43,mac80211
ssb                    69632  1 b43
bcma                   57344  1 b43

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
2: enp2s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'enp2s0f0' [IF1]> brd <MAC address>
    inet 192.168.0.101/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0f0
       valid_lft 258393sec preferred_lft 258393sec
    inet6 fe80::4d53:26d3:1690:e423/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp2s0f0  no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp2s0f0 proto dhcp metric 100 
169.254.0.0/16 dev enp2s0f0 scope link metric 1000 
192.168.0.0/24 dev enp2s0f0 proto kernel scope link src 192.168.0.101 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       934     1  0 12:19 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Inc. and subsidiaries
GENERAL.PRODUCT:                        NetXtreme BCM57765 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               57765-v1.37
GENERAL.HWADDR:                         <MAC 'enp2s0f0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0f0
GENERAL.IP-IFACE:                       enp2s0f0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       150fdeb3-16dd-338a-bfa8-992a3756e9c4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.101/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[2]:                        dad_wait_time = 0
DHCP4.OPTION[3]:                        dhcp_lease_time = 259200
DHCP4.OPTION[4]:                        dhcp_message_type = 5
DHCP4.OPTION[5]:                        dhcp_rebinding_time = 226800
DHCP4.OPTION[6]:                        dhcp_renewal_time = 129600
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        domain_name_servers = 192.168.0.1
DHCP4.OPTION[9]:                        expiry = 1568112998
DHCP4.OPTION[10]:                       host_name = dhcppc1
DHCP4.OPTION[11]:                       ip_address = 192.168.0.101
DHCP4.OPTION[12]:                       network_number = 192.168.0.0
DHCP4.OPTION[13]:                       next_server = 192.168.0.1
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       requested_domain_search = 1
DHCP4.OPTION[18]:                       requested_host_name = 1
DHCP4.OPTION[19]:                       requested_interface_mtu = 1
DHCP4.OPTION[20]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_root_path = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
DHCP4.OPTION[28]:                       requested_subnet_mask = 1
DHCP4.OPTION[29]:                       requested_time_offset = 1
DHCP4.OPTION[30]:                       requested_wpad = 1
DHCP4.OPTION[31]:                       routers = 192.168.0.1
DHCP4.OPTION[32]:                       server_name = TP-LINK
DHCP4.OPTION[33]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::4d53:26d3:1690:e423/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   150fdeb3-16dd-338a-bfa8-992a3756e9c4 | Wired connection 1

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

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

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0f0  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0f0  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/5.0.0-27-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode42.fw
firmware:       b43/ucode40.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode30_mimo.fw
firmware:       b43/ucode33_lcn40.fw
firmware:       b43/ucode29_mimo.fw
firmware:       b43/ucode26_mimo.fw
firmware:       b43/ucode25_mimo.fw
firmware:       b43/ucode25_lcn.fw
firmware:       b43/ucode24_lcn.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode16_lp.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6103E28C49B6C9B7208D51F
depends:        mac80211,ssb,bcma,cfg80211,cordic
retpoline:      Y
intree:         Y
name:           b43
vermagic:       5.0.0-27-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:12:1A:1E:
        64:1F:2A:03:9B:20:12:38:E0:CA:9F:8F:4A:6F:3F:6D:95:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:80:C0:69:65:68:46:5C:E9:61:50:37:
        69:5A:2F:C3:48:7F:2F:FA:D4:8E:A7:59:DC:DD:34:C5:0F:CD:1D:3A:
        DB:9D:FB:AC:5D:2C:DF:10:3C:1F:68:E7:F4:D3:CE:38:12:D9:E8:6F:
        E3:01:07:30:E3:50:58:2A:1C:38:BE:51:23:26:AF:D7:EA:2E:37:28:
        9E:B2:52:0C:A2:A8:EE:8A:DD:7A:10:0D:5E:2D:38:5B:C5:1F:9F:F1:
        FD:65:5C:AE:1A:11:09:64:96:05:2D:4D:8D:A6:24:AB:81:AB:73:B4:
        65:DF:02:34:5F:A2:EF:52:2F:40:CE:5B:61:7F:28:96:07:7A:0B:90:
        21:AF:55:FC:0F:CB:5C:25:B8:46:0D:11:DC:81:7F:FA:6B:99:50:B2:
        B0:5F:35:B5:48:BB:4D:F8:AC:39:AC:7F:DD:C3:28:B8:53:A7:51:F1:
        CF:E8:D0:0E:D3:09:96:FD:0F:A3:D6:71:44:6F:F8:9E:A8:1A:C0:F5:
        54:2A:86:3A:D5:53:E3:93:79:C9:5D:DF:4E:50:E2:C2:20:9B:82:27:
        C0:B9:31:09:07:61:7E:92:AE:0C:6D:D4:2F:B8:D0:1B:8F:41:68:E6:
        E4:9E:51:64:4D:36:55:A1:95:AC:26:C1:2E:A7:16:42:EC:82:24:7B:
        B7:C2:66:BE:0D:95:86:7E:EF:E4:6C:4D:ED:49:11:FC:96:B4:22:88:
        B1:AC:94:F1:99:59:92:BD:6D:00:2A:FA:45:74:68:07:E6:65:18:24:
        0B:5B:D4:25:E3:4C:CB:56:DB:BB:79:09:81:82:8E:49:D0:D6:44:B3:
        60:BE:9A:13:F2:14:25:56:02:5D:9D:5C:F5:FD:C9:34:13:DA:D4:65:
        B3:91:78:EF:CC:B4:AA:E8:10:9E:85:1D:29:F2:1E:74:D4:1E:E4:33:
        E2:E0:D2:93:92:EF:66:07:54:61:A4:12:39:39:D8:70:C0:36:87:1A:
        44:C1:79:34:7A:E4:5D:D3:99:59:8D:A5:3A:65:87:FF:C8:6C:00:BF:
        11:6C:70:75:50:D5:61:B3:CC:6C:60:DD:3E:6C:4A:D8:F3:B7:62:FC:
        E1:F0:58:D7:DD:26:B6:86:77:DD:72:55:F8:88:C9:28:68:81:56:E4:
        DE:27:77:30:E3:9A:A6:C5:2D:00:0E:D9:E3:CF:5A:16:63:43:97:5E:
        07:C6:EC:68:B3:87:F2:69:EA:B7:1E:17:F5:F3:6B:0E:52:05:85:9E:
        FB:72:E4:03:58:16:BF:3E:06:51:F7:AE:E7:5C:A8:3D:5C:05:2A:93:
        49:43:CC:FC:6D:30:4A:12:2B:F9:62:7C:7B:55:1A:B9:8F:A3:D8:4B:
        AA
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/5.0.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E72AE83255B6276A3F26D2D
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.0.0-27-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:12:1A:1E:
        64:1F:2A:03:9B:20:12:38:E0:CA:9F:8F:4A:6F:3F:6D:95:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:76:B4:C0:38:84:95:63:77:79:F7:4E:
        F5:9C:DE:89:A0:A5:6B:DD:55:E3:18:7A:D7:BE:DD:58:A3:82:B8:00:
        46:15:E9:E9:70:46:2C:B5:9F:3C:81:8F:D8:DD:0C:DB:56:28:AC:10:
        F6:17:23:50:0D:D0:C3:A6:70:04:C8:49:BC:DF:55:A6:2C:B9:EE:17:
        C3:63:1B:45:7E:D7:58:07:6A:BD:47:FE:29:EB:3B:12:48:D2:DD:24:
        73:5E:F1:60:09:01:D8:B5:4A:04:BA:8F:82:67:90:4D:E7:CB:34:11:
        3C:E2:F8:B2:FB:AE:08:A8:5C:08:3F:8B:38:D5:93:54:27:36:04:B6:
        4F:C8:DF:FF:33:56:99:05:54:3A:71:8A:76:C5:32:16:4C:E2:F1:88:
        41:62:9B:8E:E3:1E:88:9E:43:BC:03:B3:94:1E:3C:AA:8A:68:B1:42:
        C6:39:AF:40:C7:B9:53:AF:DB:87:82:58:F4:10:5A:E2:5A:45:43:FB:
        1B:72:FE:5D:12:0D:82:FC:41:E7:BE:6B:C0:65:8E:67:6F:35:E9:95:
        F6:20:E2:B9:B2:97:98:CC:1B:DD:A9:83:81:0C:5B:33:08:19:26:D9:
        CB:2E:F0:56:72:A6:FD:83:1E:4B:07:93:89:97:38:85:3B:89:FF:53:
        C3:BC:12:6E:7C:19:66:8C:CF:AB:F2:DB:C9:8B:1A:EC:A5:87:88:52:
        73:A1:5E:BB:40:57:61:56:90:F3:38:98:A2:07:4F:BE:4D:72:39:1F:
        DB:7F:27:08:DA:07:A0:19:3E:F0:10:D5:64:BB:82:45:7D:3C:EB:08:
        C6:F4:A0:66:41:A8:3D:D9:9B:FF:26:F9:9C:0A:12:DD:D8:7B:F5:3E:
        B6:0A:0D:DA:F9:37:34:95:68:92:6F:23:FE:C1:2C:11:8F:EA:4A:5C:
        37:24:65:0D:57:44:92:F8:A0:C2:2A:0E:CD:AE:A2:A0:91:20:21:B6:
        D7:8D:99:52:B0:B6:73:A3:71:21:A1:38:44:59:B9:45:2E:CA:7C:FB:
        53:9D:89:8B:BD:F8:AC:BD:8E:06:BB:B2:94:6B:7A:91:E2:2B:20:E9:
        89:44:D6:50:51:8A:A1:BB:76:88:1D:C2:3A:A4:01:09:0E:82:7D:B9:
        86:5E:37:89:3D:52:AE:E2:18:33:4D:87:8B:16:97:09:4F:A5:B7:BC:
        B4:91:6F:60:B2:69:4B:DA:02:4E:C3:7A:E9:D9:BA:E3:34:BF:73:2C:
        A1:0A:01:EE:5C:0E:C2:37:77:BB:F9:6E:41:3B:92:B0:D0:FF:D8:1E:
        FB:F5:F3:FF:BA:2E:ED:94:A4:A6:8B:77:A8:8C:5B:BF:54:5B:D0:0F:
        11
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.0.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8F0CAF5346FF71FCE9CB198
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-27-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:12:1A:1E:
        64:1F:2A:03:9B:20:12:38:E0:CA:9F:8F:4A:6F:3F:6D:95:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:15:61:11:D2:54:64:1E:67:7F:50:DA:
        FC:4C:75:70:50:E8:26:9B:D0:A9:DC:B6:03:93:52:88:42:F2:6A:16:
        50:85:45:E6:C1:AD:74:E7:3F:67:2B:C8:3D:07:8E:9C:87:7A:C3:1C:
        94:76:E7:5B:BD:17:A5:2B:59:15:DD:56:23:C5:F2:7E:9E:32:79:FD:
        6E:CE:15:BF:5E:0C:F5:D5:DD:0C:74:D1:0F:45:04:A7:EF:AE:0A:11:
        09:FD:6B:8C:84:75:D1:2A:40:5A:07:41:A3:A3:11:49:00:24:A7:E2:
        AC:5E:EE:E5:47:EE:B5:AC:DF:3A:96:03:74:EC:0C:0D:39:E2:96:4B:
        CE:84:1B:DC:C0:38:86:8A:92:1B:DE:59:49:AF:A6:B8:45:30:DF:13:
        EE:B3:E9:D6:CE:9D:03:A0:2D:2C:77:82:DA:FD:C4:45:AB:0E:8C:9C:
        0F:6A:77:3B:1A:86:4D:0E:AA:B8:87:37:57:3D:FD:FB:BA:00:24:76:
        5F:9A:21:E4:6D:93:67:13:53:CA:81:59:C7:0D:29:71:CB:DC:A9:8C:
        02:F7:7D:86:3D:1E:FC:F7:92:B5:45:2F:CF:C2:02:7B:F0:D9:84:6B:
        68:22:67:A9:3E:97:23:DB:F9:97:05:4B:CE:10:A6:B8:EE:C7:6A:EE:
        80:28:15:E8:68:EF:B6:D8:EE:13:5A:4E:42:85:56:5A:B1:90:98:22:
        9B:05:C8:DE:43:AF:85:B8:90:C5:7A:DE:AA:60:01:E8:82:0E:61:9F:
        26:D9:98:26:C2:A8:FA:B3:81:B4:88:EC:BF:65:8E:7D:10:D0:50:1F:
        6E:BC:25:A9:91:A4:B3:F7:B1:85:67:E6:E1:A7:D4:AF:E7:C3:23:33:
        E1:FE:19:03:B4:84:4B:91:9A:7F:C9:6A:63:33:94:BB:75:86:2C:66:
        AA:C8:4D:B6:80:E8:7C:8E:8E:1F:D0:5E:1F:A8:98:56:33:69:08:9F:
        9A:F7:56:53:16:3F:B1:90:C7:1F:76:04:B9:DD:A1:F4:8B:A1:64:31:
        AC:72:4D:EF:66:1B:C5:51:08:E8:0D:19:8A:C4:5E:59:4A:BB:1D:2E:
        E5:12:A8:7E:5B:BD:14:11:C4:06:93:3C:27:27:18:7E:7C:9E:66:DD:
        19:32:D9:92:D9:F7:FD:AC:77:D9:0C:E9:FA:5D:AE:24:D4:9E:C4:BB:
        88:EE:76:D7:71:86:83:7B:B2:D3:7A:31:B4:3A:E6:DD:DF:52:85:63:
        5F:F4:93:BB:5B:76:30:40:3F:33:E0:AA:3F:61:FD:62:7D:32:D9:77:
        73:AF:47:3D:95:9F:B8:4C:DF:AF:66:75:A2:C4:1E:B5:4B:24:FD:90:
        FC
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/5.0.0-27-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E7AF308F472629630CE272E
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       5.0.0-27-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:12:1A:1E:
        64:1F:2A:03:9B:20:12:38:E0:CA:9F:8F:4A:6F:3F:6D:95:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:4A:D2:BD:D9:39:B2:D4:75:CE:CE:C7:
        3F:DE:76:AF:33:B0:A8:D5:97:E3:15:83:E5:3C:1D:37:48:EA:E0:BD:
        E1:E1:51:8D:07:AF:91:6B:EC:9E:76:77:D3:6D:16:D4:A8:19:A6:02:
        D7:1B:C9:0F:CE:9B:1E:E6:91:51:58:5D:B2:0E:A8:59:4E:3E:30:CE:
        0C:6F:AA:1E:9C:2A:8C:A0:80:6D:22:86:E9:01:87:0E:00:A4:49:96:
        1F:40:F1:0B:B1:E0:94:92:C3:DE:B7:EE:A2:8F:E9:F2:5B:B5:97:43:
        59:BC:2C:0F:05:12:51:B1:35:F2:1E:78:E4:7D:86:A3:57:0C:E5:C8:
        8E:FB:1C:63:5E:44:6B:57:F4:87:30:B5:46:A9:94:61:CB:45:FA:C1:
        CF:AD:1A:29:FE:D0:DA:02:8F:E2:14:15:BD:E7:58:00:23:0A:67:9B:
        9A:CB:12:F8:AE:16:84:28:22:8C:4A:66:A6:53:F0:5A:24:56:DC:C6:
        D4:F0:16:14:65:5C:95:19:7F:7E:C0:E7:55:DA:9C:F9:03:4A:46:D4:
        11:C7:C6:19:B1:1F:29:5E:FC:5E:18:6A:60:CE:3B:5A:D2:E7:A7:AC:
        0D:CA:E4:2F:B9:BE:4A:BA:32:E7:93:AE:E2:2B:FF:EC:10:71:03:B4:
        32:AB:F7:BC:D5:A5:47:CB:1A:E8:FC:66:95:13:98:B1:FD:2B:FE:CF:
        E4:B6:8C:61:1E:DA:ED:57:4D:AE:AF:6C:0C:F6:55:32:CA:B8:92:DB:
        24:F1:19:12:53:54:32:30:2F:83:DC:13:48:B1:F6:84:C1:A9:10:08:
        D3:5A:B5:EF:15:EB:2A:C5:26:A1:37:F8:97:44:9C:34:43:54:62:95:
        B6:A7:F9:27:BD:F7:10:B2:81:0D:09:C7:AD:D5:37:74:62:97:23:99:
        88:EA:65:C7:44:16:56:DE:A4:24:09:26:DD:C7:02:0D:5F:2A:B3:29:
        D0:9B:2C:BD:CB:C1:4E:24:45:98:37:36:95:5C:D3:F1:3B:C4:64:3D:
        97:95:A4:0E:35:4E:1F:CF:73:64:1A:FB:CA:C2:CF:5B:89:A4:27:97:
        1E:54:13:9E:77:DB:C8:D9:F6:C4:F2:D3:6C:94:A8:BB:47:64:70:A4:
        A8:EC:5F:C7:35:5C:48:92:2D:33:89:EB:AC:26:47:60:8F:31:5E:A0:
        CE:95:9A:A0:C4:66:97:BA:E3:3B:1B:6C:C4:08:C1:B4:13:C9:83:7B:
        BA:1E:EE:C9:4A:23:18:69:43:AA:FC:2E:D2:A4:BF:B2:F7:90:21:55:
        DB:50:35:9F:18:C1:60:B1:81:FB:F7:40:7C:6C:F4:93:93:5C:43:E8:
        88

[bcma]
filename:       /lib/modules/5.0.0-27-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     A58277A768AAB23C742A248
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       5.0.0-27-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:12:1A:1E:
        64:1F:2A:03:9B:20:12:38:E0:CA:9F:8F:4A:6F:3F:6D:95:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:3C:24:C7:11:95:DD:1F:B1:71:51:0F:
        7F:E2:38:B8:A0:52:16:F9:9C:8B:0F:42:99:6B:EE:C1:11:46:6A:0C:
        4E:64:99:63:CD:F3:37:A3:F9:40:CD:FA:CA:EB:78:C5:19:87:B0:28:
        B5:F7:3D:D6:54:B2:DE:A6:2C:C4:8D:2E:10:1E:BF:65:FE:F7:E2:54:
        88:65:4B:35:ED:A9:41:36:EB:97:76:D0:A6:C2:FE:13:29:B1:37:AC:
        C4:FC:CE:BC:CF:AB:CB:10:E2:71:0A:05:7B:25:EB:C7:8F:81:F9:BD:
        DF:AB:43:49:D0:49:A6:B9:11:2A:67:39:E5:3F:03:04:22:E2:27:46:
        87:74:CD:FC:DA:75:8F:DA:AC:76:E7:6E:81:24:82:58:C1:31:2E:63:
        5E:AB:59:D6:F7:0D:EB:8D:BA:DD:F5:FA:20:FF:B3:0C:8D:6D:C0:D7:
        BE:91:55:8C:07:BE:70:38:BE:45:53:38:E6:4D:6C:DE:61:1C:41:73:
        E1:3C:A0:EF:20:9A:29:A4:BD:BE:89:F9:F1:72:E7:DD:FA:BF:4F:32:
        2B:89:DF:AF:AD:A2:69:53:47:AA:70:40:CF:9C:5D:8B:02:43:37:10:
        6A:CC:D4:05:C3:3A:39:CF:83:BD:78:BE:1D:97:0E:DD:D6:9D:D9:56:
        E7:21:CD:CE:51:8C:59:79:51:E2:31:89:4A:84:F2:56:5E:3A:CE:2A:
        E2:CC:A5:57:E5:33:26:63:04:51:7B:F9:17:E9:A4:C8:E0:90:39:E7:
        F5:11:C7:84:CA:B3:96:E2:55:7C:98:15:49:75:86:7D:40:CC:87:03:
        B5:FE:1F:46:39:CE:A6:13:8A:3B:05:E9:B2:19:A4:0F:CC:F8:88:5F:
        41:F1:ED:39:77:A1:40:2D:90:6C:ED:26:C8:B9:F9:CB:40:BE:0C:91:
        33:CA:89:53:E9:0C:CE:B1:BB:CD:0F:88:F3:22:6A:82:E8:E7:F0:BD:
        9A:AF:32:24:DF:18:C5:1E:05:A0:FD:11:E6:AA:30:51:9D:01:AB:57:
        47:09:59:64:8A:FD:9B:3B:A8:D8:5F:FF:C6:41:97:87:26:E6:1B:C0:
        2D:D2:9C:0E:2F:7F:F5:77:DC:DF:CE:D0:96:D9:D8:C4:FC:19:C3:0C:
        64:62:A5:54:38:A6:BE:1B:D6:4C:3A:B5:B1:E8:8F:2C:41:D4:A0:6B:
        06:A8:24:BC:03:5A:AB:DC:31:05:F1:89:47:E4:2D:FB:56:7E:56:9C:
        AF:8F:F2:42:30:25:82:32:18:F8:26:C7:A0:D0:91:ED:C9:9A:25:9F:
        0F:93:AE:90:C2:74:6B:01:A5:C0:05:0D:BA:23:D0:3C:D1:5E:53:FB:
        40

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 2243.611909] tg3 0000:02:00.0 enp2s0f0: Link is up at 1000 Mbps, full duplex
[ 2243.611941] tg3 0000:02:00.0 enp2s0f0: Flow control is on for TX and on for RX
[ 2243.611946] tg3 0000:02:00.0 enp2s0f0: EEE is enabled
[ 2243.611983] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0f0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2019-09-07
Moved to Apple Hardware

---

### Post by chili555 on 2019-09-07
Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

