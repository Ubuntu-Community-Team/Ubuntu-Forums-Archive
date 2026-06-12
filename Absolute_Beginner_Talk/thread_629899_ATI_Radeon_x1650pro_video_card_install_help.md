---
title: "ATI Radeon x1650pro video card install help"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by malibusurfer2 on 2007-12-02
I need help installing the driver for a ATI Radeon x1650pro video card. I have the card installed but the display screen resolution is set at 800x600 with no other options. lspci shows:

corer@corer:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c3 (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Unknown device 71e3 (rev 9e)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by xshagy on 2007-12-02
i've got the same card.  but can't get anything to display. when you say you installed it, what do you mean by that?

---

### Post by Shakkaa on 2007-12-02
probably the best way to go about it is to download the new 7.11 video drivers from the ATI web site.  Once you download them use the "sudo sh ./"DRIVER"" where DRIVER is what you downloaded from the ATI site.  They're not perfect yet, but it'll get you running.

by the way, more than likely you will be running this on your desktop through a terminal.  If you need more specifics just let us know =)

---

### Post by malibusurfer2 on 2008-01-02
What I meant was that I physically installed the PCIe video card into my computer box. I was unable to get it to work, so took it out, but now can't log into root - get a blank white screen, but it is obvious that Ubuntu is running - just can't see anything displayed on the desktop. Help! How can I change root video driver back to default motherboard video (Intel 945 i810)?

---

