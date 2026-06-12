---
title: "ubuntu 14.04, no wifi, macbook air"
date: 2014-06-25
forum: Apple Hardware Users
---

### Post by Felix_Koutchinski on 2014-06-25
hey guys,

Today I installed Ubuntu 14.04 for the first time. It is my first Linux OS and naturally I wasn't sure why my Wifi did not work from the beginning. I started searching for answers and found that many people have the same issue. The answers that were found on several sites (installing new kernels f.e.) seem not to work out for me as I tried the whole day, without getting any new result. So I came to my last resort. Asking people who know better than I do :-)

**lspci**
```

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Multimedia controller: Broadcom Corporation Device 1570
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
04:00.0 SATA controller: Samsung Electronics Co Ltd Apple PCIe SSD (rev 01)

```


[B]sudo lsmod
[/B]```
Module                  Size  Used by
hfsplus               103732  1 
nls_utf8               12557  1 
isofs                  40285  0 
snd_hda_codec_cirrus    18855  1 
snd_hda_codec_generic    70087  1 snd_hda_codec_cirrus
snd_hda_codec_hdmi     52339  1 
btusb                  32605  0 
asix                   39141  0 
hid_generic            12559  0 
usbnet                 44000  1 asix
mii                    13981  2 asix,usbnet
snd_hda_intel          30608  10 
snd_hda_controller     35518  1 snd_hda_intel
snd_hda_codec         144889  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_cirrus
joydev                 17587  0 
snd_hwdep              13613  1 snd_hda_codec
hid_apple              13546  0 
snd_pcm               113863  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
usbhid                 53122  0 
intel_rapl             19196  0 
hid                   110572  3 hid_generic,usbhid,hid_apple
bcm5974                17688  0 
x86_pkg_temp_thermal    14312  0 
intel_powerclamp       19099  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
coretemp               13638  0 
snd_rawmidi            30865  1 snd_seq_midi
bnep                   19884  2 
kvm_intel             149086  0 
rfcomm                 75114  8 
kvm                   464279  1 kvm_intel
bluetooth             467172  22 bnep,btusb,rfcomm
6lowpan_iphc           18968  1 bluetooth
applesmc               19564  0 
crct10dif_pclmul       14268  0 
crc32_pclmul           13180  0 
input_polldev          14607  1 applesmc
ghash_clmulni_intel    13230  0 
snd_seq                67636  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           152648  1 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
aes_x86_64             17131  1 aesni_intel
lrw                    13323  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            14095  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20531  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_timer              30118  2 snd_pcm,snd_seq
i915                  945508  5 
snd                    74235  31 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
lpc_ich                21176  0 
drm_kms_helper         62042  1 i915
mei_me                 19565  0 
drm                   316819  5 i915,drm_kms_helper
soundcore              12680  2 snd,snd_hda_codec
mei                    88632  1 mei_me
sbs                    13682  0 
i2c_algo_bit           13564  1 i915
sbshc                  13847  1 sbs
video                  20311  1 i915
spi_pxa2xx_platform    23302  0 
mac_hid                13275  0 
apple_bl               14007  0 
nls_iso8859_1          12713  1 
parport_pc             32906  0 
ppdev                  17711  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
ahci                   30167  4 
libahci                32191  1 ahci

```

[B]
rfkill list all[/B]
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

It is awkward, that there is no wireless shown here.

Also, this piece of information:
[IMG]http://oi61.tinypic.com/33p6c9h.jpg[/IMG]


I hope you can help :)

Thanks!

---

### Post by bapoumba on 2014-06-25
*Thread moved to **Apple Users**.*

---

### Post by varunendra on 2014-06-26
Welcome to the forums Felix_Koutchinski!

The screenshot you posted was asking you to "Restart", did you?

Your wireless card is one of the latest ones that support AC speeds, and unfortunately the opensource drivers don't yet support it. Your only hope is the proprietary driver suggested by the "Additional Driver" program, and if that doesn't work either, I doubt there is much hope.

Please post back what is the situation after the reboot. Whether it worked or not can be a valuable feedback for us wireless troubleshooters. We may also be able to try our luck on a few tweaks if required.

If it didn't work, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) This report may help us optimizing the wifi in hope to make it work.

---

### Post by Felix_Koutchinski on 2014-06-26
hey varunendra,
thank you for welcoming me.
yes, indeed. i actually restarted quite a couple of times, just to be sure.
i ran the script as you told me. results can be seen here:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

purplepanda 3.16.0-031600rc2-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i7-4650U CPU @ 1.70GHz
Memory : 7924 MB
Uptime : 17:22:36 up 2 min,  1 user,  load average: 0,30, 0,38, 0,17


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. Device [106b:0117]
04:00.0 SATA controller [0106]: Samsung Electronics Co Ltd Apple PCIe SSD [144d:1600] (rev 01)


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 003: ID 1058:0730 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:0291 Apple, Inc. 
Bus 001 Device 006: ID 05ac:828f Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 007: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface     Soft blocked  Hard blocked
0: hci0: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




module parameters ~~~~~~~~~~~~~~~~~~


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o======o========o==============o=========o===========o==============o===========
 Interface & ID | Type | Driver | State        | Default | Speed     | Support      | HW Addr   
================o======o========o==============o=========o===========o==============o===========
                |      |        |              |         |           |              |           
----------------+------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_DE.UTF-8)
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-031600rc2-generic root=UUID=63659252-30f7-49a0-933e-b4330a9d4cfc ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-031600rc2-generic root=UUID=63659252-30f7-49a0-933e-b4330a9d4cfc ro quiet splash vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-031600rc2-generic root=UUID=63659252-30f7-49a0-933e-b4330a9d4cfc ro quiet splash vt.handoff=7
[    0.022733] Initializing cgroup subsys net_cls
[    0.022746] Initializing cgroup subsys net_prio
[    2.671093] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.671647] audit: initializing netlink subsys (disabled)
[    4.990629] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========
```

Now I feel kind of down. not getting access to the internet with my -too-new-machine- . meh. i believe in you guys!

---

### Post by varunendra on 2014-06-26
Oops! Your card is not supported by even the STA driver (wl).. looks like we may be out of luck with this one.

Although there is still one (very little) hope - ndiswrapper with Windows driver. I can almost guaranty that it won't help, but IF it could give us even a 'somehow-usable' connection, consider yourself lucky. Here's a general guide on how to use it (general, because I don't have much experience with it, so can't give specific instructions without spending more time than I may currently have) : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

**PS:**
You used 'Quote' tags which can't preserve formatting. Use 'Code' tags instead. You can edit your post to do so now, see the "Use Code Tags" link in my sig. to see how. ;)

---

### Post by Felix_Koutchinski on 2014-06-26
Wait, what?
Are you telling me I will not have wifi on my laptop?
Well, that killed of Linux is a fairly fast manner.

(I can not download any packages, liked in the post- Seem to be offline?)

---

### Post by techcaptain on 2014-06-29
This is weird.. I have a MacBook Air (new one) and I'm not having any problems with WiFi.

---

### Post by varunendra on 2014-06-29
> **Hyunwoo_Jo said:**
> This is weird.. I have a MacBook Air (new one) and I'm not having any problems with WiFi.

With the same wifi card?

Please check (and post here) the output of command -
```
lspci -nnk | grep -iA2 net
```

It will be a discovery if yours is the same card and works on Ubuntu, although I have almost no hope that it is the same one.

---

### Post by techcaptain on 2014-06-30
I have a MacBookAir6,2 i think... let me double check after I boot in Ubuntu...
(Just a note: I'm running off ubuntu from a usb stick :P)

---

### Post by techcaptain on 2014-06-30
I got this:

```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. Device [106b:0117]
    Kernel driver in use: wl

```

---

### Post by techcaptain on 2014-06-30
For rfkill list all:

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by techcaptain on 2014-06-30
[B]sudo lsmod:
[/B]
```

Module                  Size  Used by
michael_mic            12612  4 
arc4                   12608  2 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
dm_crypt               23177  0 
intel_powerclamp       14705  0 
snd_hda_codec_cirrus    18855  1 
snd_hda_codec_hdmi     46207  1 
coretemp               13435  0 
joydev                 17381  0 
kvm_intel             143060  0 
snd_hda_intel          52355  10 
bcm5974                17589  0 
kvm                   451511  1 kvm_intel
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_cirrus
btusb                  32412  0 
applesmc               19308  0 
lib80211_crypt_tkip    17619  0 
crct10dif_pclmul       14289  0 
wl                   4207846  0 
crc32_pclmul           13113  0 
input_polldev          13896  1 applesmc
snd_hwdep              13602  1 snd_hda_codec
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lib80211               14381  2 wl,lib80211_crypt_tkip
snd_seq_midi           13324  0 
bnep                   19624  2 
dm_multipath           22873  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              484040  1 wl
mei_me                 18627  0 
snd_rawmidi            30144  1 snd_seq_midi
rfcomm                 69160  8 
glue_helper            13990  1 aesni_intel
scsi_dh                14882  1 dm_multipath
bluetooth             395423  22 bnep,btusb,rfcomm
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ablk_helper            13597  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mei                    82274  1 mei_me
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lpc_ich                21080  0 
snd_timer              29482  2 snd_pcm,snd_seq
mac_hid                13205  0 
spi_pxa2xx_platform    23056  0 
snd                    69238  31 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus,snd_seq_midi
parport_pc             32701  0 
ppdev                  17671  0 
soundcore              12680  1 snd
apple_bl               13993  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
squashfs               48362  1 
overlayfs              27916  1 
nls_iso8859_1          12713  1 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
hid_apple              13386  0 
usbhid                 52616  0 
hid                   106148  3 hid_generic,usbhid,hid_apple
usb_storage            62209  2 
i915                  783485  5 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52758  1 i915
ahci                   25819  0 
drm                   302817  4 i915,drm_kms_helper
libahci                32168  1 ahci
video                  19476  1 i915

```

---

### Post by techcaptain on 2014-06-30
and... lspci:

```

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Multimedia controller: Broadcom Corporation Device 1570
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
04:00.0 SATA controller: Samsung Electronics Co Ltd Apple PCIe SSD (rev 01)


```

---

### Post by varunendra on 2014-06-30
> **Hyunwoo_Jo said:**
> I got this:

```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. Device [106b:0117]
    Kernel driver in use: wl

```

Wow! This is a wonderful news! If not too much trouble, please also post back the outputs of -
```
modinfo wl
dpkg -l | grep bcmwl
```
..so we can see exactly which driver and package versions they are. This maybe a lifesaver for Felix_Koutchinski (or a lifesaver for Ubuntu, on his macbook :p).

---

### Post by techcaptain on 2014-06-30
modinfo wl:
```

filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


```

---

### Post by techcaptain on 2014-06-30
and for dpkg -l | grep bcmwl:
```

ii  bcmwl-kernel-source                                   6.30.223.141+bdcom-0ubuntu2                         amd64        Broadcom 802.11 Linux STA wireless driver source

```

---

### Post by varunendra on 2014-06-30
Thanks techcaptain, it's a much appreciated feedback! :)

Since this version is not even the latest one (is out from 22-Nov-2013), now I doubt if even the installation finished properly in Felix_Koutchinski's case.

@ Felix_Koutchinski,

If you wish to try it once more, can you boot into live mode and try installing the sta driver again please? Use a wired connection to get connected to internet, and run the following commands to install it -
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

If nothing happens after installation, check if it is loaded -
```
lsmod | grep wl
```
If not, load it manually -
```
sudo modprobe -v wl
```
and check again. If you still can't scan or connect to wireless networks, please post the version you got -
```
dpkg -l | grep bcmwl
```
..as well as the versions available for you in the repos -
```
apt-cache show bcmwl-kernel-source | grep Version
```

---

### Post by techcaptain on 2014-06-30
:)

---

### Post by yurusuu on 2014-07-03
**techcapitan**, **varunendra**, i'm not Felix, but you really saved me!  i have BCM4360 adapter, and after hours of pain,"update of bcmwl-kernel-source" helped perfectly)))

---

### Post by varunendra on 2014-07-04
Welcome to the forums yurusuu! Thanks for the feedback! :)

---

### Post by shadesofoctober on 2014-07-10
If I could just throw in my 2 cents for Felix real quick. I run a 4331, and the bcmwl driver works great for me, much better than b43.
1. For some reason, when I originally installed bcmwl, I had to do a restart before it would detect any networks, even with a manual modprobe insert.
2. More likely, Felix is running a newer kernel (3.16) than the stock Ubuntu kernel at this point in time.
When attempting to get wl drivers working under Fedora 20, the packages provided under RPMFusion refused to build a wl kmod for the latest kernel released. (An RPM simply wasn't released for kernels beyond the one launched for Fedora 20 at that point...)
 I had to reinstall Fedora and then install wl *before* installing any kernel updates. After this, it functioned (I believe under updated kernels as well).
And yes, attempting to force an RPM install of that particular wl kmod package with the updated kernel broke dependencies, causing many issues.

My suggestion is run the official stable kernel from Ubuntu and install bcmwl-kernel-source under that.

---

### Post by tjqt06 on 2014-11-21
hi, I have the same issue as this one but different laptop. Mine is Acer E14.

here is the version of my wlan

> ii  bcmwl-kernel-source                                   6.30.223.141+bdcom-0ubuntu2                         amd64        Broadcom 802.11 Linux STA wireless driver source



repos version

> Version: 6.30.223.141+bdcom-0ubuntu2



please help. thanks...

---

### Post by Kale_Freemon on 2014-11-22
I had an issue with my Macbook 4,1 when Ubuntu 14.04 had that driver installed by default.

What worked for me was to follow the instructions on this post: [http://ubuntuforums.org/showthread.php?t=2230194&p=13052784#post13052784](http://ubuntuforums.org/showthread.php?t=2230194&p=13052784#post13052784)

---

### Post by dondondonkaibudafl on 2014-11-30
I am also suffering slow wifi speed on my Ubuntu 14.04 on MBA 6.2. During the installation I used a wifi adapter (dlink dwa140) so the bcmwl driver was ready right after first reboot. The bcmwl driver itself doesn't work well at my home, either after purge and installing newer versions. However, it is pretty fast with my office's Verizon wifi router. Not sure if I turn off 5G on my home wifi router will work better or not. I feel my ubuntubook air 6.2 is a little bit handicapped with a wifi adapter ...

---

### Post by ceres2 on 2015-02-22
Hello,

sorry for hijacking the thread, dunno if the op got it to work, but..
.. just wanted to write that i just successfully got wlan bcm4360 to work on a macbook air 2013 (6,1) in ubuntu 14.04.2
At first i tried all the things explained here and did not even got a wl kernel modul at all.
Just a problem report at boot telling DKMS couldn't build bcmwl-6.30.223.141+bdcom.
The choosing of Prereleased Updates (trusty proposed) Updates followed by a

```

sudo apt-get install update
sudo apt-get install ugrade
sudo apt-get autoremove
sudo apt-get install linux-headers-generic-lts-utopic
sudo apt-get install ugrade

```
followed by a reboot,
Then selecting the proprietary driver "Using Broadcom 802.11 Linux STA .." under Software & Updates Additional Drivers
 did the trick.
i now have two versions in the apt-cache
```
xy@MBAnotMBA:~$ sudo apt-cache show bcmwl-kernel-source | grep -i version
Version: 6.30.223.248+bdcom-0ubuntu0.1
Version: 6.30.223.141+bdcom-0ubuntu2

```
the 0.1 version is the one the works.

edit:
and i removed the blacklisting of the bc kernel modules
/edit
Regards,
 CereS

---

### Post by edib on 2016-01-12
After installing 15.10, from usb stick,  
# dpkg -i /pool/main/d/dkms/*.deb
# dpkg -i /pool/restricted/b/bcmwl/*.deb

---

### Post by tekeous-s on 2016-09-28
Macbook Air 2015, Ubuntu GNOME 16.04 LTS, etc.

Wi-fi didn't work on install, so I grabbed a USB wifi adapter, plugged in in, and ran "apt-get update" and clicked "Mark All Upgrades" in Synaptic(apt-get upgrade). After a reboot I opened Additional Drivers and activated both the Broadcom driver and the Intel microcode driver, rebooted, and wifi worked(still does) just fine.

---

