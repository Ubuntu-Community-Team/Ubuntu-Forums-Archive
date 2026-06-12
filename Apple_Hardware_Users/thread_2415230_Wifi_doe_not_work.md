---
title: "Wifi doe not work"
date: 2019-03-22
forum: Apple Hardware Users
---

### Post by daymoon on 2019-03-22
This is my first post since 2013... I just installed Bionic Beaver onto a iMac9,1. Could you direct me to the tread for wifi not working possible missing driver. Thanks...

---

### Post by wildmanne39 on 2019-03-22
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone should be able to help.

---

### Post by daymoon on 2019-03-22
```
########## wireless info START ##########

Report from: 22 Mar 2019 14:24 MDT -0600

Booted last: 22 Mar 2019 00:00 MDT -0600

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.18.0-16-generic #17~18.04.1-Ubuntu SMP Tue Feb 12 13:35:51 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: forcedeth

04:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008e]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 002 Device 005: ID 05ac:024f Apple, Inc. 
Bus 002 Device 004: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 008: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 003: ID 05ac:8215 Apple, Inc. Built-in Bluetooth 2.0+EDR HCI
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

This system doesn't support Secure Boot

##### lsmod #############################

b43                   413696  0
bcma                   57344  1 b43
mac80211              802816  1 b43
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau
cfg80211              667648  2 b43,mac80211
ssb                    57344  1 b43

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
2: enp0s10: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s10' [IF1]> brd <MAC address>
    inet 10.0.0.215/24 brd 10.0.0.255 scope global dynamic noprefixroute enp0s10
       valid_lft 601631sec preferred_lft 601631sec
    inet6 2601:8c0:80:8f0::ed46/128 scope global dynamic noprefixroute 
       valid_lft 601633sec preferred_lft 601633sec
    inet6 2601:8c0:80:8f0:3486:36cf:6804:b9e6/64 scope global temporary dynamic 
       valid_lft 325278sec preferred_lft 82966sec
    inet6 2601:8c0:80:8f0:31b4:4b0e:f924:eaf6/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 325278sec preferred_lft 325278sec
    inet6 fe80::17ec:599b:8ef4:5d99/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp0s10   no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 10.0.0.1 dev enp0s10 proto dhcp metric 100 
10.0.0.0/24 dev enp0s10 proto kernel scope link src 10.0.0.215 metric 100 
169.254.0.0/16 dev enp0s10 scope link metric 1000 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search hsd1.nm.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       608     1  0 13:31 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s10
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP79 Ethernet (Apple iMac 9,1)
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp0s10' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0a.0/net/enp0s10
GENERAL.IP-IFACE:                       enp0s10
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       07fe4b23-e78b-39cc-b7b6-fd18e992b86e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         10.0.0.215/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 10.0.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 10.0.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.nm.comcast.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 10.0.0.215
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 10.0.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 10.0.0.255
DHCP4.OPTION[10]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[16]:                       routers = 10.0.0.1
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.nm.comcast.net
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1553887887
DHCP4.OPTION[21]:                       host_name = jesse-iMac
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 10.0.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 604800
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2601:8c0:80:8f0::ed46/128
IP6.ADDRESS[2]:                         2601:8c0:80:8f0:3486:36cf:6804:b9e6/64
IP6.ADDRESS[3]:                         2601:8c0:80:8f0:31b4:4b0e:f924:eaf6/64
IP6.ADDRESS[4]:                         fe80::17ec:599b:8ef4:5d99/64
IP6.GATEWAY:                            fe80::be64:4bff:fe0e:d97e
IP6.ROUTE[1]:                           dst = 2601:8c0:80:8f0::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::be64:4bff:fe0e:d97e, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[6]:                           dst = 2601:8c0:80:8f0::ed46/128, nh = ::, mt = 100
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:f4:46:52:17:63:6:d:49:c:ee:b1:18:bc:d5:ec:29
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[4]:                        rebind = 483840
DHCP6.OPTION[5]:                        max_life = 604800
DHCP6.OPTION[6]:                        preferred_life = 604800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1553281667
DHCP6.OPTION[10]:                       dhcp6_status_code = success Assigned an address.
DHCP6.OPTION[11]:                       ip6_address = 2601:8c0:80:8f0::ed46
DHCP6.OPTION[12]:                       ip6_prefixlen = 64
DHCP6.OPTION[13]:                       renew = 302400
DHCP6.OPTION[14]:                       starts = 1553281667
DHCP6.OPTION[15]:                       iaid = 4b:ac:d9:7c
DHCP6.OPTION[16]:                       dhcp6_server_id = 0:1:0:1:24:20:54:4e:bc:64:4b:e:d9:7e
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   07fe4b23-e78b-39cc-b7b6-fd18e992b86e | Wired connection 1

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

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Denver (based on set time zone)

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

enp0s10   no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp0s10   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
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
srcversion:     F4C4F20E18BD2B0E5D000E6
depends:        mac80211,ssb,bcma,cfg80211
retpoline:      Y
intree:         Y
name:           b43
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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

[bcma]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     A58277A768AAB23C742A248
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.18.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.0-16-generic SMP mod_unload 
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
filename:       /lib/modules/4.18.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     F3EAB59AC9D667714E87F1B
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############
```

---

### Post by wildmanne39 on 2019-03-22
Please do:
```
sudo apt install bcmwl-kernel-source
```
Reboot and your wifi should be working.

---

### Post by daymoon on 2019-03-22
Thanks Wild Man - You're the best shooter in this old west.

---

### Post by wildmanne39 on 2019-03-22
Great, I guess it worked, please use thread tools at the top of the page to mark the thread solved.

Thanks!

---

