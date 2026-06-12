---
title: "Atheros AR9462 Bluetooth, Gobi2000 3G and GPS"
date: 2014-05-29
forum: Any Other OS
---

### Post by AuToFiRE on 2014-05-29
Hello everyone!

I have 2 major issues I would like to learn how to resolve for the future when I feel ready to make and maintain my own personal distro.

One is getting the AR9462 combo WLAN/Bluetooth 4.0 card to have functioning BT4.0. I have tried for weeks now, every single thing I could find with google I have attempted without success, though the instructions outlined [here]("http://orkultus.wordpress.com/2013/01/20/ar9462-wlanbt-combo-bluetooth-4-0-driver-bug-linux-mint-14-solved/") does show promise, if I could figure out what to put in for the third command, I could possibly get it going. 

The second issue I have is with the Gobi 2000 mobile broadband card with standalone GPS. I *did* have the mobile broadband part recognized until I restarted after a 36 hour session of actually trying to get it working and I passed out and completely forgot what I did to get it going, and seemingly forgot to set it to activate at launch. As for the GPS portion, I have yet to get that to work at all, and is virtually the only reason I purchased the Gobi2000, so if my thinkpad is ever stolen, I will be able to track it down the moment it is turned on.

I will post all information requested, hopefully Ive posted enough information to at least get the ball rolling. Please, I beg of all of you to help. I have posted to reddit and several other sites and forums looking for help, and I haven't even received a single reply. I am at the point where I just want to break down and cry, please, for the love of Linus, help?


Kernel: ~3.14.4-031404-generic x86_64
Distro: Linux Mint 16 cinnamon
Laptop: Thinkpad T410 with modified BIOS without whitelist

```
omega@ThinkTank410 ~ $ sudo lspci
[sudo] password for omega: 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
0d:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

```
omega@ThinkTank410 ~ $ sudo lsusb
Bus 002 Device 003: ID 05c6:9204 Qualcomm, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
less /proc/modules

intel_powerclamp 19077 0 - Live 0x0000000000000000
coretemp 17768 0 - Live 0x0000000000000000
kvm_intel 148674 0 - Live 0x0000000000000000
joydev 17575 0 - Live 0x0000000000000000
kvm 471679 1 kvm_intel, Live 0x0000000000000000
arc4 12573 2 - Live 0x0000000000000000
ath9k 152103 0 - Live 0x0000000000000000
ath9k_common 13551 1 ath9k, Live 0x0000000000000000
dm_multipath 27401 0 - Live 0x0000000000000000
crct10dif_pclmul 14250 0 - Live 0x0000000000000000
ath9k_hw 459549 2 ath9k,ath9k_common, Live 0x0000000000000000
crc32_pclmul 13160 0 - Live 0x0000000000000000
qcserial 13139 0 - Live 0x0000000000000000
scsi_dh 14873 1 dm_multipath, Live 0x0000000000000000
usb_wwan 20324 1 qcserial, Live 0x0000000000000000
ghash_clmulni_intel 13216 0 - Live 0x0000000000000000
aesni_intel 152634 803 - Live 0x0000000000000000
ath 29397 3 ath9k,ath9k_common,ath9k_hw, Live 0x0000000000000000
usbserial 45277 2 qcserial,usb_wwan, Live 0x0000000000000000
aes_x86_64 17131 1 aesni_intel, Live 0x0000000000000000
mac80211 676910 1 ath9k, Live 0x0000000000000000
lrw 13323 1 aesni_intel, Live 0x0000000000000000
gf128mul 14951 1 lrw, Live 0x0000000000000000
glue_helper 14095 1 aesni_intel, Live 0x0000000000000000
snd_hda_codec_hdmi 47124 1 - Live 0x0000000000000000
snd_hda_codec_conexant 57479 1 - Live 0x0000000000000000
snd_hda_codec_generic 69424 1 snd_hda_codec_conexant, Live 0x0000000000000000
cfg80211 531467 3 ath9k,ath,mac80211, Live 0x0000000000000000
psmouse 109109 0 - Live 0x0000000000000000
snd_hda_intel 57222 3 - Live 0x0000000000000000
snd_hda_codec 142651 4 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel, Live 0x0000000000000000
thinkpad_acpi 81965 1 - Live 0x0000000000000000
serio_raw 13462 0 - Live 0x0000000000000000
snd_hwdep 13613 1 snd_hda_codec, Live 0x0000000000000000
ablk_helper 13597 1 aesni_intel, Live 0x0000000000000000
snd_pcm 108860 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec, Live 0x0000000000000000
nvram 14462 1 thinkpad_acpi, Live 0x0000000000000000
cryptd 20531 404 ghash_clmulni_intel,aesni_intel,ablk_helper, Live 0x0000000000000000
snd_seq_midi 13324 0 - Live 0x0000000000000000
snd_seq_midi_event 14899 1 snd_seq_midi, Live 0x0000000000000000
microcode 24391 0 - Live 0x0000000000000000
snd_rawmidi 30465 1 snd_seq_midi, Live 0x0000000000000000
snd_seq 66061 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
snd_timer 30038 2 snd_pcm,snd_seq, Live 0x0000000000000000
mei_me 18546 0 - Live 0x0000000000000000
lpc_ich 21163 0 - Live 0x0000000000000000
bnep 19884 2 - Live 0x0000000000000000
mei 87127 1 mei_me, Live 0x0000000000000000
intel_ips 18520 0 - Live 0x0000000000000000
snd 73979 19 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_codec,thinkpad_acpi,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_seq_device,snd_timer, Live 0x0000000000000000
mac_hid 13253 0 - Live 0x0000000000000000
soundcore 12680 1 snd, Live 0x0000000000000000
parport_pc 32866 0 - Live 0x0000000000000000
ppdev 17711 0 - Live 0x0000000000000000
rfcomm 74734 0 - Live 0x0000000000000000
bluetooth 426845 10 bnep,rfcomm, Live 0x0000000000000000
6lowpan_iphc 18968 1 bluetooth, Live 0x0000000000000000
lp 17799 0 - Live 0x0000000000000000
parport 42481 3 parport_pc,ppdev,lp, Live 0x0000000000000000
binfmt_misc 17508 1 - Live 0x0000000000000000
dm_mirror 22356 0 - Live 0x0000000000000000
dm_region_hash 21010 1 dm_mirror, Live 0x0000000000000000
dm_log 18527 2 dm_mirror,dm_region_hash, Live 0x0000000000000000
mxm_wmi 13021 0 - Live 0x0000000000000000
i915 826549 9 - Live 0x0000000000000000
i2c_algo_bit 13564 1 i915, Live 0x0000000000000000
drm_kms_helper 53224 1 i915, Live 0x0000000000000000
firewire_ohci 45289 0 - Live 0x0000000000000000
drm 308197 5 i915,drm_kms_helper, Live 0x0000000000000000
e1000e 257783 0 - Live 0x0000000000000000
firewire_core 69403 1 firewire_ohci, Live 0x0000000000000000
sdhci_pci 23263 0 - Live 0x0000000000000000
ahci 30119 1 - Live 0x0000000000000000
sdhci 43409 1 sdhci_pci, Live 0x0000000000000000
crc_itu_t 12707 1 firewire_core, Live 0x0000000000000000
ptp 18980 1 e1000e, Live 0x0000000000000000
pps_core 19381 1 ptp, Live 0x0000000000000000
wmi 19363 1 mxm_wmi, Live 0x0000000000000000
video 19914 1 i915, Live 0x0000000000000000

```

```
omega@ThinkTank410 ~ $ rfkill list all
0: tpacpi_wwan_sw: Wireless WAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
omega@ThinkTank410 ~ $ lsmod
Module                  Size  Used by
intel_powerclamp       19077  0 
coretemp               17768  0 
kvm_intel             148674  0 
joydev                 17575  0 
kvm                   471679  1 kvm_intel
arc4                   12573  2 
ath9k                 152103  0 
ath9k_common           13551  1 ath9k
dm_multipath           27401  0 
crct10dif_pclmul       14250  0 
ath9k_hw              459549  2 ath9k_common,ath9k
crc32_pclmul           13160  0 
qcserial               13139  0 
scsi_dh                14873  1 dm_multipath
usb_wwan               20324  1 qcserial
ghash_clmulni_intel    13216  0 
aesni_intel           152634  829 
ath                    29397  3 ath9k_common,ath9k,ath9k_hw
usbserial              45277  2 qcserial,usb_wwan
aes_x86_64             17131  1 aesni_intel
mac80211              676910  1 ath9k
lrw                    13323  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            14095  1 aesni_intel
snd_hda_codec_hdmi     47124  1 
snd_hda_codec_conexant    57479  1 
snd_hda_codec_generic    69424  1 snd_hda_codec_conexant
cfg80211              531467  3 ath,ath9k,mac80211
psmouse               109109  0 
snd_hda_intel          57222  3 
snd_hda_codec         142651  4 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel
thinkpad_acpi          81965  1 
serio_raw              13462  0 
snd_hwdep              13613  1 snd_hda_codec
ablk_helper            13597  1 aesni_intel
snd_pcm               108860  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nvram                  14462  1 thinkpad_acpi
cryptd                 20531  417 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              24391  0 
snd_rawmidi            30465  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30038  2 snd_pcm,snd_seq
mei_me                 18546  0 
lpc_ich                21163  0 
bnep                   19884  2 
mei                    87127  1 mei_me
intel_ips              18520  0 
snd                    73979  19 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
mac_hid                13253  0 
soundcore              12680  1 snd
parport_pc             32866  0 
ppdev                  17711  0 
rfcomm                 74734  0 
bluetooth             426845  10 bnep,rfcomm
6lowpan_iphc           18968  1 bluetooth
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
binfmt_misc            17508  1 
dm_mirror              22356  0 
dm_region_hash         21010  1 dm_mirror
dm_log                 18527  2 dm_region_hash,dm_mirror
mxm_wmi                13021  0 
i915                  826549  9 
i2c_algo_bit           13564  1 i915
drm_kms_helper         53224  1 i915
firewire_ohci          45289  0 
drm                   308197  5 i915,drm_kms_helper
e1000e                257783  0 
firewire_core          69403  1 firewire_ohci
sdhci_pci              23263  0 
ahci                   30119  1 
sdhci                  43409  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ptp                    18980  1 e1000e
pps_core               19381  1 ptp
wmi                    19363  1 mxm_wmi
video                  19914  1 i915

```

---

### Post by jeremy31 on 2014-05-29
Try installing linux-firmware and see if that gets bluetooth working

---

### Post by AuToFiRE on 2014-05-29
Its already the newest package

---

### Post by jeremy31 on 2014-05-30
Have you looked at ```
dmesg | grep Bluetooth
``` for errors?

---

### Post by AuToFiRE on 2014-05-30
No errors.
```
omega@ThinkTank410 ~ $ dmesg | grep Bluetooth
omega@ThinkTank410 ~ $ 

```

---

### Post by jeremy31 on 2014-05-30
How about ```
dmesg | grep btusb
```  Usually atheros BT shows up in ```
lsusb
``` and you should see btusb and ath3k in lsmod if it is detected

---

### Post by AuToFiRE on 2014-05-31
```
omega@ThinkTank410 ~ $ dmesg | grep btusb
omega@ThinkTank410 ~ $ 

```


```
omega@ThinkTank410 ~ $ lsusb
Bus 002 Device 003: ID 05c6:9204 Qualcomm, Inc. <---Gobi2000 but not activated (which would be 05c6:9205)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jeremy31 on 2014-05-31
Have you downloaded linux-firmware?  Ubuntu might need a file or 2 to get BT running

---

### Post by howefield on 2014-05-31
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by AuToFiRE on 2014-05-31
> **jeremy31 said:**
> Have you downloaded linux-firmware?  Ubuntu might need a file or 2 to get BT running

Indeed I have.

---

### Post by jeremy31 on 2014-06-11
I would try out LM17 as support for 16 ends in July. LM17 will be supported until April 2019

---

