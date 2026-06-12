---
title: "No audio running gutsy"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Kormiku on 2008-02-17
I have audio in my vista partition but not on my gutsy partition. Here is what shows up when i type lspci -v

please help

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
        Subsystem: Lenovo Unknown device 383c
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3846
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3847
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 3849
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f8304000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Unknown device 384e
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: bc000000-bfffffff
        Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f0000000-f3ffffff
        Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000fc000000-00000000fdffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b4000000-b7ffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3843
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3844
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3845
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 3848
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f8304400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
        Memory behind bridge: f8000000-f80fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Lenovo Unknown device 3840
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Lenovo Unknown device 3841
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18e0 [size=16]
        I/O ports at 18d0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Lenovo Unknown device 3842
        Flags: medium devsel, IRQ 10
        Memory at 50000000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 3862
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1002
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
        Subsystem: Lenovo Unknown device 3861
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at b4000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Lenovo Unknown device 3829
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8000000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Lenovo Unknown device 382a
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at f8000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Lenovo Unknown device 382b
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f8000c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Lenovo Unknown device 382c
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f8001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Lenovo Unknown device 382d
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f8001400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by Presto123 on 2008-02-17
I have a suggestion for you: try shutting down completely and then going back into Ubuntu. This may sound stupid, but...just try it.

---

### Post by Kormiku on 2008-02-17
> **Presto123 said:**
> I have a suggestion for you: try shutting down completely and then going back into Ubuntu. This may sound stupid, but...just try it.

ive restarted quite a few times, and still no sound.

---

### Post by astrodad on 2008-02-17
try go to System->Preferences or Administration and look for Sound
once you are there, look for something like with 'Default' word...and change the value to other then Headphone..it should work coz i got the same problem before with my laptop...

---

### Post by chips24 on 2008-02-17
> **Kormiku said:**
> ive restarted quite a few times, and still no sound.

ive tried the same.

---

### Post by spiderbatdad on 2008-02-17
Run ```
alsamixer
``` make sure PCM is up.

If that doesn't do it try this: ```
asoundconf set-default-card I8280H1ICH8
```  or the result of

```
asoundconf list
``` then reboot

---

### Post by Kormiku on 2008-02-17
> **spiderbatdad said:**
> Run ```
alsamixer
``` make sure PCM is up.

If that doesn't do it try this: ```
asoundconf set-default-card I8280H1ICH8
```  or the result of

```
asoundconf list
``` then reboot

I ran alsamixer and pcm was up. it didnt fix it.

i typed that code in: asoundconf ... and it didnt fix it even after reboot.

This is what i get when i type in asoundconf list:

Names of available sound cards:
Intel

---

### Post by lemmy999 on 2008-02-17
Try System>Preferences>Sound ,and try "Sound playback" -test. Do you hear anything?

---

### Post by Kormiku on 2008-02-17
> **lemmy999 said:**
> Try System>Preferences>Sound ,and try "Sound playback" -test. Do you hear anything?

I dont hear anything when i try sound playback test

---

### Post by spiderbatdad on 2008-02-17
I use a Lenovo. Fortunately (for me) I do not have this problem. There is a bug in the alsa driver affecting some Lenovo systems. The only fix may be to recompile alsa with a patch...I haven't been able to find...or removing the existing alsa sound base and installing the latest release candidate.

[https://bugs.launchpad.net/alsa-driver/+bug/107821](https://bugs.launchpad.net/alsa-driver/+bug/107821)

[http://www.alsa-project.org/main/index.php/ChangeLogs](http://www.alsa-project.org/main/index.php/ChangeLogs)

---

### Post by Kormiku on 2008-02-20
> **spiderbatdad said:**
> I use a Lenovo. Fortunately (for me) I do not have this problem. There is a bug in the alsa driver affecting some Lenovo systems. The only fix may be to recompile alsa with a patch...I haven't been able to find...or removing the existing alsa sound base and installing the latest release candidate.

[https://bugs.launchpad.net/alsa-driver/+bug/107821](https://bugs.launchpad.net/alsa-driver/+bug/107821)

[http://www.alsa-project.org/main/index.php/ChangeLogs](http://www.alsa-project.org/main/index.php/ChangeLogs)

This looks like the only fix. However, my computer doesnt have a CD drive, and i cant get past the point int he directions where they say to put your ubuntu CD into your cddrive.

I used USB to install ubuntu. What should I do? Is there a way to recompile the program to read ubuntu off my usb as if it were a CD? Or perhaps i can mount the ubuntu iso file and make it look like a cd? How would this be done? Thank you

---

### Post by spiderbatdad on 2008-02-20
Try to disable the request for cd in softwares sources. System>>Administration>>Software Sources.
Also run ```
sudo apt-get update
```Hopefully your sources are not commented out as the result on an installation without a working internet connection. Make sure the other sources, labeled "downloadable from the internet" are checked. Source code in unnecessary. The run sudo apt-get update.

---

### Post by spiderbatdad on 2008-02-20
Are you following this guide? [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

