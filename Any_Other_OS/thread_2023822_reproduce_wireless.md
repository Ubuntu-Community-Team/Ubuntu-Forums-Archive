---
title: "reproduce wireless"
date: 2012-07-12
forum: Any Other OS
---

### Post by Mr.Dee on 2012-07-12
So I have distro A (wireless works great) but really want to use distro B (wireless works, but not that great)

Is there a way that I can replicate the functionality of distro A on distro B.

Crazy ideas welcome!

---

### Post by uRock on 2012-07-13
The easiest way is to tell us what hardware and OSes you have.

---

### Post by Kirk Schnable on 2012-07-13
> **uRock said:**
> The easiest way is to tell us what hardware and OSes you have.


Please tell us which distro you're running, which kernel version, and what hardware. 

Kernel version can be found by running:
```
uname -r
```

And hardware can be found by running:
```
lspci
```

Kirk

---

### Post by Mr.Dee on 2012-07-13
The output below is for Linux mint, which is the distro I want to run.  However, wireless does not work to connect to an ad-hoc access point under linux mint. (cellphone ad-hoc).  It works flawlessly with JoliOS.  So I want to copy JoliOS.

```
$ uname -r
3.2.0-23-generic

$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
09:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

---

### Post by Mr.Dee on 2012-07-13
```
$ lsmod
Module                  Size  Used by
zram                   18193  2 
arc4                   12473  2 
b43                   347515  0 
ssb                    55403  1 b43
joydev                 17393  0 
pcmcia                 39791  2 b43,ssb
pcmcia_core            21511  1 pcmcia
brcmsmac              522076  0 
mac80211              465127  2 b43,brcmsmac
brcmutil               14355  1 brcmsmac
cfg80211              179271  3 b43,brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
snd_hda_codec_realtek   174055  1 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                87140  0 
serio_raw              13027  0 
ideapad_laptop         17890  0 
sparse_keymap          13658  1 ideapad_laptop
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414568  2 
rfcomm                 37289  0 
bnep                   17711  2 
bluetooth             182779  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bcma                   25919  2 b43,brcmsmac
wmi                    18744  0 
compat                 13247  9 b43,ssb,brcmsmac,mac80211,cfg80211,rfcomm,bnep,bluetooth,bcma
r8169                  56321  0 
drm_kms_helper         45466  1 i915
binfmt_misc            17292  1 
drm                   197692  3 i915,drm_kms_helper
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17699  0 
usb_storage            39646  1 ums_realtek
```

---

### Post by nothingspecial on 2012-07-13
*Thread moved to **Other OS/Distro Talk**.*

---

