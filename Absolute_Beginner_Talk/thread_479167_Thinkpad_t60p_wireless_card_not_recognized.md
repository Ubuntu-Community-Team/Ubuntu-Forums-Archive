---
title: "Thinkpad t60p wireless card not recognized"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Andross707 on 2007-06-20
In the network settings for my feisty 7.04 install, there is a ethernet connection shown but no wireless even though the wireless card is recognized and works automatically in Vista. I'm not really even sure where to begin with this as most guides I've seen ask what type of chipset and whatnot one has and I'm not sure where I can find this information, etc. Any help?

---

### Post by wormser on 2007-06-20
Post the results from the following command to let us know what type of card you have.

```
lspci
```

---

### Post by Andross707 on 2007-06-21
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71d4
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller




PS. what does lspci do?

---

### Post by ugm6hr on 2007-06-21
Hopefully this will help:
[http://ubuntuforums.org/showthread.php?t=419628](http://ubuntuforums.org/showthread.php?t=419628)

It links to a couple of solutions.

Thinkpads are apparently well-supported in Linux.

PS: *lspci* merely lists PCI devices (that's my understanding in simple terms) - it allows you to identify what hardware you have installed.

---

### Post by Andross707 on 2007-06-21
just came back to post that I followed the first link, scrolled down and selected "ThinkPad 11a/b/g/n Wireless LAN Mini Express Adapter",  downloaded cabextract (as described in the guide), followed [http://ubuntuforums.org/showthread.php?t=479009](http://ubuntuforums.org/showthread.php?t=479009) to figure out how to use cabextract, then using ndiswrapper installed from add/remove programs option in the top panel (with search for all available applications selected) used its GUI to select the extracted .inf file and am happily but exhaustedly typing this now wirelessly in Ubuntu.

---

