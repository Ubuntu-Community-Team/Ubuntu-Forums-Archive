---
title: "HELP! Intel Wireless 3945 not working"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by wak_wak on 2007-06-30
1st:  I'm a newbie.  Second:  I've been trying to figure this out for 2 days straight.

I've got a Dell Inspiron E1705 with an ATI graphics card and an Intel 3945 wireless card.

I'm running Kubuntu Feisty Faun.

I'm trying to figure this out but no luck.

I went to the Intel site and tried some instructions there but it didn't get me anywhere and it was very confusing.

If there's a step by step set of instruction that are simple please advise!!!!

---

### Post by oilchangeguy on 2007-06-30
using the search box at the upper right of the page, i typed in intel 3945. and it came back with 72 threads, one of them is bound to contain your answer.

---

### Post by MrGill on 2007-06-30
First of all you'll have to help us out by posting the outputs of some commands through terminal. do the following and paste the results in

sudo iwconfig
sudo  lspci 
--> find your network card in the list, look at the number to the left, do:
sudo lspci -n
--> and use the number to the right of it in that list:
sudo lspci -vvd [here]

eg. 

spikey@spikey-desktop:/$ sudo lspci -n
00:00.0 0600: 1039:0741 (rev 03)
00:01.0 0604: 1039:0003
left numbers first, use the right numbers next

and find your network card in:
sudo lshw -short

paste them all in a reply and someone more useful will help you :)

---

### Post by wak_wak on 2007-07-01
OK>  So here's the info.  I hope it's useful!  Thanks in advance for all of the help...



[COLOR="Blue"]**root@wak-laptop:~# sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.
[/COLOR]

[COLOR="Blue"][COLOR="Red"]
root@wak-laptop:~# sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)[/COLOR][/COLOR]

[COLOR="Green"]

**root@wak-laptop:~# sudo lspci -n**
00:00.0 0600: 8086:27a0 (rev 03)
00:01.0 0604: 8086:27a1 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.1 0604: 8086:27d2 (rev 01)
00:1c.3 0604: 8086:27d6 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:2448 (rev e1)
00:1f.0 0601: 8086:27b9 (rev 01)
00:1f.2 0101: 8086:27c4 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
01:00.0 0300: 1002:7145
03:00.0 0200: 14e4:170c (rev 02)
03:01.0 0c00: 1180:0832
03:01.1 0805: 1180:0822 (rev 19)
03:01.2 0880: 1180:0843 (rev 01)
03:01.3 0880: 1180:0592 (rev 0a)
03:01.4 0880: 1180:0852 (rev 05)
0c:00.0 0280: 8086:4222 (rev 02)

[/COLOR]


[COLOR="Red"]
**root@wak-laptop:~# sudo lspci -vvd 8086:4222**
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1020
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <128ns, L1 <64us
                Link: ASPM L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
[/COLOR]


[COLOR="Green"]
**root@wak-laptop:~# sudo lshw -short**
H/W path           Device      Class          Description
=========================================================
                               system         MP061
/0                             bus            0YD479
/0/0                           memory         64KB BIOS
/0/400                         processor      Genuine Intel(R) CPU           T225
/0/400/700                     memory         8KB L1 cache
/0/400/701                     memory         2MB L2 cache
/0/400/0.1                     processor      Logical CPU
/0/400/0.2                     processor      Logical CPU
/0/1000                        memory         1GB System Memory
/0/1000/0                      memory         512MB DIMM DDR Synchronous 533 MHz
/0/1000/1                      memory         512MB DIMM DDR Synchronous 533 MHz
/0/100                         bridge         Mobile 945GM/PM/GMS/940GML and 945G
/0/100/1                       bridge         Mobile 945GM/PM/GMS/940GML and 945G
/0/100/1/0                     display        Radeon Mobility X1400
/0/100/1b                      multimedia     82801G (ICH7 Family) High Definitio
/0/100/1c                      bridge         82801G (ICH7 Family) PCI Express Po
/0/100/1c.1                    bridge         82801G (ICH7 Family) PCI Express Po
/0/100/1c.1/0                  network        PRO/Wireless 3945ABG Network Connec
/0/100/1c.3                    bridge         82801G (ICH7 Family) PCI Express Po
/0/100/1d                      bus            82801G (ICH7 Family) USB UHCI #1
/0/100/1d/1        usb1        bus            UHCI Host Controller
/0/100/1d.1                    bus            82801G (ICH7 Family) USB UHCI #2
/0/100/1d.1/1      usb2        bus            UHCI Host Controller
/0/100/1d.2                    bus            82801G (ICH7 Family) USB UHCI #3
/0/100/1d.2/1      usb3        bus            UHCI Host Controller
/0/100/1d.3                    bus            82801G (ICH7 Family) USB UHCI #4
/0/100/1d.3/1      usb4        bus            UHCI Host Controller
/0/100/1d.7                    bus            82801G (ICH7 Family) USB2 EHCI Cont
/0/100/1d.7/1      usb5        bus            EHCI Host Controller
/0/100/1d.7/1/1                bus            USB hub
/0/100/1d.7/1/1/4              communication  BCM2045
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1e/0        eth0        network        BCM4401-B0 100Base-TX
/0/100/1e/1                    bus            Ricoh Co Ltd
/0/100/1e/1.1                  system         R5C822 SD/SDIO/MMC/MS/MSPro Host Ad
/0/100/1e/1.2                  system         Ricoh Co Ltd
/0/100/1e/1.3                  system         R5C592 Memory Stick Bus Host Adapte
/0/100/1e/1.4                  system         xD-Picture Card Controller
/0/100/1f                      bridge         82801GBM (ICH7-M) LPC Interface Bri
/0/100/1f.2        scsi0       storage        82801GBM/GHM (ICH7 Family) Serial A
/0/100/1f.2/0      /dev/sda    disk           111GB WDC WD1200BEVS-7
/0/100/1f.2/0/1    /dev/sda1   disk           Dell Utility partition
/0/100/1f.2/0/2    /dev/sda2   disk           HPFS/NTFS partition
/0/100/1f.2/0/3    /dev/sda3   disk           Linux swap / Solaris partition
/0/100/1f.2/0/4    /dev/sda4   disk           Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD+-RW TS-L632D
/0/100/1f.2/1/0    /dev/cdrom  disk
/0/100/1f.3                    bus            82801G (ICH7 Family) SMBus Controll
/1                             power          DELL C544667
[/COLOR]

---

### Post by wak_wak on 2007-07-03
OK.  So I'm not sure how but I got it working and I'm kicking myself for not paying closer attention to what I did so as to be able to share it but it works and QUITE well and I must say a bit more stably than say Windows.

---

### Post by Papi-KB7VGW on 2007-07-03
Hi,  I'm surprised that you had trouble getting it to run.  I have almost the identical system and it worked flawlessly out of the box.  I am a happy  Ubuntuer now.  I left windows on a 10g partition but I haven't booted into it for months now.  Good Luck     :popcorn:

---

