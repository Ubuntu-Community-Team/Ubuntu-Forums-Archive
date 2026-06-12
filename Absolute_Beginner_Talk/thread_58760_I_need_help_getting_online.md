---
title: "I need help getting online"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by Edico on 2005-08-21
I have a dual boot desktop with Windows XP and Linux Ubuntu. Yesterday, I got an internal router receiver for my computer because I heard that it works better than the USB ones. I installed the receiver, and it works fine with Windows, but I don't know how to get it to work with Ubuntu. I'm not sure what I need to do, I'm new to Linux, so any help would be appreciated. Thanks

---

### Post by amcavoy on 2005-08-21
[QUOTE=Edico]I have a dual boot desktop with Windows XP and Linux Ubuntu. Yesterday, I got an internal router receiver for my computer because I heard that it works better than the USB ones. I installed the receiver, and it works fine with Windows, but I don't know how to get it to work with Ubuntu. I'm not sure what I need to do, I'm new to Linux, so any help would be appreciated. Thanks[/QUOTE]

I had the exact same problem as you.  I was unable to get it to work with Ubuntu, so I changed my hardware configuration.  I set it up so the wirless setup was external and an ethernet cable connected it to my computer.  The internet worked immediately afterwards on Ubuntu.  I don't know if you want to go through the trouble of doing that though...

---

### Post by nad on 2005-08-21
Please post the output of the terminal commands:

lspci

lsmod

dmesg | grep eth0

ifconfig

---

### Post by Edico on 2005-08-21
[QUOTE=apmcavoy]I had the exact same problem as you.  I was unable to get it to work with Ubuntu, so I changed my hardware configuration.  I set it up so the wirless setup was external and an ethernet cable connected it to my computer.  The internet worked immediately afterwards on Ubuntu.  I don't know if you want to go through the trouble of doing that though...[/QUOTE]

That won't work, I'm too far away from the router

[QUOTE=nad]Please post the output of the terminal commands:

lspci

lsmod

dmesg | grep eth0

ifconfig[/QUOTE]

I can't :( I have no way to save it, come back on XP, and post it :(

---

### Post by nad on 2005-08-21
Floppy? Pen drive? FAT partition? Pencil and paper?

Let's start with just: lspci (we are looking for the network controller here)
and: dmesg | grep eth0 (we are looking to see what the kernel thinks it finds, if any thing)

If this is a wireless controller, you may wish to search these forums to find if your issue has already been discussed.

---

### Post by Edico on 2005-08-21
Got it, I had to borrow a flash drive.

Lspci 
```
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Family Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:05.0 Communication controller: Lucent Microelectronics V.92 56K WinModem (rev 03)
```

Dmesg | grep eth0

```
eth0: RealTek RTL8139 at 0xe400, 00:11:d8:e9:c4:f2, IRQ 21
eth0:  Identified 8139 chip type 'RTL-8101'
eth0: link down
eth0: no IPv6 routers present
```

---

### Post by nad on 2005-08-21
You may wish to research this thread:

[http://ubuntuforums.org/showthread.php?t=38972&highlight=Atheros](http://ubuntuforums.org/showthread.php?t=38972&highlight=Atheros)

Also, try to disable your onboard ethernet controller and modem in bios.

---

