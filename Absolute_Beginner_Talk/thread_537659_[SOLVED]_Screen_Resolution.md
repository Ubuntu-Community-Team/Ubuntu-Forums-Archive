---
title: "[SOLVED] Screen Resolution"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by sw1995 on 2007-08-29
Hi Gang,

I finally got Ubuntu loaded on my friends old computer; normally, I'd RTFM, however he will be around in a few hours and will be less than impressed if he sees the resolution I have the screen at. It is hurting my eyes as we speak. SO, I am curious, this is a an OLD pc, here is the output of "lspci":

00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 82)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 02)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)

The screen resolution is just nasty and I am wondering if there is anything I can do to fix it. System: Preferences: Resolution gives me 1024 X 728...this computer is FLYING compared to what it was two hours ago with windows so I'd love to have the screen thing fixed for him when he shows up...his mind will be blown. I'd hate to lose the deal because of this messy screen.

Any thoughts?

-S

---

### Post by forestpixie on 2007-08-29
have you enabled the restricted driver for the graphics and using the nvidia driver.

what sort of  resolution are you expecting

system > admin >restricted driver manager

---

### Post by cawill on 2007-08-29
In terminal :sudo dpkg-reconfigure -phigh xserver-xorg,
then select the driver, which looks like a nvidia one,
then select the resolutions that the monitor supports.
Press ALT + CTRL + Backspace to restart the x server to get you new resolutions.

---

### Post by sw1995 on 2007-08-29
> **forestpixie said:**
> have you enabled the restricted driver for the graphics and using the nvidia driver.

what sort of  resolution are you expecting

system > admin >restricted driver manager

Enabling the restricted drivers did it. Wow. Thank you...Hurrah!

-S

---

### Post by forestpixie on 2007-08-29
good - glad it helped - can you mark thread solved please (first post- thread tools)

---

