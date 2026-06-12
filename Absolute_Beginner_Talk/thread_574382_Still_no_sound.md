---
title: "Still no sound"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-10-12
Somewhere on my upgrade path my pc went mute. lspci displays the following:
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0d.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0f.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 43)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]

I have tried installing and building alsa manually but to no avail. In addition when I click on the volume control it displays an error message "No volume control  gstreamer and / or devices found",

Thanks for reading.

---

### Post by linuxforrealpeople on 2007-10-13
And now i have discovered that if I regress to the previous Kernel version sound is restored and Alsamixer works.

---

