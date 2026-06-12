---
title: "Can someone help me get my sound working?"
date: 2012-12-08
forum: Any Other OS
---

### Post by Newuser86 on 2012-12-08
Hello everyone, I installed Linux Mint 14.1 a few days ago and I have not been able to get my sound to work. I searched other posts and tried the terminal command "alsamixer" to see if anything was muted, and I don't believe the output is muted (although alsamixer is not familiar to me).

I will post the output of my "lspci -v" command below

```

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Lenovo Device 21fa
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 21fa
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 21fa
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at f2520000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 21fa
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f2535000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei
    Kernel modules: mei

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
    Subsystem: Lenovo Device 21f3
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f2500000 (32-bit, non-prefetchable) [size=128K]
    Memory at f253b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 5080 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 21fa
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f253a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 21fa
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f2530000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f1d00000-f24fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f0bfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 21fa
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f1c00000-f1cfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 21fa
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f1400000-f1bfffff
    Prefetchable memory behind bridge: 00000000f0c00000-00000000f13fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 21fa
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 21fa
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2539000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
    Subsystem: Lenovo Device 21fa
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 21fa
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 50a8 [size=8]
    I/O ports at 50b4 [size=4]
    I/O ports at 50a0 [size=8]
    I/O ports at 50b0 [size=4]
    I/O ports at 5060 [size=32]
    Memory at f2538000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 21fa
    Flags: medium devsel, IRQ 7
    Memory at f2534000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07) (prog-if 01)
    Subsystem: Lenovo Device 21fa
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f1d00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [800] Advanced Error Reporting
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f1c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 24-77-03-ff-ff-d2-6c-f8
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
```Any help would be appreciated.

---

### Post by Newuser86 on 2012-12-09
If anyone has been reading this... I have an update on what may be causing the problem, although I don't know how to fix it.

When I am running firefox with a terminal open, any time I go to a site like youtube or any site that has potential audio output, the terminal gives the error:

"Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory"

I've google'd the error and none of the fixes say anything about this error coming up in the terminal.

If anyone has a suggested fix for this problem, let me know. Thanks.

---

### Post by desktorp on 2012-12-09
Does that system even have an NVIDIA chip?  Also, is it only the browser or can you get sound out of other programs?  Have you tested any media players, like VLC?

If you can get sound everywhere but Firefox, try disabling the browser's hardware acceleration by clicking:

[COLOR=DarkRed]Edit [COLOR=Black]>[/COLOR] Preferences [COLOR=Black]>[/COLOR] Advanced [COLOR=DarkOrange](tab)[/COLOR] [COLOR=Black]>[/COLOR] [COLOR=Green]*uncheck*[/COLOR] Use Hardware Acceleration..[/COLOR]

---

### Post by Newuser86 on 2012-12-10
I can't get sound anywhere, not just in firefox. I've tried to test the speakers with the sound application, but nothing happens. I don't believe the OS is noticing that I have a built-in card from Lenovo and not a built-in Intel card. Is there another driver I can download and use or can I just tell the OS to use a different card with a few terminal commands?

---

### Post by smellyman on 2012-12-10
did you press f6 in alsamisxer to teh coreect card and make sure the channels are unmuted?

---

### Post by pqwoerituytrueiwoq on 2012-12-10
> **Newuser86 said:**
> "Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory"
vdpau is for nvidia GPUs, you are using a Intel GPU, you shuold purge nvidia-current or what ever nvidia driver you have installed
you should be able to set the default sink in sound settings, if you have multiple HDMIs in the configure tab in the drop down, you will need to try each till one works

---

### Post by mythic97 on 2012-12-11
Ah no sound in mint I have experience with this I fixed it with a start-up script which I can't recall or find for that matter but it starts sound running as soon as you login also check the settings as well it could be using wrong speakers ect... sorry I can't be of more help

---

