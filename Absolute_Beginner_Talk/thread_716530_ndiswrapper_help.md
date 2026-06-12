---
title: "ndiswrapper help"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Pieterdt on 2008-03-06
where do i find the program on the computer?
How do  I convert netwok card files?

---

### Post by anewguy on 2008-03-06
Just to be sure you understand:  ndiswrapper is a tool used to allow usage of some windows drivers for wireless network cards in Linux.

Ndiswrapper and it's utilities should be loaded using synaptic package manager, but this also assumes you have access to a wired connection.  Without a wired connection, you can still do it but it is a little more involved (there are threads on this forum about that).

As far as converting files, I assume you mean using the windows driver files in Linux.  This is what ndiswrapper does for you.

If you think you need ndiswrapper and need to use it, post back your wireless card maker and model, or post the output of "lspci" run in a terminal.  From there we can try to determine if there are drivers available and if we can make then work.

:)

---

### Post by Pieterdt on 2008-03-06
make  = smc : smcwpcit-g
lspci= 00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:09.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:0a.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
00:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:05.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (rev 02)

---

### Post by uberlube on 2008-03-06
If you would like a very good guide on how to use ndiswrapper check this thread out:

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper)

---

