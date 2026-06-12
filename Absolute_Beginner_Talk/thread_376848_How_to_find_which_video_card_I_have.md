---
title: "How to find which video card I have?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jayramj on 2007-03-05
Hello,

I have installed Ubuntu(Edgy) on one of my old PCs. Now none of the 3D apps/Games work on it. As first step I wanted to find out which Graphics/Video card this machine has. How can I find this information?

Thanks
Jayram

---

### Post by jayramj on 2007-03-05
Also when I try to run some application(e.g. bzflag) I get folowing error

libGL warning: 3D driver claims to not support visual 0x46
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x48
  Serial number of failed request:  141
  Current serial number in output stream:  143

---

### Post by newlinux on 2007-03-05
One way that might work is to look in the device manager

```
hal-device-manager
```

or

```
lspci

```
Look around for something that looks like a video card name might help. (e.g. GeForce, ATI, 6200, 7600, etc.) For instance mine says GeForce 6150 on one of my computers, which is exactly what I have.

---

### Post by lamalex on 2007-03-05
do an lspci and look around in the output. if you dont know post it here and ill take a look. or pop open your computer and look :)

---

### Post by jayramj on 2007-03-05
Aah great I think its VIA Technologies, Inc. VT8378 [S3 UniChrome]

[I]00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)[/I]

---

### Post by j.miller565 on 2007-03-05
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

yup it is :) By the way, I've never heard of VIA before though.

---

### Post by lamalex on 2007-03-05
that would be it :)

---

### Post by jayramj on 2007-03-05
Thanks guys :)

Now next question would be why dont 3D apps work on this machine? Any pointers from where I can start?

---

