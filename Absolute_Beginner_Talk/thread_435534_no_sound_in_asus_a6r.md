---
title: "no sound in asus a6r"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by natharin on 2007-05-07
what to do ? please help

---

### Post by BoneKracker on 2007-05-07
I suggest you supply more information.

---

### Post by natharin on 2007-05-07
_aplay -l_
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


_Usage: lsmod_
Module                  Size  Used by
snd_rtctimer            4384  0 
isofs                  36284  1 
udf                    85252  0 
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
fglrx                 540004  11 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
container               5248  0 
video                  16388  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
button                  8720  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  2 
vfat                   14208  1 
fat                    53916  1 vfat
nls_utf8                3072  1 
ntfs                  107764  1 
lp                     12452  0 
fuse                   46612  0 
pcmcia                 39212  0 
joydev                 10816  0 
bcm43xx               125332  0 
ieee80211softmac       31232  1 bcm43xx
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              34760  2 bcm43xx,ieee80211softmac
snd_atiixp_modem       17160  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
sdhci                  18700  0 
mmc_core               26756  1 sdhci
irda                  201276  2 irtty_sir,sir_dev
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211_crypt         7040  1 ieee80211
snd_atiixp             20620  1 
snd_ac97_codec         98336  2 snd_atiixp_modem,snd_atiixp
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              23684  3 snd_rtctimer,snd_seq,snd_pcm
shpchp                 34324  0 
pcspkr                  4224  0 
crc_ccitt               3072  1 irda
i2c_piix4               9740  0 
pci_hotplug            32576  1 shpchp
serio_raw               7940  0 
psmouse                38920  0 
i2c_core               22784  2 i2c_ec,i2c_piix4
ati_agp                10124  0 
agpgart                35400  2 fglrx,ati_agp
snd                    54020  13 snd_atiixp_modem,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_atiixp_modem,snd_atiixp,snd_pcm
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
8139too                27648  0 
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  5 
usbhid                 26592  0 
hid                    27392  1 usbhid
atiixp                  7440  0 [permanent]
generic                 5124  0 [permanent]
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               34188  0 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
ohci_hcd               22532  0 
usbcore               134280  4 usbhid,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

_ lspci -vv_
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: ATI Technologies Inc Unknown device 5a31
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 64
        Region 3: Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fe100000-fe1fffff
        Prefetchable memory behind bridge: bdf00000-ddefffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: I/O ports at 0b00 [size=16]
        Region 1: Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at ff00 [size=16]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        I/O behind bridge: 0000a000-0000bfff
        Memory behind bridge: fe200000-feafffff
        Prefetchable memory behind bridge: ddf00000-dfefffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1183
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min), Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at febfcc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1186
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min), Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at febfc800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1182
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 255 (2000ns min), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at 9800 [size=256]
        Region 2: Memory at fe1f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fe1c0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1045
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at b800 [size=256]
        Region 1: Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fe200000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 24000000-27fff000 (prefetchable)
        Memory window 1: 28000000-2bfff000
        I/O window 0: 0000a000-0000a0ff
        I/O window 1: 0000a400-0000a4ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin C routed to IRQ 20
        Region 0: Memory at feaff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1187
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 5
        Region 0: Memory at feaff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. A6U notebook embedded card
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at feafc000 (32-bit, non-prefetchable) [size=8K]

---

### Post by Sef on 2007-05-07
Could you paste the output of this command from your terminal:

```
cat /etc/modprobe.d/sources.list
```

Just checking if you have the same problem I do.   I need to make a change to get sound.

---

### Post by natharin on 2007-05-07
there is no No such file or directory in my computer

---

### Post by novithor on 2007-05-08
easy solution that works for my computer that's the same of your

open the terminal and type alsamixer

then you must  move with right arrow until you reach "external" and press M so you diable that.
now you quit alsamixer with "esc" and you have to put on the volume form the icon in the right part of the screen and it shoud works

sorry for my bad english i hope it help you!!

---

### Post by Najand on 2007-05-09
> **novithor said:**
> easy solution that works for my computer that's the same of your

open the terminal and type alsamixer

then you must  move with right arrow until you reach "external" and press M so you diable that.
now you quit alsamixer with "esc" and you have to put on the volume form the icon in the right part of the screen and it shoud works

sorry for my bad english i hope it help you!!

Wow! It was great and worked for me... I was looking for a solution for more than a week.

---

### Post by novithor on 2007-05-10
:popcorn: :)

---

### Post by natharin on 2007-05-13
> **novithor said:**
> easy solution that works for my computer that's the same of your

open the terminal and type alsamixer

then you must  move with right arrow until you reach "external" and press M so you diable that.
now you quit alsamixer with "esc" and you have to put on the volume form the icon in the right part of the screen and it shoud works

sorry for my bad english i hope it help you!!


[COLOR="Red"]THANK U SO MUCH[/COLOR]:guitar: :guitar: :guitar:

---

### Post by rootleafhmmm on 2007-05-18
this thing really works highly recommended on my 64 bit Feisty fawn

---

### Post by EcoLDK on 2007-05-19
Woooooooooohoooooo :-) at  last it works :)
Thank you ;)

---

