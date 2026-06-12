---
title: "Toshiba m200 laptop inbuilt webcam and bluetooth"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by mefl on 2007-11-11
I've loaded Ubuntu onto my new laptop. Can't figure out how to get the in built blue tooth and in built webcam to work. Please can someone help/advise.

---

### Post by DutyDuty on 2007-11-11
Just dove in? That's fine, I did too.
Could we know a little more about the webcam or Bluetooth? I've seen apps for Bluetooth, never used it. Can you "see" either? Do you know the names of the devices? Where are they(not physically)? 
How about a```
lspci
``` in terminal? Post results and more info, please.

---

### Post by mefl on 2007-11-12
sorry for taking so long, been of line.
here's the info. what r u looking 4???

tos@tos-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
tos@tos-laptop:~$

---

### Post by DutyDuty on 2007-11-12
Ok. Nothing useful there, for now. Hmm...could I know a little more about the bluetooth? Webcam too. What are their names and locations?

---

### Post by mefl on 2007-11-12
all i can tell u is that i just bought this laptop - Satellite Toshiba M200. it came with Vista but i kicked it off as i don't like windows now. the LT has builtin bluetooth and wireless and webcam. the wirless works OK via the network setup but the bluetooth and webcam don't work. i can't find any way to turn them on, what ort of bluetooth and webcam it is, don't know as it is built in. that's about all i know at this point - sorry.

---

