---
title: "unable to get BCM4360 [14e4:43a0] (rev 03) Broadcom wifi working (guide followed)"
date: 2019-05-01
forum: Apple Hardware Users
---

### Post by luusac on 2019-05-01
I have been trying to get wifi working on a mac booting from Disco or Bionic livecds (from a multi boot usb stick) without success.  There already seems to be a [restricted] driver listed in additional drivers which I have tried and failed to get to work, so have been trying via terminal, also without success.  This is a tri-boot macbook, and before I broke my Ubuntu installation I had Wily installed (not live cd) running quite happily with wifi.
So, here is what I have tried via terminal:

```
it@it:~$ sudo apt-get purge bcmwl-kernel-source
…
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
it@it:~$ sudo apt-get install /media/it/SharedDrive/dkms_2.6.1-4ubuntu1_all.deb 
…
Note, selecting 'dkms' instead of '/media/it/SharedDrive/dkms_2.6.1-4ubuntu1_all.deb'
Suggested packages:
  menu
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
…
Get:1 cdrom://It/multiboot/ubuntu-19.04-desktop-amd64 disco/main amd64 dkms all 2.6.1-4ubuntu1 [67.0 kB]
Selecting previously unselected package dkms.
…
it@it:~$ sudo apt-get install /media/it/SharedDrive/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb 
…
Note, selecting 'bcmwl-kernel-source' instead of '/media/it/SharedDrive/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb'
The following NEW packages will be installed:
  bcmwl-kernel-source
Get:1 cdrom://It/multiboot/ubuntu-18.04.1-desktop-amd64 bionic/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu4 [1550 kB]
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
…
Building initial module for 5.0.0-13-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-13-generic/updates/dkms/

depmod...

DKMS: install completed.
update-initramfs is disabled since running on read-only media
it@it:~$ sudo modprobe wl
```

It all seems to go ok, but no wifi adapter listed in the gui.

Output of wireless-info.sh

```

########## wireless info START ##########
Report from: 01 May 2019 10:15 UTC +0000
Booted last: 01 May 2019 00:00 UTC +0000
Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################
Distributor ID:	Ubuntu
Description:	Ubuntu 19.04
Release:	19.04
Codename:	disco

##### kernel ############################

Linux 5.0.0-13-generic #14-Ubuntu SMP Mon Apr 15 14:59:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: file=/cdrom/multiboot/ubuntu-19.04-desktop-amd64/preseed/ubuntu.seed, boot=casper, cdrom-detect/try-usb=true, noprompt, floppy.allowed_drive_mask=0, ignore_uuid, live-media-path=/multiboot/ubuntu-19.04-desktop-amd64/casper/, initrd=/multiboot/ubuntu-19.04-desktop-amd64/casper/initrd, quiet, splash, ---

##### desktop ###########################
Ubuntu
##### lspci #############################
03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
	Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b:0134]
	Kernel modules: bcma, wl
##### lsusb #############################

Bus 002 Device 003: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 002: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05ac:8289 Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 05ac:0263 Apple, Inc. Apple Internal Keyboard / Trackpad (MacBook Retina)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################
##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################
EFI variables are not supported on this system
##### lsmod #############################

wl                   6451200  0
mac80211              806912  0
cfg80211              671744  2 wl,mac80211
mxm_wmi                16384  1 nouveau
wmi                    28672  2 mxm_wmi,nouveau

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

##### iwconfig ##########################
lo        no wireless extensions.
##### route #############################
##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################
Installed:
	NetworkManager
Running:

root      2249     1  0 10:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############
##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

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

Region: Etc/UTC (based on set time zone)

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
lo        no frequency information.
##### iwlist scan #######################
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
signature:     <snip>
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
signature:     <snip>
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

[   21.179974] b43-phy0: Broadcom 4360 WLAN found (core revision 42)
[   21.180495] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 12, Type 11 (AC), Revision 1)
[   21.180503] b43: probe of bcma0:1 failed with error -95
[  184.214768] wl: loading out-of-tree module taints kernel.
[  184.214771] wl: module license 'MIXED/Proprietary' taints kernel.
[  184.215927] wl: module verification failed: signature and/or required key missing - tainting kernel

########## wireless info END ############

```

One thing that I did notice was that b43 and bcm43xx seem to be blacklisted as shown in wireless-info.txt

I can't find my thunderbolt ethernet connector, so I really want to get wifi running on the live cd before proceeding further.  I have added the full wireless-info.txt and terminal outputs as attachments, but have truncated them slightly above.
thank you.

---

### Post by howefield on 2019-05-01
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by luusac on 2019-05-04
This is what resolved the issue for me (on a livecd boot of disco):

first:

```
dmesg |grep wlan
```

gives no output.  But

```
sudo apt-get install dkms bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe -vv wl

```

gives:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  menu
The following NEW packages will be installed:
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1617 kB of archives.
After this operation, 8354 kB of additional disk space will be used.
Get:1 cdrom://It/multiboot/ubuntu-19.04-desktop-amd64 disco/main amd64 dkms all 2.6.1-4ubuntu1 [67.0 kB]
Get:2 cdrom://It/multiboot/ubuntu-18.04.1-desktop-amd64 bionic/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu4 [1550 kB]
Selecting previously unselected package dkms.
(Reading database ... 155920 files and directories currently installed.)
Preparing to unpack .../dkms_2.6.1-4ubuntu1_all.deb ...
Unpacking dkms (2.6.1-4ubuntu1) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Setting up dkms (2.6.1-4ubuntu1) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.0.0-13-generic
Building for architecture x86_64
Building initial module for 5.0.0-13-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-13-generic/updates/dkms/

depmod...

DKMS: install completed.
update-initramfs is disabled since running on read-only media
Processing triggers for man-db (2.8.5-2) ...
modprobe: INFO: ../libkmod/libkmod.c:364 kmod_set_log_fn() custom logging function 0x557f79f48ed0 registered
insmod /lib/modules/5.0.0-13-generic/updates/dkms/wl.ko 
modprobe: INFO: ../libkmod/libkmod.c:331 kmod_unref() context 0x557f7abe4410 released

```

Now:

```
dmesg |grep wlan
```

gives:

```
[   74.417108] wlan0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   74.424338] wl 0000:03:00.0 wlp3s0: renamed from wlan0

```

I can now setup network as usual via Network Connections.

---

