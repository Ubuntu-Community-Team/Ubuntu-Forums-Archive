---
title: "Issue with AMD graphics &amp; fglrx on Linux mint 16"
date: 2014-06-29
forum: Any Other OS
---

### Post by phil37 on 2014-06-29
Hi

this has been running fine for months ,I had a graphic issue with a game on steam, I checked in device manager which said I wasn't using the fglrx which was recommend and as soon as I selected this driver the problems started.

am very new to Linux so be gentle, am not sure what info I can give you to help but from looking around people usually ask for the below, I have been searching this problem and tried some terminal commands which got me from a blank screen after the grub to getting the desktop loading but with no graphic drivers being used .

Thanks in advanced

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8670D]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
03:00.0 USB controller: Etron Technology, Inc. EJ188/EJ198 USB 3.0 Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```

And

```
Module Size Used by
pci_stub 12622 1 
vboxpci 23194 0 
vboxnetadp 25670 0 
vboxnetflt 27613 0 
vboxdrv 335365 3 vboxnetadp,vboxnetflt,vboxpci
parport_pc 32701 0 
ppdev 17671 0 
rfcomm 69070 0 
bnep 19564 2 
bluetooth 371874 10 bnep,rfcomm
arc4 12608 2 
rt2800usb 27005 0 
rt2x00usb 20713 1 rt2800usb
rt2800lib 79963 1 rt2800usb
rt2x00lib 55238 3 rt2x00usb,rt2800lib,rt2800usb
binfmt_misc 17468 1 
mac80211 596969 3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211 479757 2 mac80211,rt2x00lib
crc_ccitt 12707 1 rt2800lib
kvm_amd 59958 0 
joydev 17377 0 
kvm 431315 1 kvm_amd
crct10dif_pclmul 14289 0 
crc32_pclmul 13113 0 
ghash_clmulni_intel 13259 0 
aesni_intel 55624 0 
aes_x86_64 17131 1 aesni_intel
lrw 13257 1 aesni_intel
gf128mul 14951 1 lrw
glue_helper 13990 1 aesni_intel
ablk_helper 13597 1 aesni_intel
snd_hda_codec_realtek 51465 1 
cryptd 20329 3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi 41276 1 
snd_hda_intel 48171 5 
snd_hda_codec 188738 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep 13602 1 snd_hda_codec
snd_pcm 102033 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc 18710 2 snd_pcm,snd_hda_intel
snd_seq_midi 13324 0 
snd_seq_midi_event 14899 1 snd_seq_midi
snd_rawmidi 30095 1 snd_seq_midi
microcode 23518 0 
snd_seq 61560 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer 29433 2 snd_pcm,snd_seq
psmouse 97626 0 
snd 69141 21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
dm_multipath 22843 0 
serio_raw 13413 0 
scsi_dh 14882 1 dm_multipath
soundcore 12680 1 snd
k10temp 13126 0 
i2c_piix4 22106 0 
mac_hid 13205 0 
lp 17759 0 
parport 42299 3 lp,ppdev,parport_pc
dm_mirror 22056 0 
dm_region_hash 20784 1 dm_mirror
dm_log 18411 2 dm_region_hash,dm_mirror
pata_acpi 13038 0 
hid_logitech_dj 18581 0 
usbhid 53014 0 
hid 101512 4 usbhid,hid_logitech_dj
radeon 1402449 2 
r8169 67341 0 
mii 13934 1 r8169
pata_atiixp 13242 0 
i2c_algo_bit 13413 1 radeon
ttm 83995 1 radeon
ohci_pci 13561 0 
ahci 25819 2 
libahci 31898 1 ahci
drm_kms_helper 52651 1 radeon
drm 296739 4 ttm,drm_kms_helper,radeon
```

---

### Post by coffeecat on 2014-06-29
*Thread moved to **Other OS/Distro Support**.*

I've also added code tags to your temrinal output which makes it easier to read.

> **phil37 said:**
> I have been searching this problem and tried some terminal commands which got me from a blank screen after the grub to getting the desktop loading but with no graphic drivers being used .

Perhaps you could expand on this so that others can help. If you had no graphics drivers, you wouldn't have a functional desktop. Perhaps you've reverted to the default open source driver? The terminal commands that got you back to a desktop would be useful information.

---

### Post by phil37 on 2014-06-29
ok thanks

it was these commands that brought the desktop back, but every time it loads it says cinnamnnd crashed and am in some sort of recovery mode, with a diffrent layout & no sound.

below is the code that seem to get me from the blank screen after the grub

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get update
sudo apt-get remove --purge fglrx*
sudo apt-get install fglrx
sudo apt-get upgrade
sudo reboot
```

---

