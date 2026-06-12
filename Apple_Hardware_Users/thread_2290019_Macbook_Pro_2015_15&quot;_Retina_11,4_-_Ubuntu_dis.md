---
title: "Macbook Pro 2015 15&quot; Retina 11,4 - Ubuntu distribution"
date: 2015-08-08
forum: Apple Hardware Users
---

### Post by arvind5 on 2015-08-08
Hi everyone,

I recently purchased Macbook Pro 15 inch retina. Model version is 11,4. Need to install a suitable ubuntu distribution for my mac.

11,4 has not been explored yet by mactel. 

lspci command was not found.

So i used a custom lspci package developed by [www.hackintoshosx.com]("http://www.hackintoshosx.com")

updated PCI IDs (update-pciids)

attached is the lspci terminal results:

[FONT=Menlo]pcilib: 0000:00:02.0 64-bit device address ignored.[/FONT]
[FONT=Menlo]00:00.0 Host bridge [0600]: Intel Corporation Crystal Well DRAM Controller [8086:0d04] (rev 08)[/FONT]
[FONT=Menlo]00:01.0 PCI bridge [0604]: Intel Corporation Crystal Well PCI Express x16 Controller [8086:0d01] (rev 08)[/FONT]
[FONT=Menlo]00:01.1 PCI bridge [0604]: Intel Corporation Crystal Well PCI Express x8 Controller [8086:0d05] (rev 08)[/FONT]
[FONT=Menlo]00:02.0 VGA compatible controller [0300]: Intel Corporation Crystal Well Integrated Graphics Controller [8086:0d26] (rev 08)[/FONT]
[FONT=Menlo]00:03.0 Audio device [0403]: Intel Corporation Crystal Well HD Audio Controller [8086:0d0c] (rev 08)[/FONT]
[FONT=Menlo]00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)[/FONT]
[FONT=Menlo]00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)[/FONT]
[FONT=Menlo]00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)[/FONT]
[FONT=Menlo]00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)[/FONT]
[FONT=Menlo]00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)[/FONT]
[FONT=Menlo]00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)[/FONT]
[FONT=Menlo]00:1f.0 ISA bridge [0601]: Intel Corporation HM87 Express LPC Controller [8086:8c4b] (rev 05)[/FONT]
[FONT=Menlo]00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)[/FONT]
[FONT=Menlo]00:1f.6 Signal processing controller [1180]: Intel Corporation 8 Series Chipset Family Thermal Management Controller [8086:8c24] (rev 05)[/FONT]
[FONT=Menlo]01:00.0 SATA controller [0106]: Samsung Electronics Co Ltd Unknown device [144d:a801] (rev 01)[/FONT]
[FONT=Menlo]03:00.0 Network controller [0280]: Broadcom Corporation BCM43602 802.11ac Wireless LAN SoC [14e4:43ba] (rev 01)[/FONT]
[FONT=Menlo]04:00.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]
[FONT=Menlo]05:00.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]
[FONT=Menlo]06:00.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]
[FONT=Menlo]06:03.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]
[FONT=Menlo]06:04.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]
[FONT=Menlo]06:05.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]
[FONT=Menlo]06:06.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]
[FONT=Menlo]07:00.0 Unassigned class [ffff]: Illegal Vendor ID Unknown device [ffff:ffff] (rev ff)[/FONT]

I am not a frequent coder so i am unaware of 'unassigned class'.

Please help me out with the distribution.

---

### Post by AWBbox on 2015-09-21
I'm having exactly the same problem as well, need to find a suitable build for an 11,4 Macbook Pro.

---

### Post by SmithParker on 2015-09-24
Yeah, it's also a problem on my macbook pro 2014

---

### Post by lstewart4 on 2016-08-20
I just purchased a MacBook pro 11,4, I was able to dual boot Ubuntu 16.04 with and it seems to work great except it does not wake from suspend. Screen is black and keyboard unresponsive. I have searched around and have not found an answer.

---

