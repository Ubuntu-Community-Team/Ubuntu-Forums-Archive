---
title: "[SOLVED] Radeon 3850 not recognized"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by DingsBumps on 2008-01-15
Hi there,
one of the main reasons I got in to ubuntu was compizfusion, however, I recently built a new system with a radeon 3850, and I cannot get the fglrx driver to work

[Phoronix]("http://www.phoronix.com/scan.php?page=article&item=944&num=1") got this card to work, so it is possible. The major obstacle for me is that the card is not seen ubuntu as a radeon 3850 and therefore if I click on the restricted manager, a message saying none of my hardware requires restricted drivers pops up.

lspci returns:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9505
01:00.1 Audio device: ATI Technologies Inc Unknown device aa18
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

How can I get my card to be recognized!
Thanks!

---

### Post by DingsBumps on 2008-01-15
Forgot to add:
fglrxinfo returns
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

---

### Post by DingsBumps on 2008-01-15
well, I read somewhere that my card would not work under x64, so I will install the 32bit ubuntu and see how that goes.:(

EDIT: Works beautifully under 32bit

---

### Post by punkrockguy318 on 2008-02-17
I have the 3850.  It works perfectly in 64 bit 7.10, but not many people can get it to work in 8.04 yet.  ATIs driver installer only supports up to gutsy

---

### Post by DingsBumps on 2008-02-22
Today, I decided I would try 64bit again, and it works beautifully. I used the new Catalyst Control Center (which didn't support my card at the time of original post but does now).

So yes, the Radeon 3850 works in x64.

---

### Post by dvlchd3 on 2008-04-18
Where did you download the Catalyst Control Center?  I go to ATI's website, and the 3850 is not listed on either the linux-64 bit, or linux-32 bit downloads.??:confused:

---

