---
title: "Sound Card."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-07-06
Okay, I can't even find a driver for my sound card, let alone I don't even know what sound card it is. I have no sound what so ever, can anyone help? Yes I tried the troubleshoot and all that yadda yada.

---

### Post by overdrank on 2007-07-06
> **phizikal said:**
> Okay, I can't even find a driver for my sound card, let alone I don't even know what sound card it is. I have no sound what so ever, can anyone help? Yes I tried the troubleshoot and all that yadda yada.

Hi can you post the output of the command 
```
lspci
```
And we will see what your sound card is.

---

### Post by phizikal on 2007-07-06
```

root@admin:/home/admin# lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)0000:00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:00:0f.0 Communication controller: Agere Systems LT WinModem
0000:00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

```

---

### Post by overdrank on 2007-07-06
Hi well I have done some searching and that chipset uses the AC97 audion but it is not being seen so wait till feisty comes in the mail and see if that helps!

---

