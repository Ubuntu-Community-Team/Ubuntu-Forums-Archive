---
title: "Sound issue makes no sense"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by djtecha on 2007-07-23
So after I installed Wine and started playing warcraft3 my sound would keep going out. And if I wanted sound I would have to run asoundconf set-default-card UART reinstall Alsa and reboot, and everything would work fine. Until the other day when this fix no longer worked. So I searched these forums and ran tons of help fixes from purging and reinstalling to compiling my own driver with little success. Now why I am so confused is that the sound not only works on Windows XP fine, but originally worked right out of the box on ubuntu Feisty. So after several reinstalls my audio is still not working and I keep recieving the error "No volume control GStreamer plugins and/or devices found." Someone PLEASE help 

djtecha@djtecha-desktop:~$ aplay -l**** List of PLAYBACK Hardware Devices ****
djtecha@djtecha-desktop:~$ 



djtecha@djtecha-desktop:~$ lspci -v00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 255
        I/O ports at e400 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at d3104000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d800 [size=16]
        Memory at d3102000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c400 [size=16]
        Memory at d3101000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
        Memory behind bridge: d3000000-d30fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at d3100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b000 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0000000-d2ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1) (prog-if 00 [VGA])
        Subsystem: Unknown device 19f1:201f
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d1000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at a000 [size=128]
        [virtual] Expansion ROM at d2000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at d3004000 (32-bit, non-prefetchable) [size=2K]
        Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


I have an Asus a8n-sli motherboard

---

### Post by anewguy on 2007-07-23
This may not be the case, but for the heck of it check to see if any of the gstreamer stuff shows as installed if you go into synaptic package manager.  If not, try installing them and see what happens.  If not, you might want to check the WINE forums.:)

---

### Post by djtecha on 2007-07-23
yea but why would it no longer work on reinstall like it had before? that's why I almost feel like there is some very odd problem here.

---

### Post by ReaderRat on 2007-07-23
Sorry, wrong answer.

---

### Post by djtecha on 2007-07-23
my only reasonable explanation for any of this is that some configuration files somehow are lasting through the format, either on the other partition or some extremely odd fluke. So I am booting and nuking it and hopefully this will begin to work in the morning. But i'm curious if anyone has any other ideas for why this might not work.

---

### Post by djtecha on 2007-07-24
well completely clearing the data did little good. This makes absolutely no sense?

---

### Post by djtecha on 2007-07-25
SO this is my new theory, and if anyone with electrical knowledge please let me know if this makes any sense. So the audio works on a cold boot, which made me wonder that it was a hardware problem so upon opening up my computer I found that the north bridge fan was no longer working which might explain why the audio would shut off. Now my thinking as to why it would work in windows is that windows utilizes the audio in a less stressful way to allow the audio to stay somewhat more cool. I suppose when I get my new fan I can tell if this is the problem or not.

---

### Post by Shazaam on 2007-07-25
What you could do to confirm your theory is to put a table fan next to your pc and direct the flow towards the offending chip.

---

