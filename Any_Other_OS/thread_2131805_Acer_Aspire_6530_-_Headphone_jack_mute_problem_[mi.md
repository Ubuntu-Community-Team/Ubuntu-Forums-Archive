---
title: "Acer Aspire 6530 - Headphone jack mute problem [mint 14 / ubuntu 12.10] [SOLVED]"
date: 2013-04-02
forum: Any Other OS
---

### Post by ernz on 2013-04-02
I bought a great second hand workhorse online for general linux tinkering and it's been great apart from one very irritating problem with the audio. The laptop is an Acer Aspire. Here are the install specs and hardware:

[FONT=Courier New]Release 14 (nadia) 64-bit
Kernel Linux 3.5.0-17-generic
GNOME 3.6.0
Memory: 2.7 GiB
Processor: AMD Turion(tm) X2 Dual-Core Mobile RM-72 × 2 
Graphics: Gallium 0.4 on AMD RS780 
[/FONT]

lspci out:

[FONT=Courier New]00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] AMD RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
[/FONT]

The problem is that the headphone jack does nothing at all by default. It doesn't mute the main speakers, it won't put through any sound at all. The solution I found was a combination of these audio settings:

[http://imgur.com/a/FK2Md](http://imgur.com/a/FK2Md)

...nd the use of the **black SPDIF audio jack**. Note that the green headphone jack doesn't work at all. It's the black SPDIF jack that needs to be used for your headphones, The combination of these things will allow for sound to automatically be muted and switched to headphones when plugged in and unmuted and back to built-in speakers when unplugged,

Hope this helps someone else trying to revive an excellent laptop!

---

