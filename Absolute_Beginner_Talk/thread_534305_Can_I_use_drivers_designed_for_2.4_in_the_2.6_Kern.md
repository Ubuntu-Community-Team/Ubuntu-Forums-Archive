---
title: "Can I use drivers designed for 2.4 in the 2.6 Kernel?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Aishiko on 2007-08-25
I've found Drivers for a NIC but the thing is they are written for the 2.4 Kernel at the latest, can I use these in a 2.6 installation?

[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859880202&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=8020240794B06&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859880202&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=8020240794B06&displaypage=download#versiondetail)
[http://support.3com.com/infodeli/tools/nic/linuxdownload.htm](http://support.3com.com/infodeli/tools/nic/linuxdownload.htm)

anyone have expereince with either a linksys LNE100TX V5.1 or a 3Com 3C905C-TXM?

---

### Post by Paulmd on 2007-08-25
> **Aishiko said:**
> I've found Drivers for a NIC but the thing is they are written for the 2.4 Kernel at the latest, can I use these in a 2.6 installation?

[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859880202&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=8020240794B06&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859880202&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=8020240794B06&displaypage=download#versiondetail)
[http://support.3com.com/infodeli/tools/nic/linuxdownload.htm](http://support.3com.com/infodeli/tools/nic/linuxdownload.htm)

anyone have expereince with either a linksys LNE100TX V5.1 or a 3Com 3C905C-TXM?

Those are both REALLY common NICs. The drivers should be included with Ubuntu already.... At least the 3com should. It's one of the most common networking cards of its generation.

Are these cards not working?

---

### Post by Aishiko on 2007-08-25
yeah, adn neither are the SMC 1244 or 1211 and I'm using 6.06, I'd try 6.10 if I could find an iso of that to download and try

---

### Post by DarkGob on 2007-09-18
> **Paulmd said:**
> Those are both REALLY common NICs. The drivers should be included with Ubuntu already.... At least the 3com should. It's one of the most common networking cards of its generation.

Are these cards not working?
The 3c59x driver is used for 3c905c cards, and although it works reasonably well, it's not without problems (namely, dropping the connection entirely especially during high-traffic sessions, which forces you to reboot if you want to reconnect).

I was wondering the same thing about the viability of other drivers for this card because I've been putting up with this nonsense for 3 months and it's getting a little tiresome.

The 3Com driver page that the OP linked to has a link at the very bottom to a page that ostensibly has drivers for the 3c905 series, but I haven't managed to find them on said page.

---

### Post by tgalati4 on 2007-09-18
I've never had a problem with my 3c905c card.  Perhaps yours has a hardware problem.  Linux has a way of frustrating users by choking with faulty hardware.  Under Windows, you would get a freeze or a blue-screen, but never know that it was the hardware causing the problem.

As a general rule, modules compiled for the 2.4 kernel would not work with the 2.6 kernel.  However I have successfully run code compiled under the 2.6 kernel and run it on 2.4 systems by simply moving the binary and needed libraries over to the 2.4 system.

---

### Post by DarkGob on 2007-09-18
The thing of it is, my card works impeccably under Windows.  The problem started literally as soon as I switched to Linux.  The card still works fine under XP, which I dual boot with.  So unless my card is screwing with me (and I have not ruled this out), it's not a hardware thing.

---

### Post by tgalati4 on 2007-09-18
If this is an older network card in a new PC chassis, then it could be a timing issue.  Sometimes Linux will reveal problems that Windows doesn't trigger.  Memory, serial port access, hard disk writing--there are several areas where Window's slowness can mask these problems.

The other thing to do:

In the BIOS:

Turn "Plug and Play OS" to NO

Disable parallel port, disable serial port (temporarily)

It could be a shared interrupt issue.  Windows and Linux assign interrupts in different way.

Post the output of:

>more /proc/interrupts

and

>lspci -vv

and

>lsmod

---

### Post by DarkGob on 2007-09-18
Actually, the interrupt dealie sounds like precisely the error message I get in my syslog after the problem strikes, continually reported until I restart:

[27052.246085] eth0: Interrupt posted but not delivered -- IRQ blocked by another device?

The requested outputs:

more /proc/interrupts
```
           CPU0       
  0:    1053686   IO-APIC-edge      timer
  1:       1081   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:      65807   IO-APIC-edge      ide0
 15:      72430   IO-APIC-edge      ide1
 16:     241618   IO-APIC-fasteoi   fglrx
 19:     210759   IO-APIC-fasteoi   ohci1394, eth0
 20:     422130   IO-APIC-fasteoi   eth1
 21:        679   IO-APIC-fasteoi   ehci_hcd:usb3, NVidia CK8S
 22:      18773   IO-APIC-fasteoi   ohci_hcd:usb2, libata
 23:          0   IO-APIC-fasteoi   ohci_hcd:usb1, libata
NMI:          0 
LOC:    1053629 
ERR:          0

```

lspci -vv
```
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at <ignored> (32-bit, prefetchable)
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at e800 [size=32]
        Region 4: I/O ports at 4c00 [size=64]
        Region 5: I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at ec003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at ec004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin C routed to IRQ 21
        Region 0: Memory at ec005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at ec000000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at a400 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7585
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at a800 [size=256]
        Region 1: I/O ports at ac00 [size=128]
        Region 2: Memory at ec001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 23
        Region 0: I/O ports at 09e0 [size=8]
        Region 1: I/O ports at 0be0 [size=4]
        Region 2: I/O ports at 0960 [size=8]
        Region 3: I/O ports at 0b60 [size=4]
        Region 4: I/O ports at c800 [size=16]
        Region 5: I/O ports at cc00 [size=128]
        Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 22
        Region 0: I/O ports at 09f0 [size=8]
        Region 1: I/O ports at 0bf0 [size=4]
        Region 2: I/O ports at 0970 [size=8]
        Region 3: I/O ports at 0b70 [size=4]
        Region 4: I/O ports at e000 [size=16]
        Region 5: I/O ports at e400 [size=128]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: ea000000-ebffffff
        Prefetchable memory behind bridge: 50000000-500fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0002
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 255 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 8000 [size=256]
        Region 2: Memory at e9010000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e8000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0003
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: Memory at d8000000 (32-bit, prefetchable) [disabled] [size=128M]
        Region 1: Memory at e9000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

02:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 30)
        Subsystem: 3Com Corporation 3C905C-TX Fast Etherlink for PC Management NIC
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (2500ns min, 2500ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at 9000 [size=128]
        Region 1: Memory at eb001000 (32-bit, non-prefetchable) [size=128]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: Unknown device 0574:086c
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at eb000000 (32-bit, non-prefetchable) [size=2K]
        Region 1: I/O ports at 9400 [size=128]
        Capabilities: <access denied>

```

lsmod
```
Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62468  4 rfcomm,l2cap
vboxdrv              1641856  0 
fglrx                 623096  11 
ppdev                  11272  0 
cpufreq_stats           8416  0 
cpufreq_conservative     9736  0 
cpufreq_powersave       3072  0 
cpufreq_userspace       6176  0 
cpufreq_ondemand       10640  0 
freq_table              6336  2 cpufreq_stats,cpufreq_ondemand
sony_acpi               7064  0 
dev_acpi               17028  0 
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
container               6144  0 
button                 10016  0 
asus_acpi              19756  0 
ac                      6920  0 
dock                   11992  0 
video                  19080  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
battery                12040  0 
backlight               8448  1 asus_acpi
ipv6                  307456  8 
sbp2                   26628  0 
lp                     15048  0 
fuse                   51888  0 
snd_intel8x0           39080  1 
snd_ac97_codec        117848  1 snd_intel8x0
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49408  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4736  0 
snd                    68904  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
i2c_nforce2             7680  0 
serio_raw               9092  0 
psmouse                43536  0 
k8temp                  7552  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
snd_page_alloc         11792  2 snd_intel8x0,snd_pcm
i2c_core               26496  2 i2c_ec,i2c_nforce2
af_packet              27020  6 
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
ide_disk               18304  3 
generic                 6532  0 [permanent]
amd74xx                16944  0 [permanent]
usbhid                 29088  0 
hid                    34048  1 usbhid
sata_nv                24196  0 
floppy                 67944  0 
ohci1394               38088  0 
ieee1394              369784  2 sbp2,ohci1394
3c59x                  50612  0 
mii                     7424  1 3c59x
ata_generic            10628  0 
libata                137000  2 sata_nv,ata_generic
scsi_mod              166968  2 sbp2,libata
forcedeth              48776  0 
ehci_hcd               37004  0 
ohci_hcd               24196  0 
usbcore               154416  4 usbhid,ehci_hcd,ohci_hcd
thermal                16912  0 
processor              34952  1 thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```

---

### Post by tgalati4 on 2007-09-19
Is there a reason that you are not using the on-board nVidia ethernet port?

Yes, it does look like an interrupt problem.  Try my suggestions (disabling parallel and serial ports) to free up some interrupts.  This may do the trick.

---

### Post by DarkGob on 2007-09-19
I don't know why the computer is under the impression that I have an on-board ethernet port.  I have precisely one ethernet port and it belongs to my 3Com card.  And actually, eth1 (I think it was 1) just appeared out of nowhere within the past, I want to say month or two.  I didn't make any hardware changes, it just appeared.  (I should point out, I was having this problem long before it appeared.)

I'll try out your suggestion later today.

---

### Post by DarkGob on 2007-09-19
I came home 7 hours after my last post to find my internet once again unavailable.

I couldn't disable the serial port this morning because my keyboard uses it, but I did disable the parallel port.  I redid those terminal commands and they got me the same output except for /proc/interrupts:

```
           CPU0       
  0:    6308529   IO-APIC-edge      timer
  1:       3358   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  8:          0   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:      27499   IO-APIC-edge      ide0
 15:     452039   IO-APIC-edge      ide1
 16:    1512401   IO-APIC-fasteoi   fglrx
 19:     461820   IO-APIC-fasteoi   ohci1394, eth0
 20:    2536226   IO-APIC-fasteoi   eth2
 21:        695   IO-APIC-fasteoi   ehci_hcd:usb3, NVidia CK8S
 22:       9404   IO-APIC-fasteoi   ohci_hcd:usb2, libata
 23:          0   IO-APIC-fasteoi   ohci_hcd:usb1, libata
NMI:          0 
LOC:    6308840 
ERR:          0
```

eth2 seems to have popped up in eth1's place (this is still the case post-reboot).

---

### Post by tgalati4 on 2007-09-21
It could be that your motherboard HAS a built-in ethernet port, but there's no jack for it.  It's possible that an update to the kernel has detected this on-board port and is trying to use it.  This would explain the network weirdness.

To control the two ethernet ports use the following:

>sudo ifconfig eth2 up             (to turn the chip on)
>sudo ifconfig eth2 down         (to turn the chip off)

Check the BIOS, there is usually an option to turn off the on-board ethernet.  It appears to be interferring with your 3Com card.

---

### Post by DarkGob on 2007-09-21
I've had this computer for over 2 years, actually built the thing myself, and somehow I didn't notice/remember that I do, in fact, have a jack for that on-board ethernet port (it's covered in the back by a thin metal plate, so I guess that's why I never noticed).  Good to know.

But, that didn't do the trick.  Also, and here's the part where you groan, I completely neglected to mention [this is a known bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629") (again with the forgetting).  It has seemingly been fixed in kernel 2.6.23, and since [Gutsy will be based on 2.6.22]("http://ubuntuforums.org/showpost.php?p=3128163&postcount=4"), I guess I'm screwed until April or whenever Hardy Haron ends up being released.

Thanks anyway though.

---

### Post by Aishiko on 2007-09-26
you can just compile the .23 kernel and use it instead.

or since ethernet cards are so cheap just buy a different one from a site like newegg for 10-15$ and be done with it assuming of course that this bug doesn't effect all Ethernet PCI cards (I assume PCI as ISA would be really rare to see these days.)

Also lets not forget a USB to Ethernet Dongle again a cheap and quick solution if they are supported in Linux.

There are always options you just have to look for them.

---

