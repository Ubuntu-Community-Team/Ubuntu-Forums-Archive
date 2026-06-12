---
title: "Ubuntu 19.04, MacBook Air 6,2 No Wifi"
date: 2019-04-28
forum: Apple Hardware Users
---

### Post by hffmnn on 2019-04-28
Hi everyone,

I just installed Ubuntu 19.04 on a MBA 6,2 following this tutorial: [https://help.ubuntu.com/community/MacBookAir6-2/Saucy](https://help.ubuntu.com/community/MacBookAir6-2/Saucy)

Problem is, that WiFi seems not to work.

Software & Updates App -> Additional Drivers says, that is is using the Broadcom 802.11 Linux STA wireless driver source from ... and Settings app says, that No Wi-Fi Adapter was found.

I searched this forum and found this [thread]("https://ubuntuforums.org/showthread.php?t=2231441") with a linked script to make this problem a little easier to debug. Here is the output from my machine.

```


########## wireless info START ##########

Report from: 28 Apr 2019 13:22 CEST +0200

Booted last: 28 Apr 2019 00:00 CEST +0200

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco

##### kernel ############################

Linux 5.0.0-13-generic #14-Ubuntu SMP Mon Apr 15 14:59:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b:0117]
    Kernel modules: bcma, wl

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:0291 Apple, Inc. 
Bus 001 Device 006: ID 05ac:828f Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

This system doesn't support Secure Boot

##### lsmod #############################

wl                   6451200  0
mac80211              806912  0
cfg80211              671744  2 wl,mac80211

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
2: enx<IF from MAC [IF1]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enx<IF from MAC [IF1]>' [IF1]> brd <MAC address>
    inet 192.168.11.15/24 brd 192.168.11.255 scope global dynamic noprefixroute enx<IF from MAC [IF1]>
       valid_lft 604442sec preferred_lft 604442sec
    inet6 fe80::7015:7b36:3d37:1806/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enx<IF from MAC [IF1]>  no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.11.1 dev enx<IF from MAC [IF1]> proto dhcp metric 100 
169.254.0.0/16 dev enx<IF from MAC [IF1]> scope link metric 1000 
192.168.11.0/24 dev enx<IF from MAC [IF1]> proto kernel scope link src 192.168.11.15 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search localdomain

##### network managers ##################

Installed:

    NetworkManager

Running:

root       751     1  0 13:13 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8153 Gigabit Ethernet Adapter
GENERAL.DRIVER:                         r8152
GENERAL.DRIVER-VERSION:                 v1.09.9
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       efe2e701-88b7-3399-8983-32af630aa99c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.11.15/24
IP4.GATEWAY:                            192.168.11.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.11.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.11.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.11.1
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        broadcast_address = 192.168.11.255
DHCP4.OPTION[2]:                        dad_wait_time = 0
DHCP4.OPTION[3]:                        dhcp_lease_time = 604800
DHCP4.OPTION[4]:                        dhcp_message_type = 5
DHCP4.OPTION[5]:                        dhcp_rebinding_time = 529200
DHCP4.OPTION[6]:                        dhcp_renewal_time = 302400
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.11.1
DHCP4.OPTION[8]:                        domain_name = localdomain
DHCP4.OPTION[9]:                        domain_name_servers = 192.168.11.1
DHCP4.OPTION[10]:                       expiry = 1557054999
DHCP4.OPTION[11]:                       ip_address = 192.168.11.15
DHCP4.OPTION[12]:                       network_number = 192.168.11.0
DHCP4.OPTION[13]:                       next_server = 0.0.0.0
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
DHCP4.OPTION[31]:                       routers = 192.168.11.1
DHCP4.OPTION[32]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::7015:7b36:3d37:1806/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fe80::1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   efe2e701-88b7-3399-8983-32af630aa99c | Wired connection 1

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

Region: Europe/Berlin (based on set time zone)

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

enx<IF from MAC [IF1]>  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enx<IF from MAC [IF1]>  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/5.0.0-13-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       5.0.0-13-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:01:A9:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:01:9A:30:
        82:01:96:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:01:73:30:82:
        01:6F:02:01:01:30:4A:30:32:31:30:30:2E:06:03:55:04:03:0C:27:
        75:62:75:6E:74:75:20:53:65:63:75:72:65:20:42:6F:6F:74:20:4D:
        6F:64:75:6C:65:20:53:69:67:6E:61:74:75:72:65:20:6B:65:79:02:
        14:33:D9:76:27:F5:4F:C7:4C:E2:36:62:F3:70:4F:5A:E4:EF:36:C9:
        90:30:0B:06:09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:
        48:86:F7:0D:01:01:01:05:00:04:82:01:00:45:F1:1F:A8:6F:99:AD:
        A8:A9:B5:AF:27:65:7F:F2:3F:DB:36:33:70:EB:65:BB:84:20:94:C9:
        AD:A3:77:9A:A2:91:24:B7:FB:6B:6D:47:60:D3:86:64:1E:5A:EB:10:
        A2:D3:C2:BF:0C:E5:7F:7F:DC:37:1A:60:36:05:DB:BD:05:08:8E:46:
        5A:2C:FA:6F:6B:48:09:4B:19:B6:72:17:60:6A:7B:C3:92:7F:28:67:
        41:42:AA:82:5E:8B:3A:27:FF:E6:E7:8B:9C:CF:B1:B0:1F:79:35:68:
        B8:E3:F3:68:2A:A1:9E:B5:F3:64:E2:4E:84:9E:41:F2:3B:5F:FA:A0:
        5E:12:81:2D:A8:AC:4F:2F:D9:E2:BD:B4:30:D1:5D:0D:26:8B:9F:46:
        F8:11:76:E8:23:61:4B:87:FA:11:3A:4B:F7:9B:6E:37:27:16:2F:8C:
        2C:2D:94:15:D3:C4:98:C3:D7:DE:4F:22:CB:1E:A4:FD:FD:1E:44:CA:
        05:F3:CB:39:26:0D:27:EE:AB:C8:D1:08:BC:9B:62:05:66:4E:8C:B2:
        C0:1C:93:DA:EE:9B:25:87:21:71:5B:DE:CE:E5:0B:F2:8C:5A:88:11:
        4E:E5:16:74:73:90:8F:44:0F:6D:09:03:DD:15:22:B5:2A:CC:E1:AD:
        1D:E2:7F:EE:02:25:E3:1D:83
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[mac80211]
filename:       /lib/modules/5.0.0-13-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B7EC14466A8D58C5480E512
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.0.0-13-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:31:2B:78:
        92:2C:C0:87:DF:0A:5A:AF:C6:A9:A5:5F:50:00:31:4E:F2:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:4F:83:E2:B4:40:0C:70:8E:E1:0F:2B:
        95:76:20:C2:5E:6D:A0:68:AC:CB:D9:99:C5:8E:5A:FD:4E:31:4C:A8:
        BC:8F:83:5F:8B:21:6E:57:3F:D6:F8:75:A1:A3:C2:45:71:E9:D7:FC:
        66:66:DC:31:58:03:8A:C4:78:75:45:FF:B0:77:4D:14:FD:71:2D:DA:
        4B:54:DF:5D:BB:DB:E5:E6:B1:26:14:C3:A3:33:45:96:05:EC:7A:09:
        43:3F:3A:11:D0:1B:10:23:8C:8A:52:02:19:CB:57:AC:4E:79:B2:BC:
        6C:CD:6A:BD:DB:7D:BA:47:33:9E:13:94:06:F4:60:FE:43:B8:89:4F:
        16:00:77:1B:2E:04:61:E2:E0:0E:72:EC:90:87:8C:29:A0:6E:AC:A8:
        33:D8:87:E2:C8:36:36:0F:14:F6:A1:09:D8:49:B4:79:78:FE:55:09:
        3E:36:58:3C:51:FC:55:87:5F:FD:2B:DB:09:9F:49:13:FE:9D:0C:08:
        D8:40:3B:FA:51:44:C7:13:EA:76:FF:3C:A9:C8:3F:31:2E:B6:4C:61:
        40:38:30:A5:D8:64:FC:22:E2:C9:04:6F:7F:D5:B6:97:56:9D:27:1B:
        80:D0:28:E5:BF:75:EE:3E:DE:BA:E5:1D:48:36:BE:A9:08:A2:35:34:
        77:59:44:52:34:F7:0A:8A:39:74:73:3A:3C:CF:24:0D:46:08:4D:96:
        1E:A7:48:31:78:02:B8:8F:64:AF:1F:3A:24:8C:F7:5A:A6:FA:0E:C7:
        CA:56:21:5D:C9:8E:75:75:26:BA:E1:2D:C2:6A:8F:29:BA:66:BE:C8:
        74:FF:5C:16:01:23:E2:7F:F5:C6:98:E0:E3:18:D5:57:B0:D2:F5:D7:
        F9:2D:24:2C:9B:A2:3D:E4:A2:BD:44:D7:96:0E:2F:63:3E:B4:33:A7:
        4F:25:CA:24:E2:51:57:60:AB:E7:68:A7:C2:13:68:66:C8:14:58:97:
        A0:13:33:17:6A:7A:18:97:BC:2F:10:71:4A:A6:04:DE:2D:54:21:F8:
        06:ED:5D:37:5E:55:70:AA:2C:DC:BD:2B:F0:D6:D7:93:48:DC:30:5A:
        E1:54:F3:A7:BF:23:DB:43:98:15:2E:E1:63:39:E9:65:40:FA:AD:ED:
        BF:04:5C:48:2A:25:BF:04:35:09:D3:78:F1:F4:C3:43:6F:9E:2B:71:
        C8:44:AF:8E:BD:69:12:42:CC:25:94:A2:3D:6E:F0:85:EE:FE:68:42:
        98:D3:BB:F2:75:C6:3B:81:B0:C0:F2:72:F8:7B:20:25:59:1C:59:84:
        F4:CC:57:2C:1D:B5:44:0F:DA:A6:02:18:29:A7:22:51:72:CE:CC:F6:
        A6
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.0.0-13-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2BD3ED72B421276E6C2918E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-13-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:31:2B:78:
        92:2C:C0:87:DF:0A:5A:AF:C6:A9:A5:5F:50:00:31:4E:F2:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:40:17:56:1C:64:E1:0D:28:ED:51:46:
        9E:0E:CF:D6:DB:31:52:B8:53:96:A9:2B:85:DB:E1:0F:34:9E:7A:3E:
        BB:31:FA:1F:6E:C6:94:0A:A7:97:67:DA:48:49:AB:9D:9C:70:27:9B:
        87:4A:CA:80:AC:53:40:30:EF:D3:7D:07:19:01:88:B1:A3:BB:12:55:
        6B:06:B6:66:EB:7B:B6:02:4B:FD:D5:4D:80:4E:A8:DA:38:B4:B2:C3:
        37:3A:03:85:7E:5C:67:CB:5B:1C:EB:23:C7:6C:C5:14:19:9B:FB:BF:
        18:EE:4B:D6:DB:8F:3A:71:1E:9E:91:64:6D:7E:74:9B:68:B5:4F:0F:
        D1:A2:EB:D3:C9:11:8C:2C:F9:6B:BB:3A:4A:AB:D8:94:01:34:6C:97:
        9E:95:D1:DE:70:F4:80:36:F0:74:62:87:57:27:87:2E:37:4C:D9:55:
        3B:CF:CD:0B:B3:16:95:73:B4:2E:EC:BA:8A:22:3E:9A:9E:C1:6E:58:
        2F:C3:C0:1D:CD:8A:6C:8A:C2:18:CE:DF:EB:57:B4:CC:A9:7A:60:BF:
        85:D9:8D:83:48:91:78:2C:AF:A5:D6:F1:5F:22:27:53:54:EF:9A:45:
        8B:89:6B:02:8D:9C:69:8A:F7:0B:93:AA:D5:3E:F2:17:76:C4:EC:88:
        88:03:46:4F:4C:7D:26:A5:6E:04:39:77:FE:80:F7:74:31:38:3D:29:
        85:4B:8C:1E:7D:3C:1F:AE:67:20:C6:FC:84:48:C8:FD:47:25:76:1E:
        0E:84:23:5E:42:C6:63:FF:35:3F:20:8D:7F:14:91:D0:15:A8:C7:EE:
        DE:08:05:D3:CC:72:5D:25:D2:15:9A:01:4C:E6:54:E3:9E:B2:63:DF:
        DE:5C:71:15:C0:20:5D:B5:B7:57:11:2F:B8:B3:EE:82:C7:5B:F0:F1:
        AD:39:26:1B:B6:D0:13:8D:27:AE:AF:57:9C:5E:59:95:DF:9E:B8:42:
        D2:29:8C:4C:5B:FA:F4:28:D7:73:05:46:C4:80:59:C0:38:47:D3:91:
        B9:D7:8E:A9:D2:5E:5A:D8:8C:F9:4B:33:8E:70:A1:F4:D2:F4:41:08:
        E7:5B:39:3D:74:E5:B5:D9:46:78:81:26:DD:CB:E9:FE:8B:FE:5A:D7:
        5F:A7:C1:11:50:E4:FC:3B:EC:7B:21:19:23:60:F4:84:81:78:DA:AE:
        0C:FF:E5:DB:7C:CE:01:9D:6D:71:46:0B:6A:8B:48:C3:82:DB:FC:95:
        12:78:A5:A1:A9:38:FE:39:C3:0C:97:81:0D:F4:8F:7A:27:DB:30:E2:
        1E:AB:96:E7:80:E3:7C:CB:F0:34:09:41:87:22:D1:0D:55:21:30:39:
        D1
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[    4.445801] b43-phy0: Broadcom 4360 WLAN found (core revision 42)
[    4.450679] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 12, Type 11 (AC), Revision 1)
[    4.450722] b43: probe of bcma0:1 failed with error -95
[  177.483589] r8152 2-1:1.0 eth0: v1.09.9
[  177.516410] r8152 2-1:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[  180.432688] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF1]>: link becomes ready
[  180.436264] r8152 2-1:1.0 enx<IF from MAC [IF1]>: carrier on
[  236.503390] wl: loading out-of-tree module taints kernel.
[  236.503394] wl: module license 'MIXED/Proprietary' taints kernel.
[  236.505035] wl: module verification failed: signature and/or required key missing - tainting kernel

########## wireless info END ############


```

The working ethernet connection is because of a running USB-Gigabit Adapter, which works without any problems.

Would be great if someone could support me with this.

Regards,
Christian

---

### Post by luusac on 2019-05-04
We have the same WiFi & error.  I found a solution that works for me, posted [here]("https://ubuntuforums.org/showthread.php?t=2418084").  Hope this helps.

---

### Post by aabulli on 2019-05-04
I have the same wireless adapter in my Macbook Air. I was able to get it working using the broadcom-sta-dkms package. I got it from here (but I had to use a Windows machine): [https://packages.debian.org/stretch/broadcom-sta-dkms](https://packages.debian.org/stretch/broadcom-sta-dkms). In my case I used a flash drive to copy it over to my Mac and install it from my home folder. You may be able to just sudo apt install it, although it may require adding another repository (I'm not that Ubuntu saavy, so I may be way off).

So far so good. It is slow to reconnect after waking up from sleep though. Hope that helps!
Andrew B.

---

### Post by luusac on 2019-05-05
That package is in the Ubuntu repository [multiverse] [here]("https://packages.ubuntu.com/search?suite=disco&section=all&arch=any&keywords=Broadcom-sta&searchon=names").

---

### Post by airplaneit on 2019-05-06
I had this issue just minutes ago. I have a 2009 Macbook Pro. What worked for me was to go to Software and Updates, Additional Drivers tab, and under the WiFi driver, select (do not use this device). I then let the device work through the uninstall in the background. I rebooted, re-selected the driver, allowed the re-install to happen, then rebooted. The WiFi worked after that final reboot.

[ATTACH=CONFIG]283203[/ATTACH]

---

