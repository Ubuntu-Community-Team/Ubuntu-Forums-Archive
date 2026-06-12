---
title: "Can't install Radeon HD-7670 drivers"
date: 2014-05-09
forum: Any Other OS
---

### Post by bwbritt86 on 2014-05-09
On Mint-16 I've tried all the drivers in the device manager and none of them work except for xserver though the wrapper seems to be  for the 6xxx series and not the 7xxx series, which causes the HDMI audio not to work. Well I tried to install the proprietory driver (14.4) and couldn't get it to work. The application said  that the GPU is unsupported. I've used GPU-Z on windows, I-Nex on  linux, and even googled the P/N on the card itself to make sure it's the right model. Could my motherboard's chipset  be causing unforseen problems?

MOBO Specs:
**IPIBL-LB (Benecia)**
Manufacturer: Asus
Form factor: microATX - 24.4 cm (9.6 inches) x 24.4 cm (9.6 inches)
Chipset:
    Northbridge chipset: Intel G33 Express
    Southbridge chipset: Intel ICH9R
Memory sockets: 4 x DDR2
Front side bus speeds: 1333/1066/800 MHz
Processor socket: 775
Expansion Slots:
    1 PCIe x16 slot for graphics card
    2 PCIe x1 slots
    1 PCI slot

*On a related note I'm also not able to install the Windows catalyst driver except the HDMI audio driver installs perfectly fine. I'm stuck using the one Windows downloads (ver. 8.960.11.2000) which doesn't include Catalyst Control Center.

[EDIT] I really don't know why this thing's acting so screwy. This website says that the motherboard is compatible with the GPU. (First one on the Asus list) [URL="http://www.pc-specs.com/gpu/AMD/HD_7000_Series/Radeon_HD_7670/677/Compatible_Motherboards"]
[/URL][http://www.pc-specs.com/gpu/AMD/HD_7000_Series/Radeon_HD_7670/677/Compatible_Motherboards](http://www.pc-specs.com/gpu/AMD/HD_7000_Series/Radeon_HD_7670/677/Compatible_Motherboards)

[EDIT 2] With the windows problem I disabled "auto detect & install", used the Display Driver Uninstaller, and turned off all my protection software during install but it still continues to fail.

---

### Post by bwbritt86 on 2014-05-14
OK, so as it turns out the card is an OEM card and the proprietory drivers available from the AMD website will not work. Also it's just a rebranded version of the 6670. No wonder the xserver driver was saying it was using a 6xxx series driver. Though knowing this means that the "fglrx" drivers will not work (which means no Catalyst Control), and the HDMI Audio output driver that xserver  supplies doesn't work.

Here's the big question: Does anyone know where I can find the proprietory driver for this particular GPU?
[B]GPU: HP HD7670 Firebird3 PCIex16 HF 1G GDDR5
P/N: 695592-001[/B]

---

