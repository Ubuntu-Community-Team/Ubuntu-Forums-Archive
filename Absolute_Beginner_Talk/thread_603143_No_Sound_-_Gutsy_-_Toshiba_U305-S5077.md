---
title: "No Sound - Gutsy - Toshiba U305-S5077"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Dynamite Soul on 2007-11-04
[COLOR="Navy"]I can't figure out how to get my sound working on my Toshiba Satellite U305-S5077 laptop. Does anyone have any information which may help.

This is what I am getting so far. Any assistance with ALSA will be greatly appreciated.

Here is what I am getting:[/COLOR]
[INDENT]
[B]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0300000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, fast devsel, latency 0
        Memory at d0380000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0640000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 50000000-500fffff
        Prefetchable memory behind bridge: 0000000050100000-00000000501fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
        Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: 50200000-502fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
        Memory behind bridge: d0100000-d01fffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff50

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 2000 [size=256]
        Memory at 50000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 50100000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7128
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at 50200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

0a:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at d0100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

0a:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0a:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: medium devsel, IRQ 11
        Memory at d0100c00 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

0a:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: medium devsel, IRQ 11
        Memory at d0101000 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

0a:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: medium devsel, IRQ 11
        Memory at d0101400 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2[/B][/INDENT]

[COLOR="Navy"]Again, any help would be greatly appreciated.[/COLOR]

---

### Post by stevensn on 2007-11-06
I also have the U305 and struggled to get the sound to work.  I finally found this very easy fix and now it works perfectly:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

---

### Post by mimagabooks on 2007-11-06
Smile  Toshiba a135-s4727 or 4527
Gutsy Seems to have broken this fix for Toshiba a135-s4727. I have worked on two of this model and two of the 4527 as well as a 2234. But so far only the models ending in 27 have broken.

But after allot of searching I finally found a solution download and install the realtek High Def Driver for linux.


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

However the only way I and several others have made this work is as follows.

1. Start with a fresh install of Gutsy (k,u,x which ever you like)

2. Run the first update with your package manager do not install other software. (except a compiler if needed)

3. install the Realtek High Def Driver (or as realtek calls it "codec")

This will install the alsa drivers (1.0.14), your sound wheel will seem to work (1-100%).
Each program will control its own volume level.

Note: If you have already done the driver install steps above and it didn't work in gutsy I will say the only way this realtek driver has work for us is a fresh install.

If there is another way that makes every thing work in gutsy please let me know.

---

### Post by ntlam on 2007-12-22
I also have u305-5077. I just had to install the newest alsa driver.

---

### Post by ntlam on 2007-12-22
First
sudo apt-get install build-essential

Then
go to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

download alsa-driver-newest, alsa-lib-newest to your favourite folder (e.g. alsa-yes)
cd .. to alsa-yes
tar -xvf alsa-driver-newest.tar.bz2
cd alsa-driver-newest
sudo ./configure
sudo make
sudo make install

cd .. back to alsa-yes
tar -xvf alsa-lib-newest.tar.bz2
cd alsa-lib-newest
sudo ./configure
sudo make
sudo make install

sudo reboot

---

### Post by kc3ol on 2007-12-27
Thank you.  I have a Toshiba U305 and  you solved my problem.

Ted

---

