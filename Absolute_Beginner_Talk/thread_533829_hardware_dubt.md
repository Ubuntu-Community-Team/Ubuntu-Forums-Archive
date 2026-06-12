---
title: "hardware dubt"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Nerdyn on 2007-08-24
Hello everyone... i Got a stupid question that I am sure everyone knows the answer for....

What command is used to see if your System recognises all the hardware in the machine you are using?

I know lspci.....
This is the output of the command on my Laptop
[INDENT]
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
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
01:00.0 VGA compatible controller: ATI Technologies Inc M24 [Radeon Mobility X600]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
[/INDENT]

But i don't get How i recon if everything is working properly....

Thanks in advance

Sorry spelling mistake....!

---

### Post by Steve1961 on 2007-08-24
You could have a look at the output of the command dmesg, or even take a look in System>Hardware Information.  However, you seem to have fairly standard hardware, so you shouldn't have too many problems.

---

### Post by Nerdyn on 2007-08-24
Thank you Steve...

dmesg gives me quite enough to read for tonight + it says that i got bluetooth (and i didn't know i had one...!!!!)  going to investigate

Thank you again for your help

---

### Post by w4ett on 2007-08-24
you can also:

```
lshw
```

---

### Post by Nerdyn on 2007-08-24
Thank you W4Ett 
I think everything is working properly... a part the stand by....

Thanks

---

