---
title: "Alsa messed up after installing Realtek Driver"
date: 2013-03-16
forum: Any Other OS
---

### Post by MajorPain931 on 2013-03-16
Hi guys,
at first I need to tell you, that I'm using Linux Mint. I already posted my problem in the Linux Mint forums, but it seems like nobody knows a solution for my problem, so I decided to ask the bigger Ubuntu community.
I installed the Realtek Driver for Linux because i had the problem, that with the snd_hda_intel driver I had some system freezes, but now I have a different and more serious problem... 
Everything seems to be messed up now.
Pulseaudio just recognizes "Dummy Output", so no soundcard.
Alsa doesn't seem to work at all.
```
cat /proc/asound/cards 
--- no soundcards ---
```
Also alsamixer, alsaconf etc. dont work, I just get this response:
```
alsamixer
cannot open mixer: No such file or directory
```
My 1st try was to completely reinstall alsa and pulseaudio, but the result is the same.
In lsmod I've seen, that the snd_hda_intel module isn't loaded, so I tryed to load it manually:
```
sudo modprobe snd_hda_intel
WARNING: Error inserting snd_hda_codec (/lib/modules/3.5.0-25-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Invalid argument
FATAL: Error inserting snd_hda_intel (/lib/modules/3.5.0-25-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Invalid argument
```
And here the surprise...
I've read, that someone already had such a problem and he reinstalled the whole kernel and it did work again.
So I did the same, but it didn't work either. He can't load the module.
I already tryed to insmod the module from an older kernel (3.5.0-17-generic), but I get the same error message...

What did the Realtek-Driver do to my system and the better question, how can I get it working again without reinstalling everything? :(

Some information:

OS: Linux Mint 14 Nadia Cinnamon 64-Bit
Linux Kernel:  3.5.0-25-generic
Linux Kernel, when I installed Linux: 3.5.0-17-generic

lspci -v (Here he says, the module snd_hda_intel will be loaded for sound):
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d2000000-d30fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3901
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d3400000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 42
    Memory at d3a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d3a14000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d3a19000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d3a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d3900000-d39fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: d3800000-d38fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d3a18000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 3977
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at d3a17000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: medium devsel, IRQ 10
    Memory at d3a15000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de3 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3901
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [disabled] [size=128]
    Expansion ROM at d3000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nouveau, nvidiafb

02:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
    Subsystem: Lenovo Device 3979
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d3900000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: alx
    Kernel modules: alx

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Broadcom Corporation Device 0587
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d3800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, bcma
```

lsmod:
```
Module                  Size  Used by
michael_mic            12613  4 
lib80211_crypt_tkip    17380  0 
wl                   2573608  0 
lib80211               14382  2 lib80211_crypt_tkip,wl
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  12 
binfmt_misc            17501  1 
arc4                   12530  2 
joydev                 17458  0 
mac80211              540032  0 
brcmutil               14756  0 
cfg80211              206797  1 mac80211
cordic                 12575  0 
coretemp               13401  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
btusb                  22475  0 
bluetooth             209249  22 bnep,rfcomm,btusb
rts5139               356200  0 
microcode              22804  0 
ideapad_laptop         18087  0 
sparse_keymap          13891  1 ideapad_laptop
lpc_ich                17062  0 
snd_pcm                96415  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
alx                    68240  0 
mdio                   13808  1 alx
psmouse                95595  0 
serio_raw              13216  0 
snd_timer              29371  1 snd_pcm
mac_hid                13206  0 
snd                    76527  2 snd_pcm,snd_timer
i915                  520615  3 
mei                    40691  0 
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
video                  19391  1 i915
soundcore              15048  1 snd
snd_page_alloc         18485  1 snd_pcm
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp

```

alsa-base-conf (Didnt change anything myself, but maybe realtek):
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

If you need more information, just tell me

---

### Post by Perfect Storm on 2013-03-16
Moved to Other OS/Distro Talk.

---

