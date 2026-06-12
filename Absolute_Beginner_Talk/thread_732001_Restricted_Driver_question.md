---
title: "Restricted Driver question"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by spectrevk on 2008-03-22
Does the restricted driver manager handle updates as well? How can I be certain of which version of the ATI driver I'm using? I'm asking because I think the version I have is causing some problems with my suspend/hibernate, and I'm unable to use Compiz.

---

### Post by maddog39 on 2008-03-22
Yes, the update manager will install updates to your restricted drivers. As far as the suspend/hibernate issue, that is a common problem with the drivers. Although the update manager doesnt upgrade to new versions of the driver, it only updates it for security fixes and such.

---

### Post by billgoldberg on 2008-03-22
> **spectrevk said:**
> Does the restricted driver manager handle updates as well? How can I be certain of which version of the ATI driver I'm using? I'm asking because I think the version I have is causing some problems with my suspend/hibernate, and I'm unable to use Compiz.

Don't think so.

You can always use envy to install the latest driver. (google for it)

---

### Post by VyperX on 2008-03-22
Go to Terminal and type ''lsmod'' and press enter, then type ''lspci'' and press enter
post the output of "lsmod" and "lspci" (without the quotes)

Hope this helps

---

### Post by spectrevk on 2008-03-22
Here you go:

```
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  0 
ipv6                  273892  8 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
af_packet              24840  4 
fglrx                 656352  11 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               5504  0 
button                  8976  0 
video                  18060  0 
battery                11012  0 
sbs                    19592  0 
dock                   10656  0 
ac                      6148  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_atiixp_modem       17160  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_atiixp             21132  3 
snd_ac97_codec        100644  2 snd_atiixp_modem,snd_atiixp
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
pcspkr                  4224  0 
snd_pcm                80388  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
serio_raw               8068  0 
psmouse                39952  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_atiixp_modem,snd_seq_oss,snd_atiixp,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_atiixp_modem,snd_atiixp,snd_pcm
k8temp                  6656  0 
bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
i2c_piix4               9740  0 
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
i2c_core               26112  1 i2c_piix4
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
8139too                27776  0 
atiixp                  7056  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,atiixp
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  3 ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
spectrevk@spectrevk-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by spectrevk on 2008-03-22
The weird thing is that I've even tried using a different video card driver, and while it would actually suspend, it wouldn't come back from suspend, which is really annoying.

---

### Post by spectrevk on 2008-03-23
Is it possible that upgrading to Hardy Heron might fix this?

---

### Post by Sef on 2008-03-23
> Is it possible that upgrading to Hardy Heron might fix this?

Yes, it is possible, but not guaranteed.

---

### Post by spectrevk on 2008-03-23
Well, it wasn't mentioned in the notes, but since the problem with ATI's drivers has been filed as a bug report before, I thought maybe they'd done something about it. Is there any way to find out for sure?

---

### Post by spectrevk on 2008-03-23
Well, interestingly enough, the update to 8.04 fixed my suspend problem, but now my built-in wireless doesn't work anymore, and the restricted driver appears as "In Use", but doesn't have a checkmark next to it, and no amount of clicking on the checkmark and restarting the computer seems to fix it.

---

