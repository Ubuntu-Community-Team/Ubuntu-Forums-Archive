---
title: "Dell SD slot not working?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-05
i installed ubuntu a few weeks back and LOVE it.  i've only booted into windows once since i changed to a dual-boot machine.  the only big problem i've had is that the SD card slot on my dell XPS m140 laptop doesn't work.  when i re-installed windows tho, i had to download a driver for it to work.  is there one for ubuntu?

---

### Post by teaker1s on 2007-04-05
we could try and find out hardware and then if we can make it work guessing it's usb connected- post output
```
lsusb
```

---

### Post by locke.dragon on 2007-04-06
it's not usb connected though.  it's built into the body of my laptop.  when i use your code in the terminal all it gives me is this...

```

Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

any other ideas?

---

### Post by seshomaru samma on 2007-04-06
```
lspci
```

---

### Post by locke.dragon on 2007-04-06
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

---

### Post by seshomaru samma on 2007-04-07
what kernel are you using?

(put 
```
uname -r
```
in a terminal to know)

it seems this device ,Ricoh R5C592 ,is only working with the 2.6.20-12 kernel
see [here]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84540")

---

### Post by locke.dragon on 2007-04-09
2.6.17-11-generic

that's what i'm using.

---

### Post by locke.dragon on 2007-04-14
hmmmm.  that's strange.  it started working today.  good for me, bad for people trying to learn from this thread.  oh well.  sorry about that guys.

---

### Post by jjalocha on 2007-04-14
There's a method for getting the same reader working on another Dell Notebook in [this thread]("http://ubuntuforums.org/showthread.php?t=367898"). This might help others with the same problem.

---

### Post by Mike Ozornin on 2007-04-30
The same problem but on samsung laptop .
Ricoh card reader.

2.6.20-15-generic kernel. 7.04 ubuntu.

lpci
09:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
09:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04)


modprobe -l | grep mmc
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/sdricoh_cs.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/host/sdhci.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/host/tifm_sd.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/host/wbsd.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/core/mmc_core.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/card/mmc_block.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/scsi/ibmmca.ko

modprobe -l | grep tifm
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/host/tifm_sd.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/misc/tifm_core.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/misc/tifm_7xx1.ko


dmesg show nothing after inseting MMC card into reader.

---

