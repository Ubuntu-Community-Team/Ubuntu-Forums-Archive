---
title: "Problem with my onboard sound card!"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by efond on 2007-04-08
Hello everybody

i am a new member of ubuntu community , installed it 4 houre ago. I have a problem with detecting my onboard sound card  >>**Realtek ALC888 7.1 channel CODEC with High Definition Audio** . My motherbopard is "ASRock  ALIVE NF6G-DVI" . I have no idea how to fix the problem , Can you help me please??? i love This OS , i want to conntinue using it , but this problem make me very sad.

Best regards!!!

---

### Post by mendingo84 on 2007-04-08
exactly what happens? no output or what?

---

### Post by efond on 2007-04-08
well , i have a red mark on my Volume control ikon . When i go to System->Preferences->Sound  there is no Sound card detected. i have ubuntu and windows installed on my hard drive , with windows everything is OK  (i have sound)

When i start Applocations->Sound and video -> Movie player  i receve a message "Could not establish connection to sound server"

My Ubuntu 6.06

---

### Post by efond on 2007-04-08
anyone can`t help????????

---

### Post by FoundmyTux on 2007-04-08
Check out Comprehensive Sound Problem Solutions Guide at:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by overdrank on 2007-04-08
> **FoundmyTux said:**
> Check out Comprehensive Sound Problem Solutions Guide at:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Great tip, Thanks will use that in the future. :popcorn:

---

### Post by efond on 2007-04-08
> efond@efondpc:~$ lspci -v
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 03ea (rev a1)
        Subsystem: ASRock Incorporation: Unknown device 03ea
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 03e0 (rev a2)
        Subsystem: ASRock Incorporation: Unknown device 03e0
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 03eb (rev a2)
        Subsystem: ASRock Incorporation: Unknown device 03eb
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at dc00 [size=64]
        I/O ports at 5000 [size=64]
        I/O ports at 6000 [size=64]
        Capabilities: <available only to root>

0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 03f5 (rev a2)
        Subsystem: ASRock Incorporation: Unknown device 03eb
        Flags: 66MHz, fast devsel

0000:00:01.3 Co-processor: nVidia Corporation: Unknown device 03f4 (rev a2)
        Subsystem: ASRock Incorporation: Unknown device 03f4
        Flags: 66MHz, fast devsel
        Memory at 20100000 (32-bit, non-prefetchable) [disabled] [size=512K]

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 03f1 (rev a2) (p rog-if 10 [OHCI])
        Subsystem: ASRock Incorporation: Unknown device 03f1
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 03f2 (rev a2) (p rog-if 20 [EHCI])
        Subsystem: ASRock Incorporation: Unknown device 03f2
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at dfcfec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 03f3 (rev a1) (prog- if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dfd00000-dfffffff
        Prefetchable memory behind bridge: 20000000-200fffff
        Capabilities: <available only to root>

0000:00:05.0 0403: nVidia Corporation: Unknown device 03f0 (rev a2)
        Subsystem: ASRock Incorporation: Unknown device 0888
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at dfcf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 03ec (rev a2) (pr og-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation: Unknown device 03ec
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at ffa0 [size=16]
        Capabilities: <available only to root>

0000:00:07.0 Bridge: nVidia Corporation: Unknown device 03ef (rev a2)
        Subsystem: ASRock Incorporation: Unknown device 03ef
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at dfcfd000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d480 [size=8]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2) (pr og-if 85 [Master SecO PriO])
        Subsystem: ASRock Incorporation: Unknown device 03f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        I/O ports at d400 [size=8]
        I/O ports at d080 [size=4]
        I/O ports at d000 [size=8]
        I/O ports at cc00 [size=4]
        I/O ports at c880 [size=16]
        Memory at dfcfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.1 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2) (pr og-if 85 [Master SecO PriO])
        Subsystem: ASRock Incorporation: Unknown device 03f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at c800 [size=8]
        I/O ports at c480 [size=4]
        I/O ports at c400 [size=8]
        I/O ports at c080 [size=4]
        I/O ports at c000 [size=16]
        Memory at dfcf7000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 03e8 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <available only to root>

0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <available only to root>

0000:00:0d.0 VGA compatible controller: nVidia Corporation: Unknown device 03d0 (rev a2) (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation: Unknown device 03d0
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dd000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at dfcc0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
        Flags: fast devsel

0000:01:08.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100]  (rev 08)
        Subsystem: IBM 10/100 EtherJet Adapter with Alert on LAN
        Flags: bus master, medium devsel, latency 32, IRQ 50
        Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=64]
        Memory at dfe00000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at 20000000 [disabled] [size=1M]
        Capabilities: <available only to root>


Sorry for my stupidity , but i don`t see my realtek sound card . I am ablosute beginner . When i go to  [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) i see only Nvidia one driver :( . Please help me

---

### Post by maryjanua on 2007-09-19
did u ever get this fixed i have that sound card and i got it solved  check out this thread
[http://ubuntuforums.org/showthread.php?t=550753](http://ubuntuforums.org/showthread.php?t=550753)
around page 11 may help you
regards mj

---

