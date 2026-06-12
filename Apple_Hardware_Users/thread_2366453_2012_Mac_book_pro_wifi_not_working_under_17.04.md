---
title: "2012 Mac book pro wifi not working under 17.04"
date: 2017-07-18
forum: Apple Hardware Users
---

### Post by sterator on 2017-07-18
Do I need to download something or execute a terminal command to fix this? I see nothing in settings dealing with this issue.

thank you!

---

### Post by &amp;KyT$0P# on 2017-07-18
In what ways does it not work?

---

### Post by BenginM on 2017-07-18
Salutations!


for someone to be able to assist you and troubleshoot the issue , you'll need to show us some logs , run [the wierless info script in here]("https://ubuntuforums.org/showthread.php?t=370108") , and paste/post the output here in a ```
 tag , like so :


[noparse][CODE][/noparse]

output here ...

[noparse]
```[/noparse]

---

### Post by sterator on 2017-07-18
In the way that there isn't a thing I can click to turn on wifi, nor do I see a place where I can enter my router settings.
In my reading, I see that one must tell Ubuntu which wifi card is installed, and that there are scripts/commands to make them play together.

Thank you!

---

### Post by sterator on 2017-07-18
Thank you....I'll forward this to my gmail and get that code..paste it here soon.

---

### Post by &amp;KyT$0P# on 2017-07-18
Under Settings > Additional Drivers, what (if anything) does it say about your Wi-Fi card?

* You may need to run [FONT=Courier New]sudo apt-get update[/FONT] in Terminal (requires Internet connection) before opening Additional Drivers.

---

### Post by sterator on 2017-07-19
This was a fail. Terminal asks for sudo password. I am the only sudo this computer knows, only 1 password. Do I need to somehow convince the machine that I really am sudo?  How's this done, please?

Wait..might have succeeded here...

```


########## wireless info START ##########

Report from: 19 Jul 2017 19:36 PDT -0700

Booted last: 19 Jul 2017 00:00 PDT -0700

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-28-generic #32-Ubuntu SMP Fri Jun 30 05:32:18 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Limited NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Broadcom Limited BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Broadcom Limited BCM4331 802.11a/b/g/n [14e4:4331]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 006: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   413696  0
mac80211              782336  1 b43
cfg80211              602112  2 b43,mac80211
ssb                    57344  1 b43
bcma                   57344  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0f0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.18  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::17fe:d65c:c80e:f143  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 5558  bytes 5215286 (5.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3792  bytes 528728 (528.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 338  bytes 24784 (24.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 338  bytes 24784 (24.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp1s0f0  no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0f0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0f0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0f0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       804     1  0 19:27 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        NetXtreme BCM57765 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               57765-v1.37
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0f0
GENERAL.IP-IFACE:                       enp1s0f0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       05c8cb57-b528-3eb5-a28a-71e008485ba1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   05c8cb57-b528-3eb5-a28a-71e008485ba1 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.18/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1500604060
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.18
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::17fe:d65c:c80e:f143/64
IP6.GATEWAY:                            

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp1s0f0  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp1s0f0  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
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
srcversion:     5F955FFEA61C80144A2B433
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 
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
filename:       /lib/modules/4.10.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     38B7A1BE5CF467C3CF164D5
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 

[bcma]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C645ADA4C8790A787B7C8E9
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    2.647772] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[    2.648233] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[    2.648243] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2059, Revision 0, Version 1
[    2.648244] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[    2.649349] b43 bcma0:1: Direct firmware load for b43/ucode29_mimo.fw failed with error -2 (repeated 2 times)
[    2.649380] b43 bcma0:1: Direct firmware load for b43-open/ucode29_mimo.fw failed with error -2 (repeated 2 times)
[    2.649391] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[    2.649394] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[    2.649396] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

########## wireless info END ############





```

---

### Post by &amp;KyT$0P# on 2017-07-20
sterator, did you see my last post?  Or are you unable to connect to the Internet by other, non Wi-Fi, means?

You currently have [FONT=Courier New]bcma-pci-bridge[/FONT] driver where my MacBook Pro uses [FONT=Courier New]wl[/FONT] driver.

---

### Post by BenginM on 2017-07-20
you have two options to use the correct kernel driver for the NIC , first check the additional drivers and install a driver automatically ...

 or do it manually ..


 then you have to chose either to load and use the Proprietary Broadcom STA Wireless kernel driver: wl , for that you need to install the package [bcmwl-kernel-source ]("https://launchpad.net/ubuntu/+source/bcmwl")or the free  kernel driver b43 , for that install [URL="https://launchpad.net/ubuntu/+source/b43-fwcutter"]firmware-b43-installer
[/URL]
that is described here:

 [URL="https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29"]https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=BroadcomSTA%28Wireless%29)
[/URL]



## it's simple as .. connect to wired Ethernet:

sudo apt update

sudo apt upgrade

sudo apt dist-upgrade

sudo apt install[ bcmwl-kernel-source]("https://launchpad.net/ubuntu/+source/bcmwl") 

Then reboot and retest wireless

---

### Post by sterator on 2017-07-20
halogen2

I just saw your post. I can get online via wire (ethernet). I did run the update command prior to running the script which produced the code showing which wifi driver I have.

Should that update have updated/corrected my wifi driver situation? Or is there another step I can take?
Can I [COLOR=#000000][FONT=Courier New]sudo apt-get istall(correct wifi driver)   ?
[/FONT][/COLOR]
Thank you!

---

### Post by miqrojamie on 2017-07-21
If you don't have an Internet connection such as an Ethernet port you can get the drivers from here on the Ubuntu DVD/USB:

pool/main/d/dkms_****.deb
pool/restricted/b/bcmwl/bcmwl-kernel-source_*****.deb

Copy them to your home folder and then run 'sudo dpkg -i *.deb'

Just thought I'd share this as this worked for me and is very convenient, although I know the OP has the ethernet connection.

---

### Post by &amp;KyT$0P# on 2017-07-21
> **sterator said:**
> Should that update have updated/corrected my wifi driver situation? Or is there another step I can take?
You've done step 1 of 2.  Step 2 is to go to Settings > Additional Drivers, select the proper driver for your Wi-Fi card, and apply the change.

---

### Post by kevin160 on 2017-07-22
It's complicated, because there are 2 drivers that work for the 4331 chip.  The bcml-kernel-source (aka STA) driver supports both the 2.4 and 5 GHz frequencies but is missing a lot of features like being able to set up a WPA access point.  The b43 driver (firmware-b43-installer and b43-fwcutter) only supports 2.4 GHz frequencies on the 4331, but has more features like AP (and I think mesh and monitor mode, etc).   You can switch back and forth, but make sure you don't have both firmware-b43-installer and bcml-kernel-source installed at the same time.  

The menus you click through in the various Ubuntu desktop flavors to get to the Additional Drivers screen seem to differ.  I've moved to the Gnome desktop, and now basically have to hit the command key and type "drivers" to get there.  I also have to type nm-connection-editor to be able to change wireless settings.  I hope Canonical fixes that stuff up before their first Gnome desktop release.  It's more minimalistic than macOS!  ;-)

---

