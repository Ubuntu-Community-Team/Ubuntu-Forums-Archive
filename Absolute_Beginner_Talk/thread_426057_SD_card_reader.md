---
title: "SD card reader"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by holyowned on 2007-04-28
I have a Toshiba laptop with a flash card reader built in.  How does Ubuntu handle this?  I am running Dapper.  I presumed it would see it as another drive, ala XP.  It doesn't show in my Disks that I have found.
TIA

---

### Post by finer recliner on 2007-04-28
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

^ follow these instructions. except you're not looking for a windows partition, you're looking for your SDcard.

---

### Post by Iarwain ben-adar on 2007-04-28
You might want to think to upgrade (at least to kernel version 2.6.10-17 or higher)

That's when my SD was properly recognised ;)


Iarwain

---

### Post by holyowned on 2007-04-29
Ok, I put my card in, ran sudo fdisk -l in a terminal, and it only picked up my HDD partitions.  I'll upgrade my kernel.  Thanks for the help.  :)

---

### Post by holyowned on 2007-04-29
> **Iarwain ben-adar said:**
> You might want to think to upgrade (at least to kernel version 2.6.10-17 or higher)

That's when my SD was properly recognised ;)


Iarwain

My kernel is 2.6.15-28 :(

---

### Post by Iarwain ben-adar on 2007-04-30
Well,
i got mine working by upgrading the kernel to a higer version.

What about this thread? [http://ubuntuforums.org/showthread.php?t=402316&highlight=ricoh+sd](http://ubuntuforums.org/showthread.php?t=402316&highlight=ricoh+sd)


Iarwain

---

### Post by holyowned on 2007-04-30
Thanks, larwain, I will check that out.  I discovered last night that I am running 6.06 LTS.  Truly amazing the things you discover when you really start digging in strange places.  Downloading the 6.10 full update as we speak.

---

### Post by holyowned on 2007-05-02
I downloaded 6.10.  It said there was an error with some of the files, but it installed.  SD card still not recognized.  And when I boot into 6.10, my laptop mousepad doesn't work.  Here is my lspci:
I see that the device is there, but I can't access the pics on it.

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

---

